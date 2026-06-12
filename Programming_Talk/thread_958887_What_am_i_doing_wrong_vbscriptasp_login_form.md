---
title: "What am i doing wrong? vbscript/asp login form"
date: 2008-10-25
forum: Programming Talk
---

### Post by nite owl on 2008-10-25
My first attempt at server side scripting is below, but it just times out when I try to visit the page. 

What I am trying to do is a simple login form where a user enters there ID and password and it gets checked against a database.

[HTML]
<%@ Language="VBScript" %>
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
  "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"> 

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<link rel="stylesheet" type="text/css" href="assign2.css" />
<head>
<title>Staff Login Page</title>
</head>
<body>
  <h1>Staff Login</h1>
  <form name="login" id="login" action="login.asp" method="POST">
  <p>Please enter your username and password into the corresponding fields below and then click SUBMIT. Click RESET to clear the form.</p>

  <p>Username:  <input type="text" name="uname" id="uname"/><br/><br />
     Password: <input type="password" name="pass" id="pass"/></p>
  <p><input type="reset"  value="reset"/>
     <input type="submit" value="submit"/></p>
<%
	id=request.form("uname")
	pword=request.form("pass")
	if len(id)=0 or len(pword)=0 then
	response.redirect("login.asp")
	else
	set conn = server.createobject("ADODB.connection")
				conn.open "outline", "WhatsNext", "data"
sql = "select staffID, password from Staff where staffID = '" & id& "' and password = '" & pword& "'"
	
        set rs = conn.execute(sql)
	if not(rs.bof and rs.eof) then
	server.transfer("coordinator.asp")
	else
	server.transfer("login.asp")
	end if
end if
	
%>
</form>

 </body>
</html>[/HTML]

---

