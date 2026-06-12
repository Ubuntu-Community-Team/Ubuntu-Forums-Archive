---
title: "JSP to Oracle with type 4 driver... problem"
date: 2011-10-14
forum: Programming Talk
---

### Post by obedraju on 2011-10-14
Hello...

Am using 'eclipse indigo' for web applications on ubuntu. 
In jsp page I've written the following code.
-----------------------------------------------------------------
<%@page import="java.sql.*;"%>
<%
try
{
Class.forName("oracle.jdbc.driver.OracleDriver");
Connection      con=DriverManager.getConnection("jdbc:oracle:thin:@localhost:1521:xe","system","obedraju");
PreparedStatement ps = con.prepareStatement("create table emp(Id varchar2(29)");

	System.out.println("Loading driver");
}
catch(Exception s)
{}

%>
hello
-----------------------------------------------------------------

I'm getting output on page as 'hello' but table is not created on database.

I've added ojdbc14.jar on eclipse.

folder>build path>configure build path>libraries>add external jar>ojdbc14.jar  'ok'.

Restarted.

Can some one help me plz..!!!

---

### Post by obedraju on 2011-10-15
Its been almost so many hours. None responded.

Could any one solve it please.


Thnx...

---

### Post by obedraju on 2011-10-15
Its been more than 24 hrs. Cud any 1 plz assist me...???


Thnx...

---

### Post by moldaviax on 2011-10-17
Hi

It looks to me like you create the preparedStatement but don't execute it 

eg

ps.executeUpdate();

I'd also recommend closing all the jdbc objects in a finally block - otherwise you might find repeated access of the page uses up all the available db connections :)

M.

Connection con = null;
PreparedStatement ps = null;
try
{
Class.forName("oracle.jdbc.driver.OracleDriver");
con=DriverManager.getConnection("jdbc:eek:racle:thin:  @localhost:1521:mad:e","system","obedraju");
ps = con.prepareStatement("create table emp(Id varchar2(29)");
//execute the query - note different methods required for select statements
ps.executeUpdate();
    System.out.println("Loading driver");
}
catch(Exception s)
//print out exceptions so we can see what is going wrong
{ s.printStackTrace();}
finally{
    //clean up objects
    try{ if( ps!= null)  ps.close(); }catch(Exception pex){pex.printStackTrace();}finally{ ps=null;}
    try{ if( con!=null) con.close(); }catch(Exception cex){cex.printStackTrace();}finally{ con=null;}

}

---

