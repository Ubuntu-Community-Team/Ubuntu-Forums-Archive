---
title: "Java/Eclipse - JDBC - MySQL: Communications link failure"
date: 2008-11-23
forum: Programming Talk
---

### Post by pstiady on 2008-11-23
Hello,

Referring to [http://ubuntuforums.org/showthread.php?t=897729]("http://ubuntuforums.org/showthread.php?t=897729"), I have the same problem as *malagant* and still unsolved.  Here is what I have done:

1. I have used java-6-sun-1.6.0.06 and downloaded and extracted mysql-connector-java-5.1.7-bin.jar from [http://dev.mysql.com/downloads/connector/](http://dev.mysql.com/downloads/connector/)... and set the eclipse build path to use the file as an external JAR.

2. I have created a username and password and have successfully login through terminal by command:
$ mysql -u Test -pabc123

The result is:

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 13
Server version: 5.0.51a-3ubuntu5 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> 

3. I am successfully displaying the content of table name in test database by issuing command:

mysql> use test;
mysql> select * from name;

4. In Eclipse, I'm creating a java program as following:


```
import java.sql.*;

public class tryAgain {
	public static void main(String[] args) throws Exception {
		Class.forName ("com.mysql.jdbc.Driver").newInstance ();
		Connection conn = DriverManager.getConnection 
			("jdbc:mysql://localhost:3306/test", "Test", "abc123");
		conn.close();
	}
}
```


5. The result is:

```

Exception in thread "main" com.mysql.jdbc.exceptions.jdbc4.CommunicationsException: Communications link failure

Last packet sent to the server was 0 ms ago.
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:513)
	at com.mysql.jdbc.Util.handleNewInstance(Util.java:406)
	at com.mysql.jdbc.SQLError.createCommunicationsException(SQLError.java:1074)
	at com.mysql.jdbc.ConnectionImpl.createNewIO(ConnectionImpl.java:2120)
	at com.mysql.jdbc.ConnectionImpl.<init>(ConnectionImpl.java:723)
	at com.mysql.jdbc.JDBC4Connection.<init>(JDBC4Connection.java:46)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:513)
	at com.mysql.jdbc.Util.handleNewInstance(Util.java:406)
	at com.mysql.jdbc.ConnectionImpl.getInstance(ConnectionImpl.java:302)
	at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:282)
	at java.sql.DriverManager.getConnection(DriverManager.java:582)
	at java.sql.DriverManager.getConnection(DriverManager.java:185)
	at tryAgain.main(tryAgain.java:6)
Caused by: com.mysql.jdbc.exceptions.jdbc4.CommunicationsException: Communications link failure

Last packet sent to the server was 0 ms ago.
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:513)
	at com.mysql.jdbc.Util.handleNewInstance(Util.java:406)
	at com.mysql.jdbc.SQLError.createCommunicationsException(SQLError.java:1074)
	at com.mysql.jdbc.MysqlIO.readPacket(MysqlIO.java:667)
	at com.mysql.jdbc.MysqlIO.doHandshake(MysqlIO.java:1070)
	at com.mysql.jdbc.ConnectionImpl.createNewIO(ConnectionImpl.java:2048)
	... 12 more
Caused by: java.io.EOFException: Can not read response from server. Expected to read 4 bytes, read 0 bytes before connection was unexpectedly lost.
	at com.mysql.jdbc.MysqlIO.readFully(MysqlIO.java:2455)
	at com.mysql.jdbc.MysqlIO.readPacket(MysqlIO.java:591)
	... 14 more

```

6. I have successfully connect using php and display the content of table name on Firefox using the following php scripts:

```

<?php
// Connect to MySQL database

$host="localhost";
$userdb="Test";
$passdb="abc123";
$namedb="test";
$myconnect=mysql_connect($host, $userdb, $passdb) or exit("Could not connect to database");
mysql_select_db($namedb, $myconnect);
$dt=mysql_query("select * from name");
echo mysql_error();
while($nt=mysql_fetch_array($dt)){
echo "$nt[firstname] $nt[lastname] $nt[sex]<br>";     
}
?>

```

7. Please guide me to troubleshoot the problem.  

Thank you in advance.

Regards,
Patrick

---

### Post by cl333r on 2008-11-23
In Eclipse try not explicitly specifying the MySQL port:
Connection conn = DriverManager.getConnection ("jdbc:mysql://localhost/test", "Test", "abc123");

If still doesn't work try using NetBeans, it now supports PHP very well, if the error persists using NetBeans then you'll at least know that it's not an IDE issue.
[http://www.netbeans.org/downloads/index.html](http://www.netbeans.org/downloads/index.html)

---

### Post by pstiady on 2008-11-26
I have solved the problem.

I edited the file:
$ sudo vi /etc/mysql/hosts.allow

And add a line:
mysqld : 127.0.0.1 : allow

And that's done the trick :)

---

### Post by theDaveTheRave on 2008-11-26
Dear all,

I'm having a similar but different issue.

The error is that the little program can't locate the class for the connector:
error message is
> java.lang.ClassNotFoundException: com.mysql.jdbc.Driver



I've tried changing my CLASSPATH (as suggested on the MySQL site)

```

export CLASSPATH=$CLASSPATH:"/home/davem/downloads/mysql-connector-java-5.1.7
```

- as you can see the connector is in my <downloads> folder currently, once I get things working I will put it somewhere more sensible like <etc/java/connector/> or something (so everyone can see an use it).

I need to get this working, but how can I confirm my current classpath etc?

thanks in advance.

David

---

### Post by Tianna on 2009-07-01
I'm having a similar problem.  
Here is the error:
com.mysql.jdbc.CommunicationsException: Communications link failure

Last packet sent to the server was 0 ms ago.
    at com.mysql.jdbc.SQLError.createCommunicationsException(SQLError.java:1070)
    at com.mysql.jdbc.ConnectionImpl.createNewIO(ConnectionImpl.java:2103)
    at com.mysql.jdbc.ConnectionImpl.<init>(ConnectionImpl.java:718)
    at com.mysql.jdbc.ConnectionImpl.getInstance(ConnectionImpl.java:298)
    at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:282)
    at java.sql.DriverManager.getConnection(DriverManager.java:582)
    at java.sql.DriverManager.getConnection(DriverManager.java:207)
    at testCon.main(testCon.java:16)
Caused by: java.net.ConnectException: Connection refused
    at java.net.PlainSocketImpl.socketConnect(Native Method)
    at java.net.PlainSocketImpl.doConnect(PlainSocketImpl.java:333)
    at java.net.PlainSocketImpl.connectToAddress(PlainSocketImpl.java:195)
    at java.net.PlainSocketImpl.connect(PlainSocketImpl.java:182)
    at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:366)
    at java.net.Socket.connect(Socket.java:519)
    at java.net.Socket.connect(Socket.java:469)
    at java.net.Socket.<init>(Socket.java:366)
    at java.net.Socket.<init>(Socket.java:209)
    at com.mysql.jdbc.StandardSocketFactory.connect(StandardSocketFactory.java:254)
    at com.mysql.jdbc.MysqlIO.<init>(MysqlIO.java:281)
    at com.mysql.jdbc.ConnectionImpl.createNewIO(ConnectionImpl.java:2029)
    ... 6 more
 I have tried changing the $CLASSPATH and I even dropped the driver in the /usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/ext folder.  

I have a program that needs to access my mysql database via localhost.

Does it matter that my username and password that I am passing to getConnection are root and <somepassword>?  I tried changing this to a different user and password who have grant all permissions set.  And the same result.

](*,)](*,)](*,)](*,) I'm sooo stuck.

