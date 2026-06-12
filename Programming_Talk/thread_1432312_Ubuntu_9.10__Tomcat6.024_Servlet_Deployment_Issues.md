---
title: "Ubuntu 9.10 / Tomcat6.024 Servlet Deployment Issues"
date: 2010-03-17
forum: Programming Talk
---

### Post by RobynM on 2010-03-17
Hi,
I am new to Ubuntu and to Servlets in general, and I am having difficulties deploying my first Servlet. I believe that I have Tomcat 6 installed properly and running as I get the Tomcat page when I visit the url [http://localhost:8080](http://localhost:8080). The problem I have is when I create a simple servlet, MyServlet.java and compile it to get MyServlet.class. I have also created web.xml.
When I navigate to my tomcat/webapps directory I create the folder proj1. Inside this folder I create WEB-INF, in which place the file web.xml and also a newly create folder 'classes' which I place the file MyServlet.class.

According to everything I have read this should be sufficient to allow me to visit the url [http://localhost:8080/proj1/servlet](http://localhost:8080/proj1/servlet).

When I do this however I get the http 404 error "resource() not available"
Has anyone come across this problem and discovered a solution?

R.

---

### Post by myrtle1908 on 2010-03-17
Have you referenced you servlet in the web.xml?  Here's an example ...

```
  <servlet>
    <servlet-name>ImageUpload</servlet-name>
    <servlet-class>com.figtree.carica.server.ImageUpload</servlet-class>
  </servlet>
  <servlet-mapping>
    <servlet-name>ImageUpload</servlet-name>
    <url-pattern>/ImageUpload</url-pattern>
  </servlet-mapping>
```

---

### Post by RobynM on 2010-03-17
I sure have.

---

### Post by myrtle1908 on 2010-03-17
Well then to access your servlet you must use the correct URL eg.

[http://localhost:8080/proj1/MyServlet](http://localhost:8080/proj1/MyServlet)

assuming your servlet is named MyServlet.

---

### Post by Some Penguin on 2010-03-18
Verify that you're using the Servlet-Name, and not the class name.

Also, check the catalina.out; it's entirely possible that your servlet threw some exceptions.

---

### Post by RobynM on 2010-03-21
no problems in catalina.out
in fact no exceptions that I can see at all.

I am really stumped as to why I can run the servlet examples but cannot deploy any of my own. I have verified my xml syntax and my java class file(s) repeatedly.

---

