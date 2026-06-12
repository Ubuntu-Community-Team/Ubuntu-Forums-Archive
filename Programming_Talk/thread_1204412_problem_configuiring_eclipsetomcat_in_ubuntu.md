---
title: "problem configuiring eclipse/tomcat in ubuntu"
date: 2009-07-04
forum: Programming Talk
---

### Post by badperson on 2009-07-04
I have a server environment set up in eclipse, I start the server (again, within eclipse) and the url [http://localhost:8080](http://localhost:8080) works, I get the tomcat startup page. 

The eclipse workspace is tomcat/webapps. 
the project name is testServlet (tomcat/webapps/testServlet)

There is a web.xml file at tomcat/webapps/testServlet
>   <display-name>Welcome to Tomcat</display-name>
  <description>
     Welcome to Tomcat
  </description>
    <servlet>
      <servlet-name>TestServlet</servlet-name>
      <servlet-class>TestServlet</servlet-class>
    </servlet>
    <servlet-mapping>
        <servlet-name>TestServlet</servlet-name>
        <url-pattern>/TestServlet</url-pattern>
    </servlet-mapping>

the class file (only one so far) is at
tomcat/webapps/testServlet/WEB-INF/classes/TestServlet.class


None of the following url's work:
[http://localhost:8080/testServlet/servlet/TestServlet](http://localhost:8080/testServlet/servlet/TestServlet)
[http://localhost:8080/servlet/TestServlet](http://localhost:8080/servlet/TestServlet)
[http://localhost:8080/TestServlet](http://localhost:8080/TestServlet)


any ideas?
thanks!!
bp

---

### Post by myrtle1908 on 2009-07-05
I assume you are receiving a HTTP 404 error.  Have you actually deployed the application within Eclipse?  Try dragging your project onto the Tomcat server in the Servers tab.

---

### Post by badperson on 2009-07-06
Hi,
that didn't seem to do anything...also, in the post above, I was startup up tomcat from the bin folder in the tomcat install dir...when I try running tomcat within eclipse (it starts up ok) I am get a 404 error when trying to view [http://localhost:8080/](http://localhost:8080/)

bp

---

### Post by badperson on 2009-07-06
I got the localhost url to display when running from eclipse, still having trouble getting the servlet to display. 


***SOLVED *** I added the project to the server, and made sure the eclipse workspace was NOT the tomcat/webapps folder. Then it worked properly. 
bp

---

