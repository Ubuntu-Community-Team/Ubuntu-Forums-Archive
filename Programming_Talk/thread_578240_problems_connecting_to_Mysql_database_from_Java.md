---
title: "problems connecting to Mysql database from Java"
date: 2007-10-17
forum: Programming Talk
---

### Post by THAiSi on 2007-10-17
Hi I just bought a new computer and installed 7.10 on it.

I'm working on a web application in Java using Tomcat and MySQL. I installed everything using the repositories.

On 7.04 (my old PC) everything was working fine. Only now my Java code cannot connect to the database. The database is running fine, and I can access it using phpMyAdmin.

But when I connect to the database from my jsp page I get the following exception.

Communications link failure due to underlying exception: 

** BEGIN NESTED EXCEPTION ** 

java.net.SocketException
MESSAGE: java.security.AccessControlException: access denied (java.net.SocketPermission 127.0.0.1:3306 connect,resolve)

STACKTRACE:

java.net.SocketException: java.security.AccessControlException: access denied (java.net.SocketPermission 127.0.0.1:3306 connect,resolve)
	at com.mysql.jdbc.StandardSocketFactory.unwrapExceptionToProperClassAndThrowIt(StandardSocketFactory.java:407)
	at com.mysql.jdbc.StandardSocketFactory.connect(StandardSocketFactory.java:268)
	at com.mysql.jdbc.MysqlIO.<init>(MysqlIO.java:271)
	at com.mysql.jdbc.Connection.createNewIO(Connection.java:2744)
	at com.mysql.jdbc.Connection.<init>(Connection.java:1553)
	at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:285)
	at java.sql.DriverManager.getConnection(DriverManager.java:525)
	at java.sql.DriverManager.getConnection(DriverManager.java:193)

I know 7.10 has this appArmor stuff etc but I don't know if that is affecting this because I have no idea what appArmor does.

any pointers of what may go wrong in the connection?

---

### Post by AZzKikR on 2007-10-17
Tried telnetting to localhost 3306? 

Did you run Tomcat using sudo?

---

### Post by THAiSi on 2007-10-17
I have not tried telnet yet.

tomcat is running as user tomcat55 it does this automatically after installation using synaptic

PHP is able to connect (since phpmyadmin is working) but I will try telnet as soon as I'm home.

---

### Post by fleet on 2007-10-17
Look I am a real beginer. But I had days of problems using the 5.1.1 connector generating the exact same error. Basicaly I tried everywhere for a solution with no joy and only solved it when I switched to ODBC. Also I've had a bit of history with the previous connector and frankly it was almost unusable it crashed so often.

---

### Post by tenmillionmilesaway on 2007-10-17
The tomcat in the ubuntu repo comes with the security manager on by default.  To be honest Im not sure what this is but looking at your stack trace i would guess that this is your problem.  This page may help you  [http://jspwiki.org/wiki/BugFailsToLoadOnUbuntuDapperInstall](http://jspwiki.org/wiki/BugFailsToLoadOnUbuntuDapperInstall) turn it off but i i guess that googe is your friend in this case.  You could also try installing the Tomcat from the tomcat home page rather than the one in the repo.

---

### Post by THAiSi on 2007-10-18
thanks!
turning the security manager of in /etc/default/tomcat5.5 did the trick!

thanks you guys for your help!

---

