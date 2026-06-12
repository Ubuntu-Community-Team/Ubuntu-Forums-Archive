---
title: "Open Source Database Frontends?"
date: 2008-09-23
forum: Programming Talk
---

### Post by DarkOx on 2008-09-23
I'm a fourth-year university student majoring in Accounting, but interested enough in computers that I'm taking a database course as an option for my B.Comm. Our first assignment is to create a database for a hypothetical rent-a-car service. The course mostly focuses on modeling the business process and translating that into a database design; my prof says we can use whatever tools we want for the database so long as he can open it.

I've access to a couple of Microsoft programs that could do the job -- Access 2007 or SQL Server 2005 -- but I was wondering what the Open Source world had to offer. MySQL or PostgreSQL could do the database easily enough, but the project requires a graphical interface. Is there anything I could use to create the user interface, kind of like the way you can create one in Access? Or would I have to learn a programing language a la PHP to do it?

Finally, if I do have to learn a language, which one would be best for this kind of thing? Or is there even a best?

---

### Post by tinny on 2008-09-24
For an open source database solution ive always liked MySQL.

Here are the visual tools for it...

MySQL Database design:
[MySQL Workbench]("http://dev.mysql.com/downloads/workbench/5.0.html")

MySQL Database management:
[MySQL GUI tools]("http://dev.mysql.com/downloads/gui-tools/5.0.html")

---

### Post by pmasiar on 2008-09-24
One of simple solutions would be Python+Django (web framework) + SQLite database. Django includes simple web server. Clean MVC like Django is preferable over PHP solution, IMNSHO.

---

### Post by DrMega on 2008-09-24
> **DarkOx said:**
> MySQL or PostgreSQL could do the database easily enough, but the project requires a graphical interface. Is there anything I could use to create the user interface, kind of like the way you can create one in Access? Or would I have to learn a programing language a la PHP to do it?

Finally, if I do have to learn a language, which one would be best for this kind of thing? Or is there even a best?

I like the PHP + MySQL combination. PHP is easy enough to learn, and MySQL is, as far as I can see, pretty much SQL-92 compliant.

---

### Post by pmasiar on 2008-09-24
I would advise against mySQL, which is full-features multiuser DB server, while SQLite is much simpler single-user library (but implements SQL).

Also, if you can get away with it, avoid GUI or web and program whole thing as simple text-based app (in Python) running in commandline, terminal - it will not look as pretty, but you will eliminate 80% of problems.

---

### Post by stevescripts on 2008-09-24
> **pmasiar said:**
> I would advise against mySQL, which is full-features multiuser DB server, while SQLite is much simpler single-user library (but implements SQL).

Also, if you can get away with it, avoid GUI or web and program whole thing as simple text-based app (in Python) running in commandline, terminal - it will not look as pretty, but you will eliminate 80% of problems.

+1 ...

Also worth mentioning - the OP said his instructor needed to be able to open the db - and SQLite dbs are cross-platform ... 

Steve

---

### Post by DrMega on 2008-09-24
> **stevescripts said:**
> +1 ...

Also worth mentioning - the OP said his instructor needed to be able to open the db - and SQLite dbs are cross-platform ... 

Steve

Open the db on his machine or access the db? I took it to mean the latter, and with talk of a front end requirement that kind of limits any cross platform options that I'm aware of unless it is run as a web app (or other cross platform client-server arrangement).

In my experience as a professional db app developer (on MS stuff), I would always say go for the most robust solution you can afford (MySQL is free for non-commercial use) as in the real world, db projects always evolve to massively exceed the original requirement.

---

### Post by kamaji792 on 2008-09-24
I've been fighting the database / interface game recently.

Like a lot of people I opted for MySQL (It will be running in a multi-user environment).

I'm a competent programmer and I have spent some time trying to get to grips with PHP but in the end I opted for Java.  Java may not be the way to go if you are new to it.  I come from a 'C' programming background and played with Java every now and then.  To me Java is 'C' with object orientation.  Most importantly you have to define variables before you use them.

My plan is to use Java for the data entry and updating side of the database and probably use PHP for reading the database.

The big tipping point when deciding weather to use PHP or Java was finding the NetBeans IDE.  It is the best IDE I have ever used (though I have never used Visual studio) that and re-discovering Java - I was sold.

Additionally my development tools have to come for free :)

Just my 2 peneth.

PS - NetBeans IDE can be used for just about any development you want to do PHP, C++  not that I have tried.  I think you can even use it to manage a MySQL database.

