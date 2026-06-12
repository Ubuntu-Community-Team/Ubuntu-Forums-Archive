---
title: "MySQL Connector/J JDBC driver does not work on Linux"
date: 2005-09-17
forum: Programming Talk
---

### Post by blastus on 2005-09-17
I can login to MySQL with...

```
mysql -h localhost -u root -p mysql
```

...no problem and do everything. The problem I have is with the MySQL Connector/J JDBC driver. I have always used mysql-connector-java-3.0.11-stable-bin.jar and it has worked fine on Windows XP (except for idle connection timeouts which is an unrelated issue.) When I try to connect to MySQL with...

jdbc:mysql://localhost/mysql?autoReconnect=true&user=root&password=mypassword

...I get this...

```
Server connection failure during transaction. 
Due to underlying exception: 'java.sql.SQLException: 
Data source rejected establishment of connection,  
message from server: "Host 'localhost.localdomain' is 
not allowed to connect to this MySQL server"'.
```

Does anyone know how to fix this and/or recommend a decent MySQL JDBC driver for Linux? 

I've tried all kinds of tricks like using 127.0.0.1 or localhost.localdomain instead of localhost. I've tried granting all privileges to root@localhost, I've looked at the /etc/mysql/my.cnf and no skip-networking is not on, and I've looked in /etc/hosts and yes my hostname (neo), localhost, and localhost.localdomain is in that file, finally I've messed around with my firewall.

---

### Post by blastus on 2005-09-17
I just tried mysql-connector-java-3.2.0-alpha-bin.jar and same thing...

```
java.sql.SQLException: Server connection failure during transaction.
Due to underlying exception: 'java.sql.SQLException: null,  message from 
server: "#HY000Host 'localhost.localdomain' is not allowed to connect to 
this MySQL server"'.
```

Does ANYONE know how to fix this, ANYONE?? What's the deal with localhost needing permission to connect to itself? It shouldn't need any permissions, it should just be able to open up a socket to the MySQL server and that's it. And what's with "localhost.localdomain" and why is it not just "localhost?"

---

### Post by Keffin on 2005-09-18
I just got this going yesterday. The main 2 things were to edit /etc/hosts and make sure that localhost comes before localhost.localdomain on the first line, and to comment out the skip-networking line in /etc/mysql/my.cnf.

I got both these tips from this thread: [http://www.ubuntuforums.org/showthread.php?t=33601&highlight=java+mysql](http://www.ubuntuforums.org/showthread.php?t=33601&highlight=java+mysql)

Hope this helps.

---

### Post by blastus on 2005-09-18
Thanks Keffin. 

It works now but I don't know why MySQL has to be so fragile regarding this. One shouldn't have to edit the /etc/hosts file just because MySQL can't determine that two hostnames are equivalent. Also, the skip-networking option is supposed to be replaced by the bind-address option. I can't get this working on a distribution that uses the bind-address option instead of the skip-networking option...i.e. I can't make a JDBC connection regardless of whether the bind-address option is enabled or not. I always get an "Access Denied" java.sql.SQLException. Do you know anything about the new bind-address option in /etc/mysql/my.cnf?

---

### Post by Keffin on 2005-09-19
[QUOTE=blastus]Thanks Keffin. 

It works now but I don't know why MySQL has to be so fragile regarding this. One shouldn't have to edit the /etc/hosts file just because MySQL can't determine that two hostnames are equivalent.[/QUOTE]

Amen.

[QUOTE=blastus]Also, the skip-networking option is supposed to be replaced by the bind-address option. I can't get this working on a distribution that uses the bind-address option instead of the skip-networking option...i.e. I can't make a JDBC connection regardless of whether the bind-address option is enabled or not. I always get an "Access Denied" java.sql.SQLException. Do you know anything about the new bind-address option in /etc/mysql/my.cnf?[/QUOTE]

Sorry I know very little about it all, I'd just happened to stumble across the thread I linked to before seeing this one. Perhaps with that option you will also need to specify the port too. Your connection line would then look like this:

```
 conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/databaseName", "user", "password");
```

3306 is the default port for MySQL. 

After getting a noddy program connecting to a MySQL database I moved to using the [Apache Derby](http://db.apache.org/derby/) database instead. It's pure java, zero setup, and, useful for me at work, requires no admin rights to install - just unzip the file and include the jars in your classpath. Of course it may not be suitable for what you're doing, but worth a mention...

Good luck.

---

