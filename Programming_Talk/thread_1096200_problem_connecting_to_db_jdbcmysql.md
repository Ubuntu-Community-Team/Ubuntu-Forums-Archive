---
title: "problem connecting to db: jdbc/mysql"
date: 2009-03-14
forum: Programming Talk
---

### Post by badperson on 2009-03-14
Hi,
I'm having a problem connecting to the db. 
I have the jdbc driver installed, and connecter-j is on my build path. 
Here's the relevant code:;

```
			Class.forName(className);
			
			// set user/pw
			Properties p = new Properties();
			p.put("user", "user");
			p.put("password", "pw");
			
			// establish connection
			Connection con = DriverManager.getConnection(CONNECTION,p);
			System.out.println("Successfully connected to db");
			con.close();
```

It outputs this error:

> via driver com.mysql.jdbc.Driver
com.mysql.jdbc.exceptions.MySQLSyntaxErrorException: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '????????????????' at line 1


it's weird to me that there's a sql error when I'm only connecting, not inserting or running a query. Anyone else run into this? 

also, 
I was able to run this successfully off the command line. The issue described above occurred running the app in eclipse. I'm running 64 bit ubuntu, and I had heard that there were weird little issues with eclipse on that platform...anyone else ever run into that? 
bp

---

### Post by The Cog on 2009-03-14
I don't have access to mysql stuff to check at the moment, but I think maybe it should be "passwd" not "password". Just a thought.

---

### Post by badperson on 2009-03-15
figured it out...I changed the version of the jdk I was using and that solved the problem. 
bp

---

### Post by myrtle1908 on 2009-03-15
Or

[PHP]DriverManager.getConnection(MYSQL_URL + MYSQL_DBNAME, MYSQL_USERNAME, MYSQL_PASSWORD);[/PHP]

---

### Post by jamespi on 2009-04-02
I had the same syntax error message when trying to get openoffice.org 2.4 on intrepid to connect a remote mysql database via JDBC. The solution was to go to options->openoffice.org->java

i had "use java runtime environment" ticked already, and after a short delay the list of possible runtimes was populated with one item "SUN Microsystems Inc. 1.6.0_0".

This item had a radio button next to it that was not selected. I selected the radio button and clicked ok. I restarted ooo.org and after this is could connect to the MySQL db through JDBC without a hitch.

---

