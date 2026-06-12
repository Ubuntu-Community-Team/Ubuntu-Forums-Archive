---
title: "Unable to create table on oracle. Netbeans with Jsp."
date: 2011-10-16
forum: New to Ubuntu
---

### Post by obedraju on 2011-10-16
Hi...
I have run the following code. Everything works on eclipse n netbeans. It shows output on page. But the problem is, i am unable to find any table created on oracle.

Code
-----------------------------------------------------------------
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">

<%@page import="java.sql.*;"%>

<%
try
{
	Class.forName("oracle.jdbc.driver.OracleDriver");
	Connection con = DriverManager.getConnection("jdbc:oracle:thin:@localhost:1521:XE","system","obedraju");
	PreparedStatement ps = con.prepareStatement("create table obedraju(obed varchar2(399))");
	System.out.println("Loading driver");
}
catch(Exception s)
{}

%>

<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Insert title here</title>
</head>
<body>
Done...
</body>
</html>
-----------------------------------------------------------------

I have downloaded ojdbc14.jar and added to the project.

Can any one help me in getting table created on oracle database. 


Thnx...

---

### Post by obedraju on 2011-10-18
***Dont use 'ubuntu forums'... Its waste for users. Try another. No one gives reply here.

---

