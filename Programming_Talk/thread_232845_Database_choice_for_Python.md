---
title: "Database choice for Python"
date: 2006-08-09
forum: Programming Talk
---

### Post by jethro10 on 2006-08-09
Hi,
i'm getting there with python and now want to choose a database format to use.
Now I chose to learn Python because the mix of Python/glade and Stani's Python Editor are all available for windows and linux and it keeps it familiar at work or home. I was rather hoping for the same in a database choice. It need not be a full blown relational SQL database but hopefully something that works for windows/linux, and possibly smartphones? 

Any ideas?
Jeff

---

### Post by [h2o] on 2006-08-09
I found the nice combination of PyGTK and Glade yesterday, so I am by far experienced. I also tried out the MySQLdb module for Python, and it worked really well. I doubt that it is available for smartphones though, and it might be a bit heavier than what you intended. Other than that I say give it a try.

---

### Post by jethro10 on 2006-08-09
Yes, that seems like it will do the trick. MySQL is available for both platforms. And it seems like a seperate choice for the phone side

If anyone reads past this point, what is the option for really lightweight databases then say, to use on a phone perhaps?

Jeff

---

### Post by LordHunter317 on 2006-08-09
I don't know any phone specific ones, but your life might be made eaiser using SQLite.

---

### Post by ember on 2006-08-09
I'd say, try to go with AdoDB for Python ([http://adodb.sourceforge.net/)](http://adodb.sourceforge.net/)). It will save you some headache if you intend to switch databases afterwards. Also it is very powerful and easy to setup and use.

---

### Post by Daverz on 2006-08-09
> **ember said:**
> I'd say, try to go with AdoDB for Python ([http://adodb.sourceforge.net/)](http://adodb.sourceforge.net/)). It will save you some headache if you intend to switch databases afterwards. Also it is very powerful and easy to setup and use.

Interesting.  Can you use this with .mdb files, or do you need a server?

If the OP needs a server, my  choice -- for features, standards compliance, and documentation -- would be postgresql, otherwise I'd use sqlite.

---

### Post by ember on 2006-08-09
I believe, you can connect to the File via the Microsoft drivers (or others if there are any), the documentation states:

> 
$db =& ADONewConnection('access');
	$dsn = "Driver={Microsoft Access Driver (*.mdb)};Dbq=d:\\northwind.mdb;Uid=Admin;Pwd=;";
	$db->Connect($dsn);


This is for php which I mainly use. Yet I never tried using access. For a lightweight database I'd suppose SQLite, for most web applications MySQL and for those who need a real database PostgreSQL as a backend.

---

### Post by LordHunter317 on 2006-08-09
I would not use MySQL for anything unless one must.

---

### Post by !nkubus on 2006-08-09
Sqlite would be my guess because you can give the application and the database to someone without having to install a server wich is a big plus IMHO

---

### Post by ember on 2006-08-09
> **LordHunter317 said:**
> I would not use MySQL for anything unless one must.

And that is because of what?

---

### Post by LordHunter317 on 2006-08-09
Because it's a terrible database and there are vastly superior free options (both in beer and speech) available?

Unless you're writing something aimed for mass hosting, and even then, I'd still support and develop for MySQL as a secondary choice.

---

### Post by ember on 2006-08-09
Well - I do not quite see what exactly makes MySQL terrible for you, but you are always free to choose. I go with the motto "80% is good enough" here. MySQL may not support all features of SQL/99, it also may not be suitable for all applications out of licensing issues, so you can say "MySQL is not good". But I'd reply "In most cases, it's good enough".
Its main advantage is definitely its high market share and availability in standard distributions.

---

### Post by LordHunter317 on 2006-08-09
> **ember said:**
> I go with the motto "80% is good enough" here.Perhaps, if it did that 80% correctly.  It doesn't.  IT doesn't remotely come close.  And it's clear from the development of things like 5.0 that the MySQL developers clearly don't understand "real" RDMBS needs.  

>  MySQL may not support all features of SQL/99,No one comes even close.

>  it also may not be suitable for all applications out of licensing issues,It has noting to do with that.  The code is crap.  Simple.

If it weren't for the widespread availbilty of it on hosting sites, I suspect most everyone would have moved to PostgreSQL now.  Everyone who does generally never looks back.

---

### Post by ember on 2006-08-09
Could you be more precise on what didn't work? ... I am working with MySQL now for about ten years and I never met any severe malfunctions (other than missing features).

---

### Post by LordHunter317 on 2006-08-09
Google for MySQL Gotchas.  While not all are applicable to 5.0, many are.

I can add my own list.  Most of those sins, however, are simply unforgivable as noted on the site.

---

### Post by jethro10 on 2006-08-10
wow did I start all this!

It is seeming like MySql is too big for my needs after playing with it for a few hours and I may look at others.
Still not too sure but sqlite seems the next one to look at.

thanks
Jeff

---

### Post by ember on 2006-08-10
If you stick with basic database operations and your database won't get to large, go with SQlite. To my knowledge it is the best choice for that kind of tasks.

---

### Post by jethro10 on 2006-08-10
> **ember said:**
> If you stick with basic database operations and your database won't get to large, go with SQlite. To my knowledge it is the best choice for that kind of tasks.

I spent a few hours now lokoing at this and it does seem the idea choice for Db's that are not massive, which is what i'm after.
It has ODBC drivers for allowing MS Access and OOo to connect etc. 

Tools for quickly designing of connecting to it to query it etc.

Seems to integrate easily with Python.

Just a general all rounder that is multiplatform and multi product. Superb!
thanks everyone.

J

---

### Post by sapo on 2006-08-10
[http://kinterbasdb.sf.net](http://kinterbasdb.sf.net)

---

### Post by chonger on 2006-08-18
MySQL had the advantage of having a nice GUI client (toad). When you use InnoDB, you get referential integrity. It also has very good documentation. There are also a good number of commercial companies that work with and build on top of MySQL. It's a very good database to start with.

Personally I've switched from MySQL to PostgreSQL. It seems to be much easier to administer. I think PostgreSQL is a better choice for commerical development (where you can lose your job, your home and your wife if things go wrong). But there's nothing wrong with running MySQL if you are starting to learn.

---

### Post by LordHunter317 on 2006-08-20
> **chonger said:**
> MySQL had the advantage of having a nice GUI client (toad).TOAD works on a ton of DBs.  It'a mainly meant for Oracle.

> When you use InnoDB, you get referential integrity.But not in all useful situations, sadly.

> It also has very good documentation.Not reall.  It's inferior to MS SQL Server's and PostgreSQL's in terms of layout and in comprehensiveness.

> But there's nothing wrong with running MySQL if you are starting to learn.Yes, there is.  Did you read the gotchas list?  Most of those are RDMBS equivalents of unforgivable sins.

---

