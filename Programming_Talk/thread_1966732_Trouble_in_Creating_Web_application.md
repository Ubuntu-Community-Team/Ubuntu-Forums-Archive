---
title: "Trouble in Creating Web application"
date: 2012-04-27
forum: Programming Talk
---

### Post by UmaRaman on 2012-04-27
Hi all, 

    I am new to eclipse and tomcat. Currently I am creating a web application with servlet,jsp, technologies and tomcat v7 server using Eclipse IDE on linuxmint OS.

While submit my form i got this error.

[http://localhost:8080/SampleWebApp/Add](http://localhost:8080/SampleWebApp/Add)


[COLOR=#000000][FONT=sans-serif][COLOR=black][FONT=Tahoma]**HTTP Status 404 - /SampleWebApp/Add**

[COLOR=black][FONT=Tahoma]**type** Status report[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]**message** _/SampleWebApp/Add_[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]**description** _The requested resource (/SampleWebApp/Add) is not available._[/FONT][/COLOR]
**Apache Tomcat/7.0.12**

[/FONT][/COLOR]
[/FONT][/COLOR] 
Here are the details:

Addjsp1.jsp (SampleWebApp/WebContent)

     <%@page import="com.*;"%>
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>

<head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Insert title here</title>
</head><body>
<form name="userform" method="post" action="Add">
<table>
<tr><td> <td align= "center">AddUser</td></tr>
<tr><td>FirstName</td><td><input type="text" name="first_name" value=""></td></tr>
<tr><td>LastName</td> <td> <input type="text" name="last_name" value=""></td></tr>
<tr><td>UserName</td><td> <input type="text" name="user_name" value=""></td></tr>

<tr><td>Country</td><td> <input type="text" name="country" value=""> </td></tr>
<tr><td>Password</td><td> <input type="text" name="password" value=""> </td></tr>
<tr><td></td>
<td input type="button" name="save" ></td><td><input type="submit" name="Submit" value="Save" style="background-color:#49743D;font-weight:bold;color:#ffffff;"></td></tr>
</table></form></body></html>

Servlet: AddUser.java located  SampleWebApp/JavaResources/src/com

tomcat Located in: home/apache-tomcat-7.0.27-src

Please help me solve this pblm
Thanks in advance

uma

---

