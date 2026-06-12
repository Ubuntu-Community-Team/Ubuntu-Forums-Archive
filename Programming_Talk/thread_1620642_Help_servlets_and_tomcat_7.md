---
title: "Help servlets and tomcat 7"
date: 2010-11-13
forum: Programming Talk
---

### Post by psychok7 on 2010-11-13
Hi there... i am coding a school project with java netbeans 6.9 and apache tomcat 7.

I have a running example of a login servlet working, but when i try to implement it in my project it doesnt work.. i am pretty sure my paths are correct, but for some reason that servlet is not loaded even after i choose deploy (maybe im missing something).

Please help me

 

i get 

```


 The requested resource (/BetAndUinWEB/servlet/JavaBeans.LoginServlet) is not available.



```


 my call to the java beans is : 

```



<form action="/BetAndUinWEB/servlet/JavaBeans.LoginServlet" method="post">

Username: <input name="userName" size="10" type="text"> <br>

<br>

Password: <input name="passWord" size="10" type="password"> <br>

<br>

 



```



here is my code under the javabeans package:

```



package JavaBeans;

 

import java.io.IOException;

import java.util.Hashtable;

 

import javax.servlet.RequestDispatcher;

import javax.servlet.ServletException;

import javax.servlet.http.HttpServlet;

import javax.servlet.http.HttpServletRequest;

import javax.servlet.http.HttpServletResponse;

import javax.servlet.http.HttpSession;

 

public class LoginServlet extends HttpServlet

{

    private static final long serialVersionUID = -8608034654794572382L;

 

    private Hashtable<String, String> _users;

 

    public void init()

    {

_users = new Hashtable<String, String>();

        _users.put("khan", "k");

        _users.put("rita", "r");

    }

 

    public void doGet(HttpServletRequest request, HttpServletResponse response) throws IOException, ServletException

    {

String user = request.getParameter("userName");

String pass = request.getParameter("passWord");

 

String verifiedPass;

RequestDispatcher dispatcher;

if ((verifiedPass = (String) _users.get(user)) != null && verifiedPass.equals(pass)) {

   HttpSession session = request.getSession(true);

   User userData = new User();

   userData.setUserName(user);

   session.setAttribute("user", userData);

   dispatcher = request.getRequestDispatcher("jsp/bet.jsp");

}

else

   dispatcher = request.getRequestDispatcher("/invaliduser.html");



dispatcher.forward(request, response);

    }

 

    public void doPost(HttpServletRequest request, HttpServletResponse response) throws IOException, ServletException

    {

doGet(request, response);

    }

 

}

 


```

---

### Post by psychok7 on 2010-11-13
found the solution.. i have to edit a .xml and define the servlets there... thought it was automatic

---

