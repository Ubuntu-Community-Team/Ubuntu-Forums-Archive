---
title: "Do you know MySQL? Do you want work?"
date: 2006-07-04
forum: Programming Talk
---

### Post by henkdeswardt on 2006-07-04
Do you know MySQL? Do you want work?

My company corrently runs a MRP system off MS Access. This is becoming very problematic! The Access file is about 9 Meg when compressed, and reaches 650 Meg at month end.

We are looking for somebody to convert / re-write the program to MySQL.

Anybody with good knowlage of this, please phone me ASAP!

If I don't get anybody with MySQL experience, I will HAVE to unfortunetely go the MS SQL route!!!!

Phone me soon.

Henk de Swardt
Cell: 083 655 8139

---

### Post by vayde on 2006-07-04
I don't know that Im experienced enough to help you.  I'm pretty small time.  I work with Mysql, and originally came from Access.  Now Im running Mysql with a Perl/Tk front end for my martial arts studio.  

Have you checked out Mysql Migration?  That might be a viable first step for you to move away from Access.

---

### Post by kripkenstein on 2006-07-04
I (and I am sure others here) would help as much as we can to let you stay as far away as possible from Microsoft's SQL offering...

So if you can use basic help/support, feel free to ask.

(About a job, that's not an option for me, but perhaps someone else...)

---

### Post by SteffJay on 2006-07-04
Hello **kripkenstein** I have not ventured into this realm of databases but have a look here  [http://www.softgalaxy.net/access-mysql/index.html](http://www.softgalaxy.net/access-mysql/index.html)  This maybe able to solve your problem. ;) If you would like any other help, you may contact me.

---

### Post by s|k on 2006-07-04
[QUOTE=henkdeswardt]
If I don't get anybody with MySQL experience, I will HAVE to unfortunetely go the MS SQL route!!!!

Phone me soon.

Henk de Swardt
Cell: 083 655 8139[/QUOTE]
Find someone for your position while you're at it, preferably someone who doesn't spaz out about trivial problems and leave their phone number on internet forums. ;/

---

### Post by LordHunter317 on 2006-07-04
:rolleyes: Data migration from Access, even to SQL Server, is anything but a trivial problem.

Date handling in Access is completely unique, so that can create a whole line of issues.  Depending on what queries/reports you're using, reconstruction may have to be done anyway to completely move stuff to the new database.

Access requires for several queries in JET to use seperate queries where it's not necessary in other RDBMSes.  Such things must be rewritten.

Then there are front-end issues.

---

### Post by vayde on 2006-07-04
In my case it was simpler to just dump the tables as text files, load then into mysql, and rebuild the front end.

It wasn't a trival amount of work, but it was completely worth it

---

### Post by LordHunter317 on 2006-07-04
Sometimes, that is the right way forward.  But sometimes, it's easier to keep the Access front-end, especially if the database is report heavy or has a lot of office integration going on (creating Word documents or spreadsheets).  

Replicating reporting well (so that it's easy to change) and the office integration is usally an expensive proposition.

---

### Post by vayde on 2006-07-05
I was totally unable to use Access as a front end.  No matter what I did, it would crash as soon as I loaded the ODBC driver.  Total lockup- and this was back when I still ran XP.  I chalked it up to microsoft not really wanting anyone to be able to use other db's.

You're right though, in my case, having a staff of one (me), compatibility with myself wasn't much of an issue.  I just laid down the law, and told the whole staff that they were going to do it a new way, and that they would like it. :)

---

### Post by LordHunter317 on 2006-07-05
[QUOTE=vayde]I was totally unable to use Access as a front end.  No matter what I did, it would crash as soon as I loaded the ODBC driver.  Total lockup- and this was back when I still ran XP.  I chalked it up to microsoft not really wanting anyone to be able to use other db's.[/quote]I've front-ended Access to MySQL, PostgreSQL, and SQL Server before (as well as some proprietary stuff I can't talk about).  SQL Server was the most stable, but I suspect that's because it's ODBC driver actually sees the most use.  Many of the SQL Server standard tools use ODBC instead of the native driver protocol, so the driver is more refined by nature.  Neither MySQL or PostgreSQL require ODBC for normal operation, nor are the drivers part of the "standard" installation.  As such, their ODBC drivers are somewhat less refined and stable, IME.

One thing I have seen is that Access's error handling at connect-time is crap.  If you have something wrong with your ODBC driver configuration or data source, it'll frequently crash instead of doing the right thing.

---

### Post by vayde on 2006-07-05
So how do you go about connecting Access to Mysql?  I'm beyond needing it, but I have friends that aren't.

We are talking about using an Access .mdb to contain forms, queries and reports that are linked to Mysql tables right?

---

### Post by LordHunter317 on 2006-07-05
You link the tables, like you would any other ODBC data source.  You then build what you need on top of those linked tables.

---

### Post by vayde on 2006-07-05
[QUOTE=LordHunter317]You link the tables, like you would any other ODBC data source.  You then build what you need on top of those linked tables.[/QUOTE]
There has *got* to be more of a trick to it than just that.  That's what I did, over and over, with no success, just lockups.

Your Access mojo must be greater than mine.

---

