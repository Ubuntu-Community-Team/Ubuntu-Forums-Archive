---
title: "Putting database info into a bean (JSP)"
date: 2007-07-31
forum: Programming Talk
---

### Post by Brendan Hart on 2007-07-31
Ok so I am creating my user login right, and my teacher is revising for bloody 2hrs when i want to ask him questions but he's busy with students asking about the revision.

So anyways on my sidebar there is a userlogin, at the moment when type in the correct username password it forwards the user to check1.jsp, on that page it checks to see if the username is the same as the pre defined UserName and Password in my bean, if corrent it puts the user name and password into a session object.

Now I want to change that in check1.jsp i want to use the info submitted in the user login, to check the database for valid username and password and if it is, submit the username into a session object.

---

### Post by Brendan Hart on 2007-07-31
I have got my user login working

but...

It seems to have the need to work case sensitive

Anyone know how i can make it not case sensitive

---

### Post by Note360 on 2007-07-31
> **Brendan Hart said:**
> I have got my user login working

but...

It seems to have the need to work case sensitive

Anyone know how i can make it not case sensitive
well you should keep case sensitivity, but if u dont want to you could just convert everything to lower caser.

```

    String lower = [COLOR=#0066ff]*string*[/COLOR].toLowerCase();

```

make both strings lower case and then compare and TADA.

---

### Post by Brendan Hart on 2007-07-31
I actually did that but i know what ill do now.

whenever people sign up ill convert all to lower case, then when they log in I'll convert to lower case, so it doesnt matter either way.

I actually didnt use a bean to compare just made sure the user was in database before storing the user as a session.

```

<%
ResultSet rs;
Connection con;
java.sql.Statement stmt;
%>


<jsp:useBean id="user" class="proCodes.UserData" scope="session" />
<jsp:setProperty name="user" property="*" />


<%
String UserName = new String();
String Password = new String();
UserName = request.getParameter("userName");
Password = request.getParameter("password");
try{
    Class.forName("org.apache.derby.jdbc.ClientDriver"); //load bridge driver
    con = DriverManager.getConnection("jdbc:derby://localhost:1527/jsp","admin","xxxxxx");
    stmt = con.createStatement();
    rs = stmt.executeQuery("SELECT * FROM \"ADMIN\".\"user\" WHERE \"UserName\"='"+UserName+"' AND \"Password\"='"+Password+"'");
    if(rs.next()){
%>
<jsp:forward page="index.jsp"/>
<%
    } else {
        session.invalidate();
%>
<jsp:forward page="register.jsp"/>
<%
    }
} catch(Exception e) {
    out.print(e.getMessage());
    
}
%>

```

---

