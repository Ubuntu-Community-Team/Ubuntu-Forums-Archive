---
title: "simple q re java database connection"
date: 2008-10-05
forum: Programming Talk
---

### Post by mrodent on 2008-10-05
Hi,

Trying to migrate to Linux.

I have a few projects written in java which, when run on the "dark side" (MS) of my machine, use the jdbc connectivity to connect to MS Access databases.

I seem to have understood that you simply can't connect to MS Access using java in Linux.  OK, that's fine.  I'm happy to convert my MS Access database to some other format, even just export individual tables and manually link them up.

There are 2 problems: what RDBMS app should I use (NB the OpenOffice database app seems VERY basic)?
the other problem is that the Sun documentation on JDBC is completely and utterly confusing (to me anyway) when I approach it from a Linux angle.  

Incidentally, when I say "java" I am talking about the freely distributable Eclipse ... this is not some "Enterprise Edition" or whatever.

Any help would be greatly appreciated!

Mike

---

### Post by ianhaycox on 2008-10-05
One option is MySQL which you can install from the Synaptic Package manager very easily.

Also check out [http://dev.mysql.com/usingmysql/java/]("http://dev.mysql.com/usingmysql/java/") for a guide to connectivity with Java.

You may also wish to install phpmyadmin to manage your database, but you'll need php and apache2, all again in the package manager. There may also be add-ons within Eclispe to help with Db management etc.

---

### Post by xlinuks on 2008-10-05
I used to use MS Access a long time ago. I'm not sure whether it works but try to dump the MS database to a standard sql file and then import that file to a MySQL database. If possible make the dump in UTF8 and import it into MySQL as utf8 as well, that will save you a lot of headaches if you're using or gonna use non english letters.

---

### Post by pp. on 2008-10-05
I do not quite understand the problem.

As far as I know, an MS Access "database" is just a file, and if there's a java package which can process this kind of file, it ought to run in Linux just as it does in Windows or any other platform where the package is available.

That's not the same with "real" databases which are accessible through some kind of service or over the network only.

---

### Post by jespdj on 2008-10-05
> **mrodent said:**
> the other problem is that the Sun documentation on JDBC is completely and utterly confusing (to me anyway) when I approach it from a Linux angle.  

Incidentally, when I say "java" I am talking about the freely distributable Eclipse ... this is not some "Enterprise Edition" or whatever.
JDBC on Linux is exactly the same as JDBC on Windows or any other operating system. Can you explain in more detail what you find so confusing?

Besides MySQL there are other databases you could use. [HSQLDB](http://hsqldb.org/) is a nice and small 100% Java database. I don't know what you use your database for, but HSQLDB is very suited for small applications.

Eclipse is not Java; Eclipse is an IDE, which you can use to create Java programs.

---

### Post by tinny on 2008-10-05
If I was in the OP's situation I would do the following.

My selection of Database would be MySQL and I would use the MySQL migration toolkit to migrate the MS assess DB to MySQL.

The MySQL migration toolkit is part of the MySQL GUI tools bundle.


[http://dev.mysql.com/doc/migration-toolkit/en/index.html](http://dev.mysql.com/doc/migration-toolkit/en/index.html)
[http://dev.mysql.com/downloads/gui-tools/5.0.html](http://dev.mysql.com/downloads/gui-tools/5.0.html)

BTW: JDBC is no different on Linux (This is the point of Java, platform independent). I think you may be confusing the MS assess lock-in to the Windows platform with an inability to run assess on Linux. MS assess sucks anyway so you wont miss it.

---

### Post by mssever on 2008-10-05
If you've been using Access instead of a "real" database, you might find that SQLite meets your needs nicely without having to install a separate server.

---

### Post by pmasiar on 2008-10-05
> **pp. said:**
> As far as I know, an MS Access "database" is just a file, and if there's a java package which can process this kind of file, it ought to run in Linux just as it does in Windows or any other platform where the package is available.

That's not the same with "real" databases which are accessible through some kind of service or over the network only.

That's not true. Access uses MSFT Jet engine. Yes it stores all code and forms as system objects in database, but you can access (small a 8-) ) Jet engine from client programs.

Access is **much** more than just DB library, like SQLite. It suffers from implementation language (VB), which is crap, but with all the wizards, it is actually pretty good for clueless beginners.

---

### Post by mrodent on 2008-10-09
thank you all... quite a few things to chew on there...

to answer jespdj about what I find confusing... for some reason I found it very easy to set up a jdbc thing in WXP: Control Panel --> Admin Tools --> Data Sources ODBC --> User DSN... then it was usable from a java project.

```
connection = DriverManager.getConnection( "MyUserDSN", "", "" );
```

but when I go an look at the idiot's guide JDBC pages I get confused from this point
[https://java.sun.com/docs/books/tutorial/jdbc/basics/connecting.html](https://java.sun.com/docs/books/tutorial/jdbc/basics/connecting.html)

"Loading the driver you want to use is very simple. It involves just one line of code in your program. To use the Java DB driver, add the following line of code:

    ```
Class.forName("org.apache.derby.jdbc.EmbeddedDriver");
```

Your driver documentation provides the class name to use. In the example above, EmbeddedDriver is one of the drivers for Java DB."

This sounds great, but I've no idea where this driver is meant to come from... should I install apache and it all become clear?  Is the "EmbeddedDriver" class specific to each RDBMS...?  If so where does it come from etc.

Bear in mind that I still find Linux very alien at the mo!

Thanks again tho, I shall report back on any success I may have!

Mike

---

