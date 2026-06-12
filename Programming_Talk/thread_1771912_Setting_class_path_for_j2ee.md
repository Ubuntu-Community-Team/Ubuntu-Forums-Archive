---
title: "Setting class path for j2ee"
date: 2011-05-30
forum: Programming Talk
---

### Post by RobikShrestha on 2011-05-30
I installed j2ee by downloading .bin file from java site
Now how do I set its class path variables?
I have netbeans which does not compile j2ee programs. After setting class path variables is there anything else I have to do to make netbeans recognize the j2ee classes?

---

### Post by slavik on 2011-05-31
what now?

do you know how j2ee works? what do you use as a container?

---

### Post by RobikShrestha on 2011-05-31
No I am just a beginner.
Please tell me how to setup the class path.
Please tell me if netbeans will then support j2ee.
I do not know what a container is.

---

### Post by ratcheer on 2011-05-31
Here is what I have in my .bashrc:

JAVA_HOME=/usr/java/jre1.6.0_24
PATH=$JAVA_HOME/bin:$PATH
CLASSPATH=$JAVA_HOME/lib

Tim

---

### Post by t1497f35 on 2011-05-31
If you download the ["Java EE"]("http://netbeans.org/downloads/index.html") version of NetBeans - it already ships with all enterprise related stuff and no need to customize/set the classpath to do EE development, unless you're already deploying your app or are working with neither glassfish nor tomcat or some other specific case.

---

