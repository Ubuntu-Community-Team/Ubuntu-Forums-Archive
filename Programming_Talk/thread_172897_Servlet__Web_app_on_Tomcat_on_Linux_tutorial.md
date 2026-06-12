---
title: "Servlet / Web app on Tomcat on Linux tutorial"
date: 2006-05-09
forum: Programming Talk
---

### Post by JeffS on 2006-05-09
I'm sure this has been done before, but why not one more? In my initial forays into writing, compiling, deploying, running servlets on Tomcat running on Linux, I encountered extreme frustration. Frankly, the documentation/tutorials out there, including the ones at the Tomcat website, the ones at the Sun website, and others, are lacking. They tell you how to write a servlet. They tell you to create a WAR. They tell you to deploy the WAR to the CATALINA_HOME directory, etc etc.

However, the tutorials often severely lack a lot of the necessary details, and I would always run into stumbling blocks. So I would Google this, Google that, paruse message boards, and fight with it until I would finally come up with a solution.

Sure, I was always able to easily do servlets with Tomcat using NetBeans, or some other great tool. But I always ran into problems trying to do it all manually in the commnand line (a worthwhile endevour, to understand how everything works and is put together properly, rather than relying on the IDE crutch).

With all this, you will have to install Tomcat from the debian repos, as well as Java itself.  Using apt-get to install Tomcat should give everything you need, but you might also want to instal the regular Sun Java SDK, or install Eclipse (to bring it's dependencies), or install the free Java SDK from the Deb repos (which includes the Jikes compiler, the SableVM virtual machine, and GNU classpath).  In any case, having a full Java install, and Tomcat, might be the subject of another tutorial.  But this tutorial is centered on getting a web app / servlet compiled, deployed and running on Tomcat on Kanotix.  So it assumes you already installed Java and Tomcat.

So, here is how it all works (at least for me, with a Debian install and Tomcat5, and Java 1.5 (as well as gcj):

1. Create Web Application directory:
NameOfProjectDirectory
NameOfProjectDirectory/WEB-INF
NameOfProjectDirectory/WEB-INF/classes (optional sub directories like sample here)
NameOfProjectDirectory/WEB-INF/lib (optional, if needed)

2. In NameOfProjectDirectory/WEB-INF/classes (/subdir) Compile:
javac -cp /usr/share/tomcat5/common/lib/servlet-api.jar NameOfServlet.java

the -cp argument is, of course, providing the classpath to the servlet jar file. Without providing this, the servlet won't compile. You could, of course, set the CLASSPATH environment variable as well.

3. In NameOfProjectDirectory (root) Make WAR file:
jar -cvf NameOfWarFile.war .
(don't forget the ".", with a space between it and the war - it's important)

4. Stop Tomcat (if already running)
su
/etc/init.d/tomcat5 stop

Here, you log on as root, ("su"), and it will prompt you for root's password. Root access is necessary to stop/start Tomcat, and is necessary to copy the WAR into the webapps directory of Tomcat.

5. copy WAR file to webapps directory of Tomcat:
su
cp NameOfWarFile.war /usr/share/tomcat5/webapps

Here, cp is the the Linux copy command, not to be confused with the -cp argument to javac.

6. Start Tomcat:
su
/etc/init.d/tomcat5 start

7. In browser:
[http://localhost:8180/NameOfWAR/NameOfServlet](http://localhost:8180/NameOfWAR/NameOfServlet) (or how it's named in URL pattern tag of web.xml)

In my Tomcat install on my Debian/Kanotix install, Tomcat is configured to port 8180. With most Tomcat installs, it defaults to 8080.  I'm not sure what is is for the Ubuntu install (I did all this on my Kanotix box, not my Ubuntu box), but I assume it's the same.

Servlet sample code (HelloServlet.java):

package test;

import java.io.*;

import javax.servlet.http.*;
import javax.servlet.*;

public class HelloServlet extends HttpServlet {
public void doGet (HttpServletRequest req,
HttpServletResponse res)
throws ServletException, IOException
{
PrintWriter out = res.getWriter();

out.println("<h1>Hello, world!</h1><br>");
out.println("<h1>Jeff loves Servlets!</h1>");
out.close();
}
}

web.xml Sample code:

<web-app xmlns="http://java.sun.com/xml/ns/j2ee" version="2.4"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http:/java.sun.com/dtd/web-app_2_3.dtd">
<servlet>
<servlet-name>hello</servlet-name>
<!-- in this example, the servelt is in a subdir/package called test -->
<servlet-class>test.HelloServlet</servlet-class>
</servlet>

<servlet-mapping>
<servlet-name>hello</servlet-name>
<!-- accessed in browser, or HTML/JSP link, via "/NameOfWar/hello" -->
<url-pattern>/hello</url-pattern>
</servlet-mapping>
</web-app>

If one wants to add JSPs or html forms (that call the servlet), it's a matter of having them in the root of your project directory (above WEB-INF). If there are additional classes that the servlet(s) depends on or accesses, put them in NameOfProjectDirectory/WEB-INF/lib

Also, there is an easier way of deploying the servlet (leaving the command line a bit). It's in the Tomcat Manager page (accessed, of course, in your browser). First, you have to add a user account in the tomcat-users.xml file (the xml there is pretty self explanatory, you just have to make it an administrator). Then you have to bring up the Tomcat homepage in your browser - [http://localhost:8180/](http://localhost:8180/) - then you click on the Tomcat Manager Link on the left, and you'll be prompted to enter your user id and password. After than, in the Manager page, scroll down to the deploy war file option, and click on the browse button to browse to where you created the WAR. Then click on "Deploy". Then it's ready to go. No loggin on as root in the command line, not stopping Tomcat, no copying the WAR to the webapps of Tomcat directory, not restarting Tomcat.

Then, to be even easier, one can create an Ant script that does everything automatically. But that's the subject of another tutorial. ;-)

Finally, it's brain-dead easy to create web apps in NetBeans. But it's very very very worthwhile to do it all in the command line, in order to learn how everything works and is put together.

I hope this helps for any Tomcat/Servlet newbies out there!

---

### Post by LordHunter317 on 2006-05-09
You don't, in a default install of Tomcat5, need to stop or stop the server for it to notice a deployed WAR.

You don't even need to in a non-default install, you just have to command it manually to stop and start the webapplication.

Also, in developer mode (The default), you can deploy an already exploded WAR tree to webapps and use that.  It's perfectly legal and allows you to change .JSPs on the fly without having to remove and redeploy the WAR.  They are automatically recompiled on every change. 

However, certain things like changes to configuration files will not be caught unless you change web.xml, which will cause a complete redeploy.  I have had issues with this in the past, and tend to manually redeploy (or kickstart the server) when making such changes.  But depending on the development you're doing, this may be eaiser than doing other things.

---

### Post by JeffS on 2006-05-10
[QUOTE=LordHunter317]You don't, in a default install of Tomcat5, need to stop or stop the server for it to notice a deployed WAR.

You don't even need to in a non-default install, you just have to command it manually to stop and start the webapplication.

Also, in developer mode (The default), you can deploy an already exploded WAR tree to webapps and use that.  It's perfectly legal and allows you to change .JSPs on the fly without having to remove and redeploy the WAR.  They are automatically recompiled on every change. 

However, certain things like changes to configuration files will not be caught unless you change web.xml, which will cause a complete redeploy.  I have had issues with this in the past, and tend to manually redeploy (or kickstart the server) when making such changes.  But depending on the development you're doing, this may be eaiser than doing other things.[/QUOTE]

Those are some subtleties (and conveniences) that I have yet to discover in Tomcat.  I'm glad you added to that.  Thanks.

---

### Post by charlieg on 2006-05-12
For those looking to do Tomcat development, try Eclipse with the plugin by Sysdeo.

Howto:
[http://www-128.ibm.com/developerworks/library/os-ectom/](http://www-128.ibm.com/developerworks/library/os-ectom/)

Plugin:
[http://www.sysdeo.com/eclipse/tomcatplugin](http://www.sysdeo.com/eclipse/tomcatplugin)

---

### Post by Shpongle on 2010-10-09
can anyone tell me how to add the servlet-api.jar to the classpath so i dont have to manually add it to the classpath each time. thanks

---

### Post by Shpongle on 2010-10-09
I figured it out its export CLASSPATH=$CLASSPATH:/directory/to/your/class

add it to /ect/bash.bashrc to keep it persistent

---

### Post by midnight1111 on 2010-12-04
Okay, I am in the same boat being a newbie to servlet development.  I have Ubuntu 10.10 all setup with tomcat6 running.  I have installed the "openjdk".  When I try and compile a Java program is get the following errors, even with the classpath set.

m@ubuntu:~/myapp$ echo $CLASSPATH
/usr/share/tomcat6/lib/servlet-api.jar
m@ubuntu:~/myapp$ 

m@ubuntu:/var/lib/tomcat6/webapps/k2$ !386
sudo javac HelloWorld.java 
HelloWorld.java:4: package java.servlet does not exist
import java.servlet.ServletException;
                   ^
HelloWorld.java:5: package java.servlet.http does not exist
import java.servlet.http.HttpServlet;
                        ^
HelloWorld.java:6: package java.servlet.http does not exist
import java.servlet.http.HttpServletRequest;
                        ^
HelloWorld.java:7: package java.servlet.http does not exist
import java.servlet.http.HttpServletResponse;
                        ^
HelloWorld.java:9: cannot find symbol
symbol: class HttpServlet
public class HelloWorld extends HttpServlet {
                                ^
HelloWorld.java:10: cannot find symbol
symbol  : class HttpServletRequest
location: class HelloWorld
  public void doGet(HttpServletRequest request, HttpServletResponse response)
                    ^
HelloWorld.java:10: cannot find symbol
symbol  : class HttpServletResponse
location: class HelloWorld
  public void doGet(HttpServletRequest request, HttpServletResponse response)
                                                ^
HelloWorld.java:11: cannot find symbol
symbol  : class ServletException
location: class HelloWorld
      throws ServletException, IOException {
             ^
8 errors




THX for the help ahead of time.

---

### Post by myrtle1908 on 2010-12-05
Those servlet classes are in the java**x**.servlet package not java.servlet.

---

### Post by midnight1111 on 2010-12-05
m@ubuntu:/var/lib/tomcat6/webapps/devguide/WEB-INF/classes$ sudo javac HelloWorld.java 
HelloWorld.java:6: class HelloServlet is public, should be declared in a file named HelloServlet.java
public class HelloServlet extends HttpServlet {
       ^
HelloWorld.java:3: package javax.servlet.http does not exist
import javax.servlet.http.*;
^
HelloWorld.java:4: package javax.servlet does not exist
import javax.servlet.*;
^
HelloWorld.java:6: cannot find symbol
symbol: class HttpServlet
public class HelloServlet extends HttpServlet {
                                  ^
HelloWorld.java:7: cannot find symbol
symbol  : class HttpServletRequest
location: class HelloServlet
public void doGet (HttpServletRequest req,
                   ^
HelloWorld.java:8: cannot find symbol
symbol  : class HttpServletResponse
location: class HelloServlet
HttpServletResponse res)
^
HelloWorld.java:9: cannot find symbol
symbol  : class ServletException
location: class HelloServlet
throws ServletException, IOException
       ^
7 errors
m@ubuntu:/var/lib/tomcat6/webapps/devguide/WEB-INF/classes$ echo $CLASSPATH
/usr/share/tomcat6/lib/servlet-api.jar
m@ubuntu:/var/lib/tomcat6/webapps/devguide/WEB-INF/classes$ echo $JAVA_HOME
/usr/lib/jvm/java-1.6.0-openjdk
m@ubuntu:/var/lib/tomcat6/webapps/devguide/WEB-INF/classes$

---

### Post by midnight1111 on 2010-12-06
Still getting the same error as listed above.

---

### Post by myrtle1908 on 2010-12-07
I've never used OpenJDK but would have assumed that the package heirarchy to be the same as Suns.  At least in the EE arena.  Perhaps not.  You probably should be be using the Sun JDK anyway.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

The first error in your output _"HelloWorld.java:6: class HelloServlet is public, should be declared in a file named HelloServlet.java"_ ... is a giveaway.  Do you understand it?  You should.  Rename HelloWorld.java to HelloServlet.java.

Finally, it's best to start a new thread for these questions rather than hijack an old one.

---

### Post by PaulM1985 on 2010-12-08
Are you sure that you are using an enterprise edition jdk rather than a standard edition jdk?  Standard edition does not contain these packages whereas the Enterprise edition does.

EDIT:
Oops.  Didn't see myrtle1908's comment on second page.  I agree with myrtle1908, use Sun for enterprise rather than OpenJDK.
END EDIT

Paul

---

### Post by Tryart on 2011-02-18
I have a problem with deploying WAR file:
I'm using: Ubuntu 9.10, Tomcat6 from the official site, Java from the official site.
My Web-application (DS1) is developed in Eclipse and it works fine there - I can to open page "http://localhost:8080/DS1" in browser.
Then I making WAR file from it by Eclipse.
And interesting things happen when I try to start Tomcat without Eclipse:
1) There are valid CATALINA_HOME and JAVA_HOME variables in the Tomcat startup script.
2) When I deploying WAR into CATALINA_HOME/webapps - I have the war file successfully decompressed there.
3) When I try to open page "http://localhost:8080/DS1" in browser, it is such error "The requested resource () is not available".
4) But when I try to open nonexistent page "http://localhost:8080/DS333", the error becoming like this "The requested resource (/DS333/) is not available".
5) And finally, in Windows everything works fine.

sorry for my English
Heeeeeeeeeeeeeeeelp me please!

---

### Post by Some Penguin on 2011-02-18
The usual starting point would be to examine the access log to first confirm that your request actually reached Tomcat, and then to check catalina and localhost logs to see whether your webapp even deployed properly.

---

### Post by Tryart on 2011-02-18
[Some Penguin]("http://ubuntuforums.org/member.php?u=963358"),  thank You!
I found the solution!
It looks like three instances of Tomcat was started with the Ubuntu start.
It was defined by "ps ax | grep tomcat"
Why? Because of the incorrect tomcat startup file "tomcat6" in /etc/init.d directory.
Here what I did:
1) "sudo update-rc.d tomcat6 remove"
2) Remove file "tomcat6" from /etc/init.d directory
3) Correct catalina.sh from Tomcat/bin directory (initialise variables): CATALINA_HOME, JAVA_HOME, CATALINA_PID ("var/run/tomcat7.pid")
4) Rename and copy catalina.sh to /etc/init.d directory
5) "sudo update-rc.d tomcat7 defaults"

Now I have a working Tomcat7 with the deployment directory CATALINA_HOME/webapps/

---