---

### Post by theDaveTheRave on 2009-07-01
Tianna

if you are using an IDE to develop your system you should be able to set the classpath with that.

The classpath issue seems to be highly <hit and miss> with regards to if it will work or not?

I can't decide if this is a bug or a desired effect, but I read of no end of people who can't get it to function on a persistent basis.

I don't have my "normal" pc on me at the moment, so I can't help you too much, sorry for that.

However I can say this. if you set the classpath in the terminal using the export command it will only set the variable for that single session, open a second terminal and your program won't run there!

so, if you want to run the program, write it, compile it then past the full command line (including the full path to the jar executable) into the terminal that you have set the classpath in.

If your system, still doesn't find the JDBC then you can set the classpath as part of the command line function tool.

I have another thread / post out there where I have explained how I got this to work.... but I can't immediately find it!

Search for my threads /posts with classpath and jdbc keywords.. it should come up!

hope that helps... I'll hunt down the document I wrote for setting the classpath also. If I fail to get back to this thread in a reasonable timescale (I've got some important business over the weekend, so middle of next week.. again appologies for that), then drop me a pm to bump me into action.

David

---

### Post by shijobaby on 2009-11-30
[http://jdbcerrorinfo.blogspot.com/2009/11/communication-link-failure-mysqljdbc.html](http://jdbcerrorinfo.blogspot.com/2009/11/communication-link-failure-mysqljdbc.html)

---

### Post by psnel on 2010-01-28
My Solution for this error:

----------
com.mysql.jdbc.exceptions.jdbc4.CommunicationsException: Communications link failure
...
Last packet sent to the server was 0 ms ago.
...
Caused by: java.net.ConnectException: Connection refused
        at java.net.PlainSocketImpl.socketConnect(Native Method)
...
----------

Changing localhost to 127.0.0.1 did NOT work.
Although having different MySQL server versions on dev pc and deployment host, the jdbc version was not the problem
// jdbc (packaged in .war):
//             mysql-connector-java-5.1.6-bin.jar
// dev mysql:  5.1.37, for debian-linux-gnu
// depl mysql: 5.0.51a-3ubuntu5.4-log (Ubuntu)
// container:  tomcat 6.0

Changing the IP ADDRESS to that of the deployment host WORKED (same host as db?!); But gave another error about the user not having permissions on that host - even though i did previously as mysql root

> grant all privileges on mydb.* to 'myuser'@'%' identified by '####';

(connecting from both localhost & other hosts using mysql cmd-line client did indeed work, but the web-app on tomcat runing on the same host is denied..?)

This fixed the permission problem (specify IP):
> grant all privileges on mydb.* to 'myuser'@'<host-IP>' identified by '####';

- péter

---

### Post by marquonis on 2011-05-13
Check the files:

/etc/hosts.allow 
/etc/hosts.disallow

And ensure you dont have any entries which are blocking Java from making the connection. 

I was also getting the errror:
com.mysql.jdbc.exceptions.jdbc4.CommunicationsException: Communications link failure

then discovered I had left the line: 
mysqld : ALL : ACCEPT
in the hosts.allow file (forgotten about from somehting else I'd been trying previously). 

Commented it out and everything started working again.

---

