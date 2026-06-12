---
title: "Accessing oracle database in java"
date: 2011-10-30
forum: Programming Talk
---

### Post by raac on 2011-10-30
Hello guys, I'm new with oracle. I want it to connect my code to my oracle database.
I downloaded the driver and added to the class path.
Then I found this piece of code

```
    public class ConnectToOracleDatabase     {                   public ConnectToOracleDatabase()         {             try             {                 DriverManager.registerDriver(                     new oracle.jdbc.driver.OracleDriver()                 );                 Properties props = new Properties();                 props.put("user", "username");                 props.put("password", "password");                              Connection conn = DriverManager.getConnection(                     "jdbc:oracle:thin:@<HOST>:1521:<SID>",                     props                 );                              try                 {                     // perform some database stuff                 }                 finally                 {                     conn.close();                 }             }             catch (SQLException sqle)             {                 sqle.printStackTrace();             }         }                           public static void main(String[] args)         {             new ConnectToOracleDatabase();         }               } 
```

I installed oracle, and it did not ask me for port or SID, I don't know how to get them.
How can I get them?

---

### Post by raac on 2011-10-30
The code was not displayed correctly in the previous port

```

public class ConnectToOracleDatabase {    public ConnectToOracleDatabase()    {       try    {    DriverManager.registerDriver(       new oracle.jdbc.driver.OracleDriver()    );    Properties props = new Properties();    props.put("user", "username");    props.put("password", "password");     Connection conn = DriverManager.getConnection(    "jdbc:oracle:thin:@<HOST>:1521:<SID>",    props   );     try    {    // perform some database stuff    }    finally    {    conn.close();    }  }    catch (SQLException sqle)     {       sqle.printStackTrace();    } } public static void main(String[] args)   {    new ConnectToOracleDatabase();   } }  
```

---

### Post by raac on 2011-10-30
Sorry guys I can't seem to post the code correctly

---

### Post by raac on 2011-10-30
OK guys, I thought it'd be best if I put the link of the website that explains how to talk with an oracle database in java
 
[http://www.rgagnon.com/javadetails/java-0112.html](http://www.rgagnon.com/javadetails/java-0112.html)
 
Well back to my original question...
 
I installed oracle, and it did not ask me for port or SID, I don't know how to get them.
How can I get them?
 
Is there some sort of query to get that information?

---

### Post by ofnuts on 2011-10-30
> **raac said:**
> OK guys, I thought it'd be best if I put the link of the website that explains how to talk with an oracle database in java
 
[http://www.rgagnon.com/javadetails/java-0112.html](http://www.rgagnon.com/javadetails/java-0112.html)
 
Well back to my original question...
 
I installed oracle, and it did not ask me for port or SID, I don't know how to get them.
How can I get them?
 
Is there some sort of query to get that information?
[http://www.orafaq.com/wiki/ORACLE_SID](http://www.orafaq.com/wiki/ORACLE_SID)

---

### Post by raac on 2011-10-30
Thanks for the response. So, the oracle environment variable is set through a sql query or through an OS command??

---

### Post by raac on 2011-10-30
And about the port, is it a query or something that I can do to find out the port # that is being used on the database?

---

### Post by ofnuts on 2011-10-31
never created an Oracle DB myself, but the SID should be obtainable using the same tool you used to create the DB. 

SID explained: [http://asktom.oracle.com/pls/apex/f?p=100:11:0::::P11_QUESTION_ID:318216852435](http://asktom.oracle.com/pls/apex/f?p=100:11:0::::P11_QUESTION_ID:318216852435)
Finding SID on local DB server: [http://www.dbforums.com/oracle/894215-about-oracle-sid.html](http://www.dbforums.com/oracle/894215-about-oracle-sid.html)

---

