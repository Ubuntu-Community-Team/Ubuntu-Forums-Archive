---
title: "trouble deploying HelloWorld servlet first time"
date: 2014-02-20
forum: Programming Talk
---

### Post by IAMTubby on 2014-02-20
Hello,
 I'm having a problem deploying my servlet. It's building fine, but I'm not able to access it over the browser. These are the steps I followed

1.My code for HelloWorld.java is as follows
```
// Import required java libraries
import java.io.*;
import javax.servlet.*;
import javax.servlet.http.*;

// Extend HttpServlet class
public class HelloWorld extends HttpServlet
{
        private String message;
        public void init()throws ServletException
        {
                // Do required initialization
                message ="Hello World";
        }


        public void doGet(HttpServletRequest request,HttpServletResponse response) throws ServletException,IOException
        {
                // Set response content type
                response.setContentType("text/html");
                // Actual logic goes here.
                PrintWriter out= response.getWriter();
                out.println("<h1>"+ message +"</h1>");
        }


        public void destroy()
        {
                // do nothing.
        }
}

```

2.My exports are :
$ echo **$CATALINA_HOME**
**/home/IAMTubby/Desktop/installfiles/apache-tomcat-7.0.50**
$ echo **$CLASSPATH**
**/home/IAMTubby/Desktop/installfiles/apache-tomcat-7.0.50/lib/servlet-api.jar**


3.I have placed the output of javac HelloWorld.java which is HelloWorld.class in **/home/IAMTubby/Desktop/installfiles/apache-tomcat-7.0.50/webapps/examples/WEB-INF/classes/HelloWorld.class and have also added the following in /home/IAMTubby/Desktop/installfiles/apache-tomcat-7.0.50/webapps/examples/WEB-INF/web.xml**
```
<servlet>
<servlet-name>HelloWorld</servlet-name>
<servlet-class>HelloWorld</servlet-class>
</servlet>
<servlet-mapping>
<servlet-name>HelloWorld</servlet-name>
<url-pattern>/HelloWorld</url-pattern>
</servlet-mapping>

```

4.I have ensured that localhost:8080 is running tomcat; when I access this url, I get the tomcat page

**But when I access [http://localhost:8080/HelloWorld](http://localhost:8080/HelloWorld) , I get HTTP Status 404 - /HelloWorld saying that "The requested resource is not available."**

Where am I going wrong ? Is the location where I'm placing the .class file wrong?
Please advise.
Thanks.

EDIT : I also made my own directory structure inside webapps, as /home/IAMTubby/Desktop/installfiles/apache-tomcat-7.0.50/webapps/hello/WEB-INF/classes and placed my HelloWorld.class here and web.xml under the WEB-INF directory, but that doesn't seem to work as well.

---

### Post by IAMTubby on 2014-02-21
I tried a bit more.
I have access to the html page at [http://localhost:8080/examples/servlets/index.html](http://localhost:8080/examples/servlets/index.html); when I click the "Execute" link for the HelloWorld example on it, it takes me to a page at [http://localhost:8080/examples/servlets/servlet/HelloWorldExample](http://localhost:8080/examples/servlets/servlet/HelloWorldExample) . Even in the code for index.html, it says, ```
<td VALIGN=TOP WIDTH="30%"><a href="servlet/HelloWorldExample"><img SRC="images/execute.gif" HSPACE=4 BORDER=0  align=TOP></a><a href="servlet/HelloWorldExample">Execute</a></td>
```.

1. I thought that maybe placing my .class servlet files in this directory would work. But I can't seem to find a directory like examples/servlets/servlet under apache.

2.So I searched for all files which have anything to do with HelloWorld as follows, and placed my corresponding .java and .class files in both those locations. And then tried to access from browser  as [http://localhost:8080/examples/servlets/servlet/MyAlteredHelloWorldExample]("http://localhost:8080/examples/servlets/servlet/HelloWorldExample"). But still it says "_The requested resource is not available._"
```
$ find ./ -name 'HelloWorldExample*' 2>/dev/null/home/IAMTubby/Desktop/installfiles/apache-tomcat-7.0.50/webapps/examples/WEB-INF/classes/HelloWorldExample.class
/home/IAMTubby/Desktop/installfiles/apache-tomcat-7.0.50/webapps/examples/WEB-INF/classes/HelloWorldExample.java

```

Please advise.

---

