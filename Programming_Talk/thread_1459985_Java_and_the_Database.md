---
title: "Java and the Database"
date: 2010-04-22
forum: Programming Talk
---

### Post by Uchiha_madara on 2010-04-22
Hi Everyone ,

Connecting Java with Database I Know Just one Methodology this Methodology is 'JDBC' How Can I Connect Java using JDBC ?

Second Question How can I connect Java with Oracle ...?

Note : I am not using [NETBeans, JDeveloper, Eclipse , ...etc]
I installed JDK6 and Working on Text pad ...

---

### Post by ja660k on 2010-04-22
oh the days of programming 3,
you want JDBC.

firstly
[PHP]import java.sql.*;[/PHP]

then you need to load the oracle ODBC driver.
[PHP]
Class.forName("oracle.jdbc.driver.OracleDriver");
[/PHP]

then specify a connection url
the string can look like this, there are variations, look them up. 
```
jdbc:odbc:<DB_NAME>
```
this will connect to local db, domain and port must be used to remote db
[PHP]
Connection con = DriverManager.getConnection("jdbc:odbc:AnyDB", "user", "pass");
[/PHP]

next, create and execute a statement/query, 
[PHP]
Statement statement = connection.createStatement();
String query = "Select * ...";
ResultSet rs = statement.executeQuery(query);

[/PHP]

and last, iterate and display/store the data.
rs.getString(1) returns the first column of data.
you may wish to write a loop to get all resultant strings
[PHP]
while (rs.next())
    System.out.println(rs.getString(1) + " " + rs.getString(2));
connection.close();
[/PHP]

wrap all that in a try catch block and there you have it.

---

