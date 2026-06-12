---
title: "Java + database"
date: 2006-11-07
forum: Programming Talk
---

### Post by jinxen on 2006-11-07
Hi! if i wan't to create a program that saves for example and idNr, name, about, price into a database? I dont want to use txt files. What is my best option? What should i be using? And is there any tutorials on it? :) I also want to read from the database (the database should be saved in some kind of file) and show the content in the program.

All help is appreciated!

Best regards! Tommy

---

### Post by Tomosaur on 2006-11-07
Uhh. Why not just learn SQL and use PostgreSQL or MySQL?

---

### Post by GorBo on 2006-11-07
> **jinxen said:**
> Hi! if i wan't to create a program that saves for example and idNr, name, about, price into a database? I dont want to use txt files. 

I would start with investigating usage of [SQLite]("http://www.sqlite.org/") or [Berkley DB]("http://today.java.net/pub/a/today/2004/08/24/sleepy.html").

---

### Post by sailingboarder on 2006-11-07
jinxen, im in the same boat u r
i am hoping to make program with an embedded database, and am looking for ideas
i will probably use MySQL or maybe Derby(if i decide 2 program in java)

what would be the best language to use?
i already know java, but am willing to learn something new if it will work better

---

### Post by mad0master on 2006-11-07
Well, i've started with JDBC and Oracle XE, but that was a heavy way.

So learning plan: Java, SQL - and remember that it's a required minimum!

---

### Post by sailingboarder on 2006-11-07
> **mad0master said:**
> Well, i've started with JDBC and Oracle XE, but that was a heavy way.

So learning plan: Java, SQL - and remember that it's a required minimum!

I've looked for guides and books on running sql in java, but have been unsuccessful

does ne1 know a good place 2 start?

---

### Post by johnnymac on 2006-11-07
If you looking for an embedded database...and it's not going to get insane without being pruned and archived...you could always go the XML route.  Many embedded databases are geared around XML since it's quite fast to walk the tree.

---

### Post by DavidBell on 2006-11-08
Openoffice database component uses Hypersonic SQL ([http://www.hsqldb.org/)](http://www.hsqldb.org/)). Might be worth a look becasue you can use OOo as a quick tool for making prototype tables etc. It's written in java. DB

---

### Post by mad0master on 2006-11-08
> **sailingboarder said:**
> I've looked for guides and books on running sql in java, but have been unsuccessful

does ne1 know a good place 2 start?
Do u mean Java in database Procs or Java programm + JDBC + database? I've understood that you need JDBC + database..

In the other case start with PL\SQL first, and then Java **in** database.

---

### Post by _asc_ on 2006-11-08
If you do not want to access the database from other clients but your own program, then I would use an embedded database like Derby
([http://db.apache.org/derby/)](http://db.apache.org/derby/)). You will also find some good documentation on the derby website. BTW, Java 6, which sould be released by the end of this year, will include JavaDB which is basically a version of Derby. So, if you don't plan to release your program before 2007 you might consider trying one of the release candidates of Java 6, which has the additional benefit that Swing is a lot faster.

Resources:

SQL tutorials: 
[http://www.w3schools.com/sql/default.asp](http://www.w3schools.com/sql/default.asp)
[http://www.sqlcourse.com/](http://www.sqlcourse.com/)

Derby docs: 
[http://db.apache.org/derby/manuals/index.html](http://db.apache.org/derby/manuals/index.html)

Java DB tutorial:
[http://java.sun.com/developer/technicalArticles/J2SE/Desktop/javadb/](http://java.sun.com/developer/technicalArticles/J2SE/Desktop/javadb/)

JDBC Tutorial:
[http://java.sun.com/docs/books/tutorial/jdbc/index.html](http://java.sun.com/docs/books/tutorial/jdbc/index.html)

---

### Post by jinxen on 2006-11-08
Ok, i think MySql is the best choice for me, since i have worked in it before, but not in java though. Anyone got any good tutorials on that? 

Regards, Tommy

---

### Post by _asc_ on 2006-11-08
Basically, in Java you access databases through JDBC. So you have to look for JDBC tutorials. I have posted a link to the Sun JDBC tutorial in my pevious post.

For MySQL, you have to get the JDBC driver from the MySQL webpage.

---

