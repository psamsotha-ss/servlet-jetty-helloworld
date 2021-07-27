# Hello World Servlet with jetty-maven-plugin

## Run

```shell
$ git clone https://github.com/psamsotha-ss/servlet-jetty-helloworld.git
$ cd servlet-jetty-helloworld
$ ./mvnw clean package jetty:run
```

If you are using Windows, use the `mvnw.bat` file. `mvnw` is a wrapper for Maven, similar to the Gradle wrapper. It allows people to run Maven without actually installing Maven locally. The command `mvnw` is just like running `mvn`. The `mvnw(.bat)` script is included in the project. If you have Maven installed locally, you can use `mvn` instead.

## Access servlet

```shell
$ curl localhost:8000/hello
<h1>Hello Servlets!</h1>
```

## Servlet

```java
@WebServlet(name = "HelloWorldServlet", urlPatterns = "/hello")
public class HelloWorldServlet extends HttpServlet {

    @Override
    public void doGet(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        PrintWriter writer = response.getWriter();
        writer.write("<h1>Hello Servlets!</h1>");
    }
}

```

## `jetty-maven-plugin`

The project uses [`jetty-maven-plugin`](https://www.eclipse.org/jetty/documentation/jetty-11/programming-guide/index.html#jetty-maven-plugin) to run an embedded Jetty Servlet container. Your servlet will be deployed to this container. The Maven goal the run the plugin is `jetty:run`.