---

### Post by drubin on 2008-09-24
> **tinny said:**
> 
MySQL Database design:
[MySQL Workbench]("http://dev.mysql.com/downloads/workbench/5.0.html")

> Please note that at this point only the Windows release is available. Linux and OS X releases will be available in 2008.

They have not been released not as far as I could tell. 

There is a simple mysql-query-browser
> sudo apt-get install mysql-query-browser

---

### Post by tinny on 2008-09-24
> **rubinboy said:**
> They have not been released not as far as I could tell. 

There is a simple mysql-query-browser

Yeah MySQL Workbench is only available for Windows right now. However they must be getting close to a Linux release (which im itching for!) 

[http://dev.mysql.com/workbench/?p=156](http://dev.mysql.com/workbench/?p=156)

The other option is [DBDesigner4]("http://fabforce.net/dbdesigner4/")

Remember the above are just visual design tools. MySQL GUI tools (Database management) is available for Linux and is also available in the Ubuntu repositories :)

---

### Post by drubin on 2008-09-24
> **tinny said:**
> Yeah MySQL Workbench is only available for Windows right now. However they must be getting close to a Linux release (which im itching for!) 

[http://dev.mysql.com/workbench/?p=156](http://dev.mysql.com/workbench/?p=156)

I personally feel that there are MUCH better mysql GUI tools for windows then linux. I still use sqlyog through wine. 

I just feel that a easy to use light weight GUI is a must I mean there is phpMyAdmin but I feel it just doesn't cut it.

---

### Post by tinny on 2008-09-24
> **rubinboy said:**
> I personally feel that there are MUCH better mysql GUI tools for windows then linux. I still use sqlyog through wine. 

I just feel that a easy to use light weight GUI is a must I mean there is phpMyAdmin but I feel it just doesn't cut it.

Yeah im not a phpMyAdmin fan either.

sqlyog and MONyog look interesting, I havent seen them before but ill be trying them out :)

---

### Post by drubin on 2008-09-24
> **tinny said:**
> Yeah im not a phpMyAdmin fan either.

sqlyog and MONyog look interesting, I havent seen them before but ill be trying them out :)

I am used to sqlyog from my Windows machine.  and runs perfectly under wine.  

I am not 100% sure if it open source. but they have a community edition with is free to use.

---

### Post by TigerCat on 2008-10-07
A company in Texas has been developing a cross-platform RAD tool for a while. The Linux version is free and comes with sqlite integrated for a single user database.

The program is totally awsome. Go to [www.Realbasic.com](www.Realbasic.com) and download the Linux version. It runs slower than the Windows counterpart but still very friendly and usable.

The program is event driven and graphical just like VB6 except and is a reasonable replacement for VB6.

---

### Post by UbuWu on 2008-10-07
[Glom]("http://www.glom.org/") is very nice and similar to access.

---

### Post by tazz4vr on 2008-10-08
Okay, :shock: I was looking into this thread for more or less, mysql vs sqlite...As with orig poster, I too have to do a database from scratch, however mine is work related.  
So my question is, after reading the posts, checking out examples, the last is of 'Glom', it looks good, appears as though I could master it..what are others thoughts on this 'glom'
Also...I have approx 2 weeks to get this database in some sort of hopefully working order 8-[.

---

### Post by mssever on 2008-10-09
> **TigerCat said:**
> A company in Texas has been developing a cross-platform RAD tool for a while. The Linux version is free and comes with sqlite integrated for a single user database.

The program is totally awsome. Go to [www.Realbasic.com]("http://www.Realbasic.com") and download the Linux version. It runs slower than the Windows counterpart but still very friendly and usable.

The program is event driven and graphical just like VB6 except and is a reasonable replacement for VB6.Problems:

[LIST]
[*]RealBasic isn't a database, as the OP specified
[*]RealBasic isn't open source, as the OP specified
[*]RealBasic is a BASIC dialect, which alone should be enough to terrify people :)
[*]Subjective: The only RealBasic program I've used has a really quirky GUI. Now, I'm sure some of that is due to the programmer, but some seems to be a fault of RealBasic itself. E.g., the widgets don't match the system. What kind of idiot would invent their own GUI toolkit for a language clearly targeted at Windows instead of using the Windows API which is guaranteed to be superior to a home-grown solution?
[/LIST]

---

### Post by tazz4vr on 2008-10-09
crossing RealBasic off my list....

---

