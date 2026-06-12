---
title: "Accesing MSSQL Server"
date: 2007-03-15
forum: Programming Talk
---

### Post by graz79 on 2007-03-15
Does anyone know of any tools out there that will allow me to access, administer and program a MSSQL server from my ubuntu machine.  It is the one thing preventing me making the full swap over.

I am after something along the lines of the SQL Managment Studio or MYSQL browser.

Any thoughts, suggestions would be welcomed cos I can find nothing (that does not cost an arm and two legs)

Cheers
Graz

---

### Post by peeps21086 on 2007-03-15
I’m not sure it’s exactly what you are looking fore but you might try [http://www.phpmyadmin.net/home_page/index.php](http://www.phpmyadmin.net/home_page/index.php)

---

### Post by graz79 on 2007-03-16
I am after that sort of tool but to connect to a Microsoft SQL database server (Rather than mySQL)

---

### Post by pmasiar on 2007-03-16
Free software tools to connect to MS SQL are not abundant for the same reason as Tomosaur explained in  thread [futel dying effort](http://ubuntuforums.org/showthread.php?t=385597). It does not make much sense to create tools to access proprietary database which runs on Windows only, if we have at least two free cross-platform databases (MySQL is GPL, Postgres is BSD) which run on Windows *and* Linux. Maybe someone has a project for MS SQL, or some generic functionality can be handled by PHPMyAdmin.

PHPMyAdmin is free software, you have source, and you can start youw own project by modifying modules for MySQL to handle MS SQL,  but for above reasons I do not expect such a project be very popular. From a free software developers, it just does not makes sense to invest time to make MS SQL more usable - contribute for free to MS profits? Just the oposite makes more sense: making free alternatives better and more widely used, we can (1) make free software more palatable for business (2) break MS vendor lock-in (3) force MS to be compatible and play nicely with free software.

So sorry to dissapoint you, but not likely you will find free tools for MS SQL, and if you do, they will not be very important/popular projects. MS Visual Studio might have something, and some versions might be free or very cheap. Eclipse might have something too, maybe.

---

### Post by graz79 on 2007-03-16
That just about sums up my experience.

The need is there for anyone (like me) on a corporate network.  I am MSSQL Dba so need to access the databases.  My laptop is running ubuntu cos it is mine and the less money I give to M$ the better.  My current method is a RDP connection to the SQL box but this is long winded.

I will keep my eye out (or write something myself)

Cheers

Graz

---

### Post by pmasiar on 2007-03-16
> **graz79 said:**
> write something myself

you may want to try web-based front-end, like oracletools/phpmyadmin, so it runs on the same web server you access you MS SQL server, and you can access it from both Ubuntu nad WIndows machines - thus gaining some more possible users and developers.

Good luck!

---

### Post by orengolan on 2007-03-19
Hi graz79,

I have the same problem as you, I need to use something like Enterprise Manager.
I started using Ubuntu on my desktop machine (this weekend) and want to convert my tablet pc.

Maybe the only free solution is VMware. do you have any experience with it?
I hope that it will be comfortable enough (Fujitsu Lifebook P1510D with 500 MB RAM).

---

### Post by robdudley on 2007-11-16
I know this is a little late but there is a tool called Aqua Data Studio which provides access to MSSQL via JDBC.

It's not open source but version 4.7 is free for non-cmmercial use and I've used it on my Mac for quite some time. 

That said I've not managed to get it running under Gutsy yet :-(

Worth a look perhaps?

Rob

---

