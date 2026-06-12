---
title: "Help running my first servlet with tomcat ???"
date: 2013-04-01
forum: Programming Talk
---

### Post by vikkyhacks on 2013-04-01
I just now downloaded tomcat. I learned java the last week and now am planing for servlets. I have a php background. To run my servlet I

1. Created my WEB-INF at 
          ```
 <DIR>/apache-tomcat-7.0.32/webapps/ROOT/WEB-INF
```

2. Put my simple web.xml inside WEB-INF with only
          ```
 <webapp>
           </webapp>
```

3. Then wrote my HttpServlet.java and tried to compile it.

```
// Import required java libraries
import java.io.*;
import javax.servlet.*;
import javax.servlet.http.*;


// Extend HttpServlet class
public class HelloWorld extends HttpServlet {
 
  private String message;


  public void init() throws ServletException
  {
      // Do required initialization
      message = "Hello World";
  }


  public void doGet(HttpServletRequest request,
                    HttpServletResponse response)
            throws ServletException, IOException
  {
      // Set response content type
      response.setContentType("text/html");


      // Actual logic goes here.
      PrintWriter out = response.getWriter();
      out.println("<h1>" + message + "</h1>");
  }
  
  public void destroy()
  {
      // do nothing.
  }
}

```


I am getting error message as 

```
meow@vikkyhacks ~/Arena/apache-tomcat-7.0.32/webapps/ROOT $ javac HelloWorld.java 
HelloWorld.java:3: error: package javax.servlet does not exist
import javax.servlet.*;
^
HelloWorld.java:4: error: package javax.servlet.http does not exist
import javax.servlet.http.*;
^
HelloWorld.java:7: error: cannot find symbol
public class HelloWorld extends HttpServlet {
                                ^
  symbol: class HttpServlet
HelloWorld.java:11: error: cannot find symbol
  public void init() throws ServletException
                            ^
  symbol:   class ServletException
  location: class HelloWorld
HelloWorld.java:17: error: cannot find symbol
  public void doGet(HttpServletRequest request,
                    ^
  symbol:   class HttpServletRequest
  location: class HelloWorld
HelloWorld.java:18: error: cannot find symbol
                    HttpServletResponse response)
                    ^
  symbol:   class HttpServletResponse
  location: class HelloWorld
HelloWorld.java:19: error: cannot find symbol
            throws ServletException, IOException
                   ^
  symbol:   class ServletException
  location: class HelloWorld
7 errors



```

[B][SIZE=4]MY SERVER WORKS FINE COS I PUT AN index.html AS ~/webapps/ROOT/index.html AND AM ABLE TO SEE IT AT localhost:8080.

[SIZE=5]1. WHY AM I NOT ABLE TO COMPILE MY CODE ?
2. WHAT TO DO NEXT 
[SIZE=3]
[SIZE=4]I am using [/SIZE][/SIZE][/SIZE][/SIZE][/B][SIZE=4][http://www.tutorialspoint.com/servlets](http://www.tutorialspoint.com/servlets) to learn servlets. It will be great if some one can point some useful resources. I feel java environment very much different from php and python[/SIZE]

---

### Post by Elfy on 2013-04-01
Thread closed. Please do not post duplicates, it dilutes community effort.

---