### Post by RobikShrestha on 2011-05-31
Ok I used netbeans.
I used one of the sample web applications.
When I run it, it says:
/home/robik/NetBeansProjects/whatTheHell/build.xml:9: warning: 'includeantruntime' was not set, defaulting to build.sysclasspath=last; set to false for repeatable builds
Compiling 1 source file to /home/robik/NetBeansProjects/whatTheHell/build/web
compile:
compile-jsps:
Stopping Tomcat process...
Waiting for Tomcat...
Tomcat server stopped.
Starting Tomcat process...
Waiting for Tomcat...
Tomcat server started.
In-place deployment at /home/robik/NetBeansProjects/whatTheHell/build/web
deploy?config=file%3A%2Ftmp%2Fcontext252228081563511850.xml&path=/
[http://localhost:8080/manager/deploy?config=file%3A%2Ftmp%2Fcontext252228081563511850.xml&path=/](http://localhost:8080/manager/deploy?config=file%3A%2Ftmp%2Fcontext252228081563511850.xml&path=/)
/home/robik/NetBeansProjects/whatTheHell/nbproject/build-impl.xml:686: The module has not been deployed.
BUILD FAILED (total time: 43 seconds).


How to solve it and what does the error even mean?

---

### Post by RobikShrestha on 2011-05-31
I also have another question:

Our group is quite new to java. But our minor project is supposed to be really good. We are not taught java at college. Now we want to develop an online shopping application, like ebay.com (but much simpler of course). Is the netbeans->web applications the correct way to go? Is tomcat server similar to sql server? Can we create an actual network between two computers to create a real server-client environment with such an application?

---

### Post by t1497f35 on 2011-05-31
You seem to have a problem with "Ant", a quick google yields this
[http://www.coderanch.com/t/503097/tools/warning-includeantruntime-was-not-set](http://www.coderanch.com/t/503097/tools/warning-includeantruntime-was-not-set)

A quick solution might be to change in build.xml the line
[COLOR=#009900][COLOR=#000000]**<javac**[/COLOR] [COLOR=#000066]srcdir[/COLOR]=[COLOR=#ff0000]"${src.dir}"[/COLOR] [COLOR=#000066]destdir[/COLOR]=[COLOR=#ff0000]"${classes.dir}"[/COLOR][COLOR=#000000][B]/>
to
[/B][/COLOR][/COLOR][COLOR=#009900][COLOR=#000000]**<javac**[/COLOR] [COLOR=#000066]srcdir[/COLOR]=[COLOR=#ff0000]"${src.dir}"[/COLOR] [COLOR=#000066]destdir[/COLOR]=[COLOR=#ff0000]"${classes.dir}"[/COLOR] [COLOR=#000066]includeantruntime[/COLOR]=[COLOR=#ff0000]"false"[/COLOR][COLOR=#000000][B]/>

[/B]If you still have issues you might post your project so people can replicate your issue.

As to your shopping app question, both Java "Web Application" and
"Java EE" are ok for creating such a website, the former is simpler to get up and running
cause it doesn't require you to know about EJB and stuff alike.

A typical scenario would be using JSP/Servlets/MySQL.
If you also like to use JSF or Spring - is up to you.


[/COLOR][/COLOR]

---

### Post by RobikShrestha on 2011-05-31
It still does not run:

init:
deps-module-jar:
deps-ear-jar:
deps-jar:
library-inclusion-in-archive:
library-inclusion-in-manifest:
Compiling 1 source file to /home/robik/NetBeansProjects/whatTheHell/build/web
compile:
compile-jsps:
Starting Tomcat process...
Waiting for Tomcat...
Tomcat server started.
In-place deployment at /home/robik/NetBeansProjects/whatTheHell/build/web
Deployment is in progress...
deploy?config=file%3A%2Ftmp%2Fcontext1769566867100144084.xml&path=/
[http://localhost:8080/manager/deploy?config=file%3A%2Ftmp%2Fcontext1769566867100144084.xml&path=/](http://localhost:8080/manager/deploy?config=file%3A%2Ftmp%2Fcontext1769566867100144084.xml&path=/)
/home/robik/NetBeansProjects/whatTheHell/nbproject/build-impl.xml:686: The module has not been deployed.
BUILD FAILED (total time: 42 seconds)

---

### Post by t1497f35 on 2011-05-31
search on google

---

### Post by RobikShrestha on 2011-05-31
I have done that already but to no use

---

### Post by r-senior on 2011-05-31
Do you know if Tomcat is from the Ubuntu repositories or do you have it unpacked somewhere under your home folder?

The server page for Tomcat inside Netbeans should tell you. If the path starts with /home, it's in your home folder. If it starts /usr/local, it's the repository version.

EDIT: Have a look at this:

[http://ubuntuforums.org/showthread.php?t=1447417](http://ubuntuforums.org/showthread.php?t=1447417)

---

### Post by RobikShrestha on 2011-05-31
Well I could not solve the problem so I switched to Glassfish server.
I have another question:

For our project, we intend to create a webpage on customer side and application (JFrame) for admin side and shop side (i.e. department stores are able to update their database via a software(JFrame) but customers buy things from a website). Is the netbeans-> web application the way to do it. Please provide some hints on the JFrame part for the department stores.

---

### Post by r-senior on 2011-06-01
If you are running Glassfish I'd recommend running Oracle/Sun Java rather than OpenJDK. I've had problems with the Admin console on Glassfish using OpenJDK but YMMV.

> 
For our project, we intend to create a webpage on customer side and application (JFrame) for admin side and shop side (i.e. department stores are able to update their database via a software(JFrame) but customers buy things from a website). Is the netbeans-> web application the way to do it. Please provide some hints on the JFrame part for the department stores. 
Netbeans can help you write the web application and the GUI builder tool in Netbeans (Matisse) is well regarded. So yes, you can develop the whole application using Netbeans.

Hints:

1. Both parts of the application share a common "model". That suggests to me having a separate model project with a clearly defined API, i.e. an interface exposing all its methods. Test driven development using JUnit is very valuable on such projects. The model project should be layered: business API (aka service layer, aka session facade) interacting with persistence API (DAOs).

2. Both the web application and Swing application should have no business or persistence logic. That should all be in the model project. When you come to add a smartphone app, you just write a web service using the same model and interact with the web service over the wire from the device.

3. This project sounds sufficiently large that a couple of hours spent working through the Maven tutorial would pay dividends later.

4. If I was writing it, I'd probably use Spring. Make a model project configured using Spring, Spring managed transactions. Persistence layer up to you but sitting behind a well-defined API (interfaces) so that you can change it if necessary. If the database structure involves complex object graphs, e.g. Order -> Order Line -> Product, I'd sit Hibernate behind it. Unless the project was expected to scale up to a distributed architecture, in which case I'd make the whole model project EJB3.

5. What you are doing has been done before. Off the shelf eCommerce solutions (from eBay shop right up to something like WebSphere Commerce, depending on scale) can often work out cheaper than reinventing.

---

### Post by RobikShrestha on 2011-06-01
Thank You for replying but quite frankly most of the things went over the head. I do not even know JSP let alone maven and spring. Seems a lot of study needs to be done. So what I was planning to do was: create web application and swing application sharing same database. Swing application is used by shopkeepers to update their prices and quantities. Web application is used by customer to order and search for items. I am really an amateur. Is this a good idea?

---

### Post by slavik on 2011-06-01
You should not be developing an e-commerce web site in a language you have no knowledge about. Stick to a language you know or get an intro book on Java and learn the basics first. J2EE is a not a beginner level topic.

---

### Post by RobikShrestha on 2011-06-01
Well, I can develop desktop applications in java. I have no idea about j2ee. I am starting out with JSP and am making quite a progress because of past experience in php. I know sql. What else should I learn?

---

### Post by r-senior on 2011-06-01
> **RobikShrestha said:**
> What else should I learn?
My suggestions would be:

1. Maven - as a Java developer you'll never look back. Honestly.

You can do this now (Maven is in the Ubuntu repositories):

[http://maven.apache.org/guides/getting-started/maven-in-five-minutes.html](http://maven.apache.org/guides/getting-started/maven-in-five-minutes.html)

This will take a couple of hours (treat Ch3-Ch6 as your priority):

[http://www.sonatype.com/books/mvnex-book/reference/public-book.html](http://www.sonatype.com/books/mvnex-book/reference/public-book.html)

Once you have a web application that depends on 20-30 jar files, Maven will be your best friend.

2. MVC - as applied to web applications (use servlets/JSP to learn the process, then learn a framework such as Struts2, JSF or Spring MVC)

[http://www.oracle.com/technetwork/articles/javase/servlets-jsp-140445.html](http://www.oracle.com/technetwork/articles/javase/servlets-jsp-140445.html)

3. Learn how to make a clean, self contained (M)odel for MVC that you can re-use in your Swing application, your web application and a web service.

[http://www.bigbeeconsultants.co.uk/blog/interfaces-for-decoupling/](http://www.bigbeeconsultants.co.uk/blog/interfaces-for-decoupling/)

Nothing difficult there. Just new. You could just start coding scriptlets in JSP and not bother with this stuff, but you'll get into a mess as the applications get bigger. I've done that.

---

