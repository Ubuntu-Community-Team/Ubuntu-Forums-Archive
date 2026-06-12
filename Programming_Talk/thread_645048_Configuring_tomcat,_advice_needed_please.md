---
title: "Configuring tomcat, advice needed please"
date: 2007-12-19
forum: Programming Talk
---

### Post by cuco2772 on 2007-12-19
I keep getting this error:

'The requested resource (/servlet/HelloServlet) is not available'. (404)
The servlet is not getting located by tomcat for some reason. 

This happens when I go to localhost:8080/servlet/HelloServlet.
The servlet engine is running, tomcat is running.

I did this:

javac -classpath /usr/local/tomcat/apache-tomcat-6.0.14/lib/servlet-api.jar HelloServlet.java

and I was able to at least compile the servlet into a .class file.

If  you have tomcat installed, there should be an html document on how to configure it somewhere like here :
file:///usr/local/tomcat/apache-tomcat-6.0.14/webapps/docs/config/server.html
I've been studying this document trying to figure out what I need to do, but so far to no avail.

I added the folowing Context element to my context.xml, located in 
$CATALINA_HOME/conf:

<Context path="" docBase="webapps/ROOT" debug="0" reloadable="true"
> crossContext="true">
> </Context>

My HelloServlet.class is located in .../webapps/ROOT/WEB-INF/classes
In addition I added the following element to the bottom of my
..../webapps/ROOT/WEB-INF/web.xml to try to provide some sort of servlet mapping, I think:

 <servlet>
     <servlet-name>HelloWorld</servlet-name>
     <servlet-class>HelloWorld</servlet-class>
  </servlet>

I got this info mostly from doing Google research, so I dont know
how well this applies. 

The only thing I can think of at this point is maybe I need to set my
java -classpath also,  but attempts to set it to my .../classes directory
fail. I'm not sure exactly what it needs to be set to, and if you have
to provide a .class filename every time. Could anybody help clarify
some of this ? Thanx

---

### Post by pmasiar on 2007-12-19
Web app development in java in IMHO nightmare. I struggled with Struts for a long time without success, then paid $50 for MyEclipse plugin for Eclipse, and I can struggle with chance on success now. :-)

Sorry hope some java experts will help you, I try to avoid Java if possible... :-/

---

### Post by AZzKikR on 2007-12-20
Tomcat needs to know how to map the ./servlet/<ServletName> to an actual servlet, I think. I believe there must be something changed  to $CATALINA_HOME/conf/context.xml or server.xml. I can't SSH into my server box at the moment due to a firewall, or else I could tell you what I have changed in Tomcat to make servlets working :S

---

