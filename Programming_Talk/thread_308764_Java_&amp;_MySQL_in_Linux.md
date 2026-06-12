---
title: "Java &amp; MySQL in Linux"
date: 2006-11-28
forum: Programming Talk
---

### Post by welshboy on 2006-11-28
Hi guys,

I'm currently re-installing my linux stuff at the moment, and I have a split on my HD of XP & Linux.

My question is this.

For some weeks now, I have been working on a Sales system using the JDBC bits in Java.  I'm looking to do the same in Linux using MySQL instead of Access.

Couple of things I wanna know:

1.   How do I install a MySQL driver for linux
2.   I can create a data base easily enough, however I need to change where the file is kept.  Ideally I want it in the same place as my source code for the programming stuff.

Many thanks.

---

### Post by FyreBrand on 2006-11-28
Look at this article: [**JDBC And MySQL**]("https://help.ubuntu.com/community/JDBCAndMySQL").  A great place to look for getting stuff working is help.ubuntu.com.  You can also get there from the clicking through the Ubuntu main site start page.

---

### Post by stickboy2642 on 2006-11-29
There is a mysql jdbc driver that you can get to connect your app to mysql.  I believe that you can even install it via apt-get in ubuntu.  If not, it can be downloaded from the mysql site.

With regards to storing your data in mysql, it does not work the same as Access does.  Access is designed to store data in a file, where mysql is actually a server.  You cannot just open up a file and view your database.  You will have to connect up to a database server, login, and run your queries against the database.  It does not store data in a file per se, but stores and serves data via the mysql process, so storing the database with your source code will not be possible (well, not in the same sense as with Access).  You can dump all of the SQL code from the database and store it with the code, but you will still have to have a mysql server to upload the data to before it will work.

As for using the JDBC stuff with mysql vs. access, I think you will find that they are relatively similar.  There are a few SQL differences with mysql.  It doesn't support stored procedures (actually, I think mysql 5.0 does now, but it is pretty new), and your connection settings will be quite a bit different,  but it shouldn't be that tough of a transition.

---

### Post by sailingboarder on 2006-12-07
if u want to store ur MySQL database with ur code, you might want to look into an embedded database, but only if u don't need the data for anything other than in ur program 
i can't remember if MySQL has an embedded database, but DerbyDB (by Apache)[http://db.apache.org/]("http://db.apache.org/") is a good option

---

### Post by welshboy on 2006-12-13
Just wanted to say thanks.  I've got mySQL working with the JDBC.  However I do have one more question.

If I wanted to sell an application I'd developed using MySQL and JDBC, would there be a way to deploy the whole thing, or would I need to use something like DerbyDB?  Or re-write the data base on the client's mysql server (or set one up if they didn't have one?)

Many thanks for your patience.

Beers all round!!

---

### Post by gordyt on 2006-12-13
For Java-based applications that we ship to the customer for installation at their site, we use h2, which is a pure-Java database written by Thomas Mueller, the same guy that wrote HSQLDB.  For the same application that we serve online, we use either MySQL or Postgres.  

In addition we use Hibernate.  It provides Object-Relational mapping and database independence.  That way we don't have to worry about coding for differences between the SQL dialects of one database versus another one.

--gordy

---

### Post by Bunro on 2006-12-14
I have installed the Ubuntu AMD 64 version in this version I can not install the java driver.
 Does any body now an other way to make a connection with my MySQL database?
 

 I tride the following also but I am getting the following ERROR:
 ERROR code: 1000
 libodbc.so
 

 And when manully connecting to the database I get the message: isql not found?
 [http://linuxgangster.org/modules.php?name=Content&file=viewarticle&id=10](http://linuxgangster.org/modules.php?name=Content&file=viewarticle&id=10)
 

 Hopefully there is someone how can help me out.
 

 Best regards, Robert

---

### Post by welshboy on 2006-12-14
> **FyreBrand said:**
> Look at this article: [**JDBC And MySQL**]("https://help.ubuntu.com/community/JDBCAndMySQL").  A great place to look for getting stuff working is help.ubuntu.com.  You can also get there from the clicking through the Ubuntu main site start page.

I followed this link to where it taught me how to install mysql and the data base drivers for it.

It's very good.  I heartily recommend it

welshboy

---

### Post by welshboy on 2006-12-14
> **gordyt said:**
> For Java-based applications that we ship to the customer for installation at their site, we use h2, which is a pure-Java database written by Thomas Mueller, the same guy that wrote HSQLDB.  For the same application that we serve online, we use either MySQL or Postgres.  

In addition we use Hibernate.  It provides Object-Relational mapping and database independence.  That way we don't have to worry about coding for differences between the SQL dialects of one database versus another one.

--gordy

Hey gordyt,  

Thanks for the info man.  The certainly to clear things up.  I need to start reading tutorials etc on this.  :)

HSQLDB and h2, are they open source?  If so, how would I go about installing that on my linux box?  I'm using Edgy at the moment.

Many thanks.

welshboy

---

### Post by gordyt on 2006-12-14
> **welshboy said:**
> Hey gordyt,  
HSQLDB and h2, are they open source?  If so, how would I go about installing that on my linux box?  I'm using Edgy at the moment.

welshboy
[LEFT][/LEFT]

Absolutely they are open source.  As far as installation goes, remember this is Java... You just need to have the jar file in your CLASSPATH.  I would recommend H2 for all new development.  The web site is: 

[http://www.h2database.com/](http://www.h2database.com/)

--gordy

P.S. - After looking through the H2 docs, if you need help getting started please feel free to contact me off list.

---

### Post by lloyd mcclendon on 2006-12-15
you're wasting your time, [http://www.gloegl.de/17.html](http://www.gloegl.de/17.html)

hibernate pwnz

---

### Post by welshboy on 2006-12-16
Hey folks,

Yet another question if I may.

I've got the MySQL working perfectly, and I've written a nifty little login dialogue to log in to the data base, with the intention of using it as an opening screen in an app I'm writing.  However, I was chatting to a friend of mine who told me it was a bad idea to have a user connect directly to the data base, that I should write some sort of middle layer.

That I have no problem with.  

My problem is this...

I want the users of the system to be able to use the data base to do the usuall, add people, add courses, add bookings etc.  But I want to make sure that they can log in to the mySQL data base.  How would you go around writing a middle layer that does that?  That doesn't connect people directly, but kind of manages the connection.

Many thanks, and if you're not cross eyed by the time you've read this drivell, you've done well.

---

