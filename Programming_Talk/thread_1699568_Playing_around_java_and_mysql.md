---
title: "Playing around java and mysql"
date: 2011-03-03
forum: Programming Talk
---

### Post by raac on 2011-03-03
Hi, I want to connect a java program with a database that I created but I can't do it. I installed mysql using sudo apt-get install mysql-server. I don't know the default configuration, (i.e. the port number and if it is accessible through any other computer or not) although I looked around and apparently the default port number is 3306. Can someone tell me what is the configuration after my installation??

Anyways, back to my question, I'm trying to access the database with the following code that I found online...I changed user name and password to mine but still it would throw an exception on this statement....

Class.forName ("com.mysql.jdbc.Driver").newInstance ();

(//I put debugging statements and I came up with that conclusion)

Here it is the following code...Please tell me what do I need to do to connect, also I would appreciate if someone tell me what does this mean or do??...

String url = "jdbc:mysql://localhost/test";
Class.forName ("com.mysql.jdbc.Driver").newInstance ()


I REALLY APPRECIATE YOUR HELP

   import java.sql.*;

   public class Connect
   {
       public static void main (String[] args)
       {
           Connection conn = null;

           try
           {
               String userName = "testuser";
               String password = "testpass";
               String url = "jdbc:mysql://localhost/test";
               Class.forName ("com.mysql.jdbc.Driver").newInstance ();
               conn = DriverManager.getConnection (url, userName, password);
               System.out.println ("Database connection established");
           }
           catch (Exception e)
           {
               System.err.println ("Cannot connect to database server");
           }
           finally
           {
               if (conn != null)
               {
                   try
                   {
                       conn.close ();
                       System.out.println ("Database connection terminated");
                   }
                   catch (Exception e) { /* ignore close errors */ }
               }
           }
       }
   }

---

### Post by Some Penguin on 2011-03-03
You really need to think about whether throwing away all the information from exceptions and replace them with unhelpful messages is ever a remotely reasonable thing to do.

Wouldn't surprise me if you haven't properly configured your classpath.

---

### Post by foxmuldr on 2011-03-03
> **Some Penguin said:**
> You really need to think about whether throwing away all the information from exceptions and replace them with unhelpful messages is ever a remotely reasonable thing to do.

It's likely the OP whittled down the original source code for the purposes of public display and ease of understanding.

> Wouldn't surprise me if you haven't properly configured your classpath.

Possibly.  There are open source Java projects out there which use MySql.  I suggest downloading one of those and looking through the code.  Seeing is often the best teacher.

- Rick C. Hodgin

---

### Post by raac on 2011-03-04
will do thank you. I had a class where we worked with SQL, but the database was already setup and we just implement queries. So I didn't learn how to do it from scratch. I looked online and ubuntu has the apt-get install mysql-server but I mean I don't know what going on in the installation.

Thanks

---

### Post by Some Penguin on 2011-03-04
You'll need to ensure that Java can find the appropriate JDBC connector jar in its classpath.  A search for 'mysql jdbc connector' should find out how.  Oracle itself also has JDBC tutorials online; they're a bit dated and low-level (a fair number of people use frameworks like Hibernate because they also want other functionality), but should work for basic purposes and would be useful to understand.

Regarding error reporting, you should *really* look into using Apache's log4j and dumping stack traces and exceptions.  It's normally not useful to catch and report exceptions unless you have a way of identifying what exception was actually thrown.  Exceptions have class names, messages, and stack traces because they're useful.

---

