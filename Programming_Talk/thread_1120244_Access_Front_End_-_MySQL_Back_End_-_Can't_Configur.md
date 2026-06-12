---
title: "Access Front End - MySQL Back End - Can't Configure"
date: 2009-04-08
forum: Programming Talk
---

### Post by Steve R. on 2009-04-08
I can't seem to get my Access database to connect to MySQL using the MySQL ODBC 3.51 Driver.  See attached image.  MySQL is on a UBUNTU computer and Access is on a WindowsXP computer connected on a home lan. I also tested by turning off the WindowsXP firewall.

I get the following error message: [MySQL][ODBC 3.51 Driver]Can't connect to MySQL server on 'localhost' (10061)

In looking around, this appears to type of configuration problem, but I have not found any posting of a "solution".  In fact the lack of reported "problems" would seem to indicate that most attempts at doing this have worked.  Any suggestions on how to solve????????

---

### Post by cabalas on 2009-04-08
Access is trying to connect to a MySQL database on your local machine and not on the ubuntu machine.  I don't know access but I would assume there is an setting somewhere telling it where the database is meant to be located, change that from localhost or 127.0.0.1 to the IP address of the ubuntu machine.

---

### Post by Steve R. on 2009-04-08
> **cabalas said:**
> Access is trying to connect to a MySQL database on your local machine and not on the ubuntu machine.  I don't know access but I would assume there is an setting somewhere telling it where the database is meant to be located, change that from localhost or 127.0.0.1 to the IP address of the ubuntu machine.

That is a possibility, so far all the directions imply using 127.0.0.1.  The IP address needs to be "fixed", and the IP address of the UBUNTU computer will change.
---------------------------------------------------------
I just ran accross this on the [MySQL forum]("http://dev.mysql.com/doc/refman/5.1/en/connector-odbc-configuration-dsn-windows.html"): "*The Database pop-up should automatically populate with the list of databases that the user has permissions to access.*" Since this is not happening I am also wondering about the user permission's to access MySQL.  I thought they were set, but maybe not.

---

### Post by cabalas on 2009-04-08
You should only use 127.0.0.1 when the database is going to located on the same machine that you are running access on - which in your case it isn't.  So you have to set the IP to the ubuntu machine if you want to use the MySQL DB there, if you are worried about the IP changing set the ubuntu machine to a static IP.

---

### Post by Steve R. on 2009-04-08
Ok, looks like you were correct.  I changed by bind-address =192.168.1.102 and one table popped-up.  The test database "world" didn't.  But I will try some more tomorrow. It's now midnight, and I need to get to bed for work.

---

