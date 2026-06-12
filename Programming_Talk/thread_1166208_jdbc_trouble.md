---
title: "jdbc trouble"
date: 2009-05-21
forum: Programming Talk
---

### Post by patrickyount on 2009-05-21
I've downloaded the connector/j driver and set the classpath variable but still cannot connect to my (mysql) song database. I've written scripts that have connected to the same db in perl and recently decided to try to do the same in java but have had a lot of trouble getting started.

here is my code:
```
import java.sql.*;

public class SongDetect
{
  public static void main(String[] args)
  {
    System.out.println();

    Connection con = null;

    try
    {
      Class.forName("com.mysql.jdbc.Driver").newInstance();        //load jdbc driver

      String username = "analysis",
             password = "yyyy",
             dbURL    = "jdbc:mysql://localhost/song";            //jdbc:subprotocol:subname

      con = DriverManager.getConnection(dbURL, username, password);
      System.out.println("\tSuccessfully connected to database");

    } 
    catch(Exception e)
    {
      System.out.println("\tCannot connect to database.");
      System.err.println("\tException: " + e.getMessage() + "\n");
    }
    finally
    {
      try
      {
        if(con != null)
          con.close();
      }
      catch(SQLException e)
      {}
    }
  }
}
```here is the output:
```
    Cannot connect to database.
    Exception: Access denied for user 'analysis'@'localhost' to database 'song'
```i am 100% sure my username and password are correct and here is even a mysql query for you:
```
mysql> select current_user();
+--------------------+
| current_user()     |
+--------------------+
| analysis@localhost | 
+--------------------+
1 row in set (0.00 sec)

```what am i doing wrong?

---

### Post by cl333r on 2009-05-21
I don't know what's the matter, but can you also put the stack trace here? ( Exception.printStackTrace() )

---

### Post by Zugzwang on 2009-05-21
Try to database managerment tool from sourceforge that is programmed in Java and see if it works there. This allows you to track whether there's a problem with your code or if probably the method of connection causes the problem.

---

### Post by sujoy on 2009-05-21
like cl333r said a stack trace will be useful

besides, its understandable that you can connect to mysql using the username password. but do you have permission to use the song db?

login to mysql
and do
```
use song;
```

if that works, then i am pretty stumped. though at this point i believe you dont have permission to acess that particular db, check your grant table

---

### Post by HotCupOfJava on 2009-05-22
I'm not sure if this is the problem, but I notice that when you declare the Connection, you go ahead and initialize it to null. Then you try to create a real Connection later. Try dropping the null initialization and go for the straight declaration.

---

### Post by jespdj on 2009-05-22
> **HotCupOfJava said:**
> I'm not sure if this is the problem, but I notice that when you declare the Connection, you go ahead and initialize it to null.
That is certainly not the cause of the problem.

Instead of "jdbc:mysql://localhost/song", try the following JDBC URL: "jdbc:mysql://localhost:3306/song"

Note that 3306 is the default port that MySQL listens on.

---

### Post by txcrackers on 2009-05-22
Users/permisisons have to be set explicitly in MySQL - does this user have access to the DB "song"?

---

### Post by patrickyount on 2009-05-26
thanks for the replys.. i took the weekend off and am back working on it again today.

ok.

removing the connection initialization did not solve the problem.

'analysis' **does** have the appropriate permissions and **can** use 'songs'.

my initial thought was that my database url was wrong so i thought @jespdj's reply would help.. but access was still denied even after changing dbURL to 'jdbc:mysql://localhost:3306/song'. is it possible the port MySQL listens on was changed (from default 3306)? if so, how do i find out what it is?

here is the stack trace.

```
analysis@analysis-desktop:~/Desktop/pat$ java -cp .:/home/analysis/mysql-connector-java-5.1.7/mysql-connector-java-5.1.7-bin.jar SongDetect

    Cannot connect to database.
    Exception: Access denied for user 'analysis'@'localhost' to database 'song'

com.mysql.jdbc.exceptions.jdbc4.MySQLSyntaxErrorException: Access denied for user 'analysis'@'localhost' to database 'song'
    at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
    at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
    at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
    at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
    at com.mysql.jdbc.Util.handleNewInstance(Util.java:406)
    at com.mysql.jdbc.Util.getInstance(Util.java:381)
    at com.mysql.jdbc.SQLError.createSQLException(SQLError.java:1030)
    at com.mysql.jdbc.SQLError.createSQLException(SQLError.java:956)
    at com.mysql.jdbc.MysqlIO.checkErrorPacket(MysqlIO.java:3515)
    at com.mysql.jdbc.MysqlIO.checkErrorPacket(MysqlIO.java:3447)
    at com.mysql.jdbc.MysqlIO.checkErrorPacket(MysqlIO.java:911)
    at com.mysql.jdbc.MysqlIO.secureAuth411(MysqlIO.java:3953)
    at com.mysql.jdbc.MysqlIO.doHandshake(MysqlIO.java:1276)
    at com.mysql.jdbc.ConnectionImpl.createNewIO(ConnectionImpl.java:2048)
    at com.mysql.jdbc.ConnectionImpl.<init>(ConnectionImpl.java:723)
    at com.mysql.jdbc.JDBC4Connection.<init>(JDBC4Connection.java:46)
    at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
    at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
    at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
    at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
    at com.mysql.jdbc.Util.handleNewInstance(Util.java:406)
    at com.mysql.jdbc.ConnectionImpl.getInstance(ConnectionImpl.java:302)
    at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:282)
    at java.sql.DriverManager.getConnection(DriverManager.java:620)
    at java.sql.DriverManager.getConnection(DriverManager.java:200)
    at SongDetect.main(SongDetect.java:39)

```

---

### Post by KMuchane on 2009-05-26
Have you tried using MysqlDataSource under the optional  package , you dispense with using the urls and registering the driver.  Lesser code to worry about...

---

### Post by cl333r on 2009-05-26
It seems a syntax exception:
```

com.mysql.jdbc.exceptions.jdbc4.MySQLSyntaxErrorException

```

Going further, you talk about "songs" but use "song" in the code:
> 
'analysis' does have the appropriate permissions and can use 'songs'.


> 
dbURL    = "jdbc:mysql://localhost/song";


Thus I think you should check which one is correct, songs or song.

---

### Post by patrickyount on 2009-05-27
thanks @cl333r!

a little embarrassed.. database is 'songs'.. not 'song'
i spent so much time trying to figure out what was wrong with my database url and it was something so simple..

thanks everyone

---

