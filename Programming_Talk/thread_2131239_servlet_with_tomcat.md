---
title: "servlet with tomcat"
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
  symbol:   class ServletException[/SIZE]
  location: class HelloWorld
7 errors



```
MY SERVER WORKS FINE COS I PUT AN index.html AS ~/webapps/ROOT/index.html AND AM ABLE TO SEE IT AT localhost:8080.

1. WHY AM I NOT ABLE TO COMPILE MY CODE ?
2. WHAT TO DO NEXT 
I am using[http://www.tutorialspoint.com/servlets](http://www.tutorialspoint.com/servlets) to learn servlets. It will be great if some one can point some useful resources. I feel java environment very much different from php and python

---

### Post by r-senior on 2013-04-01
You need servlet-api.jar in your classpath when you compile. So something like:

```
javac -c servlet-api.jar HelloWorld.java
```

EDIT: The tutorial sets up a CLASSPATH variable to achieve the same result. See page 4.

---

### Post by vikkyhacks on 2013-04-02
Thanks :) , ok that was simple, I got that compiled ... but it seems like I have to keep restarting the server for every small change, that is very much irritating, is there any other way around this. I have not tried other servers. I don like keep restarting my server for each and every simple small change.

---

### Post by r-senior on 2013-04-02
You can just reload the application through the Tomcat Admin page. You should see a link to it if you go to [http://localhost:8080](http://localhost:8080). If it's not letting you log in, you need to set up the [FONT=Courier New]tomcat-users.xml[/FONT] file, which you'll find in the [FONT=Courier New]conf[/FONT] directory. Apache changed the format of this slightly with Tomcat 7.x but this should work if you are using a recent version:

```
<?xml version='1.0' encoding='utf-8'?>
<!--
  Licensed to the Apache Software Foundation (ASF) under one or more
  contributor license agreements.  See the NOTICE file distributed with
  this work for additional information regarding copyright ownership.
  The ASF licenses this file to You under the Apache License, Version 2.0
  (the "License"); you may not use this file except in compliance with
  the License.  You may obtain a copy of the License at

      http://www.apache.org/licenses/LICENSE-2.0

  Unless required by applicable law or agreed to in writing, software
  distributed under the License is distributed on an "AS IS" BASIS,
  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
  See the License for the specific language governing permissions and
  limitations under the License.
-->
<tomcat-users>
<!--
  NOTE:  By default, no user is included in the "manager-gui" role required
  to operate the "/manager/html" web application.  If you wish to use this app,
  you must define such a user - the username and password are arbitrary.
-->
<!--
  NOTE:  The sample user and role entries below are wrapped in a comment
  and thus are ignored when reading this file. Do not forget to remove
  <!.. ..> that surrounds them.
-->
  <role rolename="tomcat"/>
  <role rolename="manager-gui"/>
  <user username="tomcat" password="tomcat" roles="tomcat,manager-gui"/>
</tomcat-users>
```

You'd log into the admin manager with username "tomcat", password "tomcat". You'll see the deployed application listed and there's a reload button.

EDIT: Note that you do need to restart Tomcat after updating this XML file.

A second option is: [https://tomcat.apache.org/tomcat-7.0-doc/manager-howto.html#Reload_An_Existing_Application](https://tomcat.apache.org/tomcat-7.0-doc/manager-howto.html#Reload_An_Existing_Application)

A third option is to set the reloadable attribute on the context. This reloads the application when it detects the .class file has been updated: [https://tomcat.apache.org/tomcat-7.0-doc/config/context.html](https://tomcat.apache.org/tomcat-7.0-doc/config/context.html)

It looks something like this:

```
<Context docBase="..." ... reloadable="true"/>
```

A fourth option is to write a little script, a Makefile perhaps, that compiles your servlet, jars it up and copies the war file to the web apps directory. Tomcat will explode it, deploy it and reload it.

A fifth option is to use Eclipse or Netbeans and set up the server under control of the IDE, which will reload the application as part of the build.

A sixth option is not to use Tomcat at all, instead using Maven with the Jetty plugin.

A seventh option would be too much for a single post. ;)

I tend to use the first option, i.e. the manager, in combination with Tomcat set up under control of Eclipse.

---

### Post by vikkyhacks on 2013-04-02
Thanks a lot, that solved it. It helped me a lot ....
:) :) :) :) :) :)

---

### Post by rmuniprashanthi on 2013-10-30
hai to all...
I am new to servlets and I am not knowing why my web application is not running on ubuntu 12.04 using tomcat 7
I have created a small servlet to request parameters "username and password" and servlet programs receives this parameters and displays the same parameters on the browser.
My problem is I am able to see the html page..but result is not displayed on the page..
please help me regarding this issue...please ..please

---

### Post by rmuniprashanthi on 2013-10-30
please tell complete procedure to configure any variables required for it..

---

### Post by r-senior on 2013-10-30
Please post your servlet code. In code tags. Also your web.xml file.

---

### Post by arnavkumartechno on 2013-11-01
Re: servlet with tomcat

May be you forgot to define CATALINA_HOME, JAVA_HOME and classpath in your system.
If this is not the case then reply here i will give you full description here.

---

