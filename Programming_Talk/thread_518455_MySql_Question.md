---
title: "MySql Question"
date: 2007-08-05
forum: Programming Talk
---

### Post by playing_with_matches on 2007-08-05
Hello, sorry if the answer is obvious but I can't find it anywhere.
I want to build an application (both for linux and windows) that needs to use a database that i create.

I figure MySQL would be the best bet.  If I want to distribute my database, does mySQL need to be installed on everyone who uses my app's machine, or is it possible to deploy my database without the whole server (I believe that SQL Server 2005 *gasp* allows you to do something like this).  I rather not have to succumb in using Windows technology, so if anyone has any info on this, please let me know.  thanks.

---

### Post by rrinker on 2007-08-05
You have to install the database engine on each user's system, or use a single database server on the network for all the users to connect to. SQL Server 2005 is no different in this respect, they just divide the product up into different 'editions' where the Express version is meant to install on each computer running essentially a single-user program and the other versions are for installation on dedicated Database servers servicing multiple users. In SQL Server the files are compatible across editions so you can use the same database file on Express Edition as you do on Standard Edition or Enterprise Edition. So you can do development work with Express and deploy on Standard, or vice-versa. No reason why you couldn't do the same with MySQL. I'm pretty sure the database files are compatible from the Linux MySQL to the Windows MySQL, so you can devlope on Linux and deploy to Windows or vice-versa.

---

### Post by pmasiar on 2007-08-05
Why you presume that MySQL is "best"? How your database will be used? Is multiuser access to database server required?

SQLite is just library to access SQL database (without a running server), much simpler than full-blown MySQL, and looks like better fit for your needs - but it is hard to guess when we know nothing about what you need.

---

### Post by Kralizec on 2007-08-05
If this is supposed to be a network tool, I know first hand that MySQL can run as a server allowing remote connection to it. All you would need is an app that would act as a front-end to the server, which will probably be different on different OS's.

---

### Post by playing_with_matches on 2007-08-06
Thanks for all of the help guys.  

> **pmasiar said:**
> Why you presume that MySQL is "best"? How your database will be used? Is multiuser access to database server required?

SQLite is just library to access SQL database (without a running server), much simpler than full-blown MySQL, and looks like better fit for your needs - but it is hard to guess when we know nothing about what you need.

To be honest, I didn't even think of using SQLite.  I really don't need a server, just a database that my program can query, add stuff to, delete, etc.  For cross-platform compatibility, I was aiming to use Java, so if SQLite has support for Java, then I will probably go that route.

---

### Post by pmasiar on 2007-08-06
not sure about java, but Python 2.5 includes SQLite as standard module. And Python is about as cross-platform as Java is, but feels more productive (and not for me only) :-)

---

### Post by AlexThomson_NZ on 2007-08-06
> **playing_with_matches said:**
> Thanks for all of the help guys.  



To be honest, I didn't even think of using SQLite.  I really don't need a server, just a database that my program can query, add stuff to, delete, etc.  For cross-platform compatibility, I was aiming to use Java, so if SQLite has support for Java, then I will probably go that route.

There are JDBC drivers for SQLite (even a nifty example/tutorial I found here: [http://www.pysquared.com/files/Java/JavaSQLiteExample/](http://www.pysquared.com/files/Java/JavaSQLiteExample/))

At work we generally use Derby during the early development phase, that has been quite good for us, but unless you are doing particularly funny queries, the functionality should be pretty similar, and just comes down to what one you find easier to install/manage.

---

