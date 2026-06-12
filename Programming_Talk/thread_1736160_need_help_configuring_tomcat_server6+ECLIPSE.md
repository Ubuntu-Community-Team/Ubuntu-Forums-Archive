---
title: "need help configuring tomcat server6+ECLIPSE"
date: 2011-04-22
forum: Programming Talk
---

### Post by ravikanth.vva on 2011-04-22
i installed eclipse(helios)+tomcat6-----i want to compile a java servlet(its my first)......i added the servlet to tomcat server by right clickin the server in the bottom tab.......then started the tomcat again by right clicking the tomcat.....when i try to run it in the browser by typing===[B][I][http://localhost/MyFirsrServlet/](http://localhost/MyFirsrServlet/)

[/I][/B]i get

**Not Found**

 The requested URL /MyFirsrServlet/ was not found on this server.
  Apache/2.2.16 (Ubuntu) Server at localhost Port 80




im a complete beginner and need help

---

### Post by r-senior on 2011-04-22
That error is coming from Apache. Tomcat usually listens on port 8080. Try 

```
http://localhost:8080/MyFirsrServlet
```

If that doesn't work, please post the servlet source code and your web.xml file.

---

### Post by ravikanth.vva on 2011-04-23
yes i tried it..and again the error

**HTTP Status 404 - /MyFirsrServlet**

**type** Status report
**message** _/MyFirsrServlet_
**description** _The requested resource (/MyFirsrServlet) is not available._
**Apache Tomcat/6.0.28**



[SIZE=1]my code is

[SIZE=2][I]<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Insert title here</title>
</head>
<body>
 <form action=" " method="POST">
        First Name: <input type="text" name="firstName" size="20"><br>
        Surname: <input type="text" name="surname" size="20">
        <br><br>
        <input type="submit" value="Submit">
    </form>
</body>
</html>


[/I][SIZE=1]web.xml


[SIZE=2]i have no idea what it is.......im just trying to learn servlets and i read some basics and copied an example program....and im not able to execute it.......im an absolute beginner in need of help

[/SIZE][/SIZE][/SIZE]
[/SIZE]

---

### Post by ravikanth.vva on 2011-04-23
i think its the default in eclipse i did not change anything

---

### Post by r-senior on 2011-04-23
OK, your message is now coming from Tomcat, so that is a step forward.

Your code is not a servlet. It is a JSP with no dynamic content. This part tells me it is a JSP:

```
<%@ [COLOR="Red"]page language="java"[/COLOR] contentType="text/html; charset=UTF-8"
pageEncoding="UTF-8"%>
```

If it had dynamic content (content that may change each time the page is refreshed), a simple example would probably have scriptlet code, e.g. to show the current date and time:

```
<%= new java.util.Date() %>
```

Servlets are Java code that produce dynamic output from an application server such as Tomcat. JSP is a way of creating HTML pages with embedded Java code. The two are very closely related and often used together.

What is your objective? To learn how to write web applications with Java? Do you have a framework that you want to learn beyond that? For example Java Server Faces (JSF), Spring MVC or Struts?

If you could help us with the direction you want to go, we can recommend a tutorial,.

---

### Post by ravikanth.vva on 2011-04-23
i wanna run the file in eclipse using tomcat for the sake of knowing how to do it....i have netbeans.......

iam new to programming....i just started learning java(pretty basic stuff)...i just thought itd be cool to know jsp.......i have the basics of html,css,javascript and xml....i dont know  the platfrms u talked abt....but i sure wanna learn .....any suggestions on going farward with this......thank you

---

### Post by r-senior on 2011-04-23
This is a simple tutorial. Perhaps try and work through this and post if you get stuck:

[http://www.jsptutorial.net/](http://www.jsptutorial.net/)

---

### Post by ravikanth.vva on 2011-04-23
thank you man

---

### Post by anshulmeena on 2011-10-11
:) 
But the main questions is still unanswered about the 404 error.
I have eclipse3.5 and tomcat6 on Ubuntu 11.04. 
I am trying to run Dynamic website project on Tomcat but every time its giving me http 404 error. I am sure Apache2 is setup. I followed every possible solution available on line. Changing the Catalina variable, installing tomcat6 manually, changing workspace and creating sym links and changing the permissions on file according to one of the popular thread on Ubuntu form. 

Still no result..
I have given many hours with zero and frustrating results.

---

