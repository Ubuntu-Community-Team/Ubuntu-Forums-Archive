---
title: "PostgreSQL and MySQL"
date: 2007-11-01
forum: Programming Talk
---

### Post by YetAnotherNoob on 2007-11-01
Does anyone use PostgreSQL?  I am thinking about using it for some development.  Seems powerful and free.

PostgreSQL seems to have more features than mySQL, and be slightly more industrial strength.  MySQL has slightly more prohibitive licensing.  

Does anyone have any experience with Postgres?  What are your gripes with it?  have you used other databases: Oracle, SQL server, mySQL?

---

### Post by pmasiar on 2007-11-01
Yes, there are people who successfully use PostgreSQL, and even prefer it over MySQL. Many of them might not hang around this forum. 

You may get higher quality information (with bias :-) ) directly on PostgreSQL website and mailing list. But don't worry, PSQL is alive and kicking, and will stay so for quite a while.

---

### Post by dataw0lf on 2007-11-01
> **YetAnotherNoob said:**
> Does anyone use PostgreSQL?  I am thinking about using it for some development.  Seems powerful and free.

PostgreSQL seems to have more features than mySQL, and be slightly more industrial strength.  MySQL has slightly more prohibitive licensing.  

Does anyone have any experience with Postgres?  What are your gripes with it?  have you used other databases: Oracle, SQL server, mySQL?

I've used Oracle, Firebird, MySQL, and Postgres extensively, and Postgres remains my favorite database.

Why?  Postgres complies with the SQL standard to higher degree;  it's PL languages have been extended to allow you to write PL code in Python and Perl, amongst other languages;  It has materialized views, write ahead logging, and many other extensive features;  and, last, but certainly not least, PostGIS (I used to work for a large aerial photogrammetric company as lead system administrator; PostGIS beat the pants off anything else for storage of geospatial objects).

With the advent of MySQL 5, the gap between the two databases has lessened considerably, but Postgres still has many features that MySQL lacks.  I recommend it wholeheartedly.

---

### Post by ThinkBuntu on 2007-11-01
I've heard rumblings that PostgreSQL is slower than MySQL. I have no benchmarks to back this up though.

---

### Post by dataw0lf on 2007-11-01
In a read focused environment, MySQL will come out with a slight edge over Postgres (one of the reasons for MySQL's use on the web).  But for any enterprise application, Postgres wins, especially with a lot of use of stored procedures.

Generally, though, if I'm writing a lightweight application, that doesn't have much database use, I'll use SQLite.  For most everything else, I use Postgres.

---

### Post by dumbsnake on 2007-11-01
I hear people say MySql is faster, but if you look at the benchmarks, you will notice that many times an older version of PostGres is being used.  I've used both quite a bit and several differences are obvious to me:

1) MySql has full text indexing, in PostGreSQL you must link it with a special library to do this.

2) Under heavy loads, PostGreSQL is way faster than MySQL.  Under light loads it doesn't really matter, but MySQL might be faster.

3) MySql is more widely used

4) PostGreSQL has WAY more features

5) PostGreSQL is way more stable

6) PostGreSQL has a more liberal license

7) PostGreSQL is easier to modify and link custom code into

8) PostGreSQL has better support for asyncronous calls (very powerful in high end programs)

9) The older versions of PostgreSQL have some problems.

10) MySQL is much simpler

Of the 4 main databasing products I'm familiar with, I'd say this:

SQL Server is a pathetic excuse of a relational database.  It is crap.  Period.

MySQL is pretty good if you don't require anything complicated.

Oracle is a solid commercial database.

PostGreSQL is overall the fastest database.  It has the most features.  It has the best license.  It is the most stable.  It is the most customizable.  Overall, it is the best.  Unless you have special circumstances, you ought to use it.



Important: Make sure you use version 8 of PostGreSQL and not version 7.  There have been a good number of big improvements.  Same goes for any DB: use the latest stable version.

Disclaimer:  This is merely my opinon.  Don't discount the importance of #1 and #3.  Also, everyone has different opinions on the matter.  After using MySQL for years, I switched to PostGreSQL.

---

### Post by YetAnotherNoob on 2007-11-01
Some interesting opinions.  I read that mysql does not support transactions or does so only partially?  Wow, I can't beleive that...That definetly makes me lean towards postgres.  also the licensing is better with postgres.

As for SQL server, I have used it extensively.  It is a good database that has heaps of features not supported in mysql.  But obviously it is not what I need as it is windows based and expensive.

Looks like I have some some reading to do on postgres.
:)

---

### Post by CptPicard on 2007-11-01
Oh, the mother of all database flamewars.. yay :)

I use Postgres exclusively. It was over 5 years ago when I started developing for databases and had to make my choice, and at least back then postgres was the only decent choice, as MySQL was a bit of a script kiddie toy that didn't even have proper transaction handling, data integrity enforcement or important SQL features such as subqueries. I hear it's been getting better, but I've stuck to postgres and never been unhappy with it. In the 8.x series even the query optimizer has been improved, so query execution speed is noticeably better from 7.x.

As other people have said, Postgres just feels complete and solid... there no "hacks" to do things with it, as it seems to me to be the case with MySQL. Also it is my impression that the typical MySQL user does a LOT of things in PHP code that should really be handled by the database... database-side processing is something Postgres really excels in, both because of its more extensive datatype system, strong support for stored procedures and its robust views and triggers.

Postgres is a MVCC database which is a way to handle concurrency efficiently. Transaction correctness is of extreme importance for example in the main web application I'm taking care of at the moment -- it handles money, and things just aren't allowed to go wrong. Both referential integrity and transactions must work 100%.

Then there is just simply the userbase differences of the two products that sometimes gives me the creeps a bit... my friend is a PHP+MySQL guy who has been writing small websites for a few years now, and we ended up having a database discussion where he defended MySQL... and ended up saying priceless things like "what are these foreign keys and cascades you've got here in the schema? Why do you care about transactions? :confused:" ... well... there you have it -- if their users do not know or care, why should they? ;)

---

### Post by YetAnotherNoob on 2007-11-01
> **CptPicard said:**
> my friend ... ended up saying priceless things like "what are these foreign keys and cascades you've got here in the schema? Why do you care about transactions? :confused:" ... well... there you have it -- if their users do not know or care, why should they? ;)

Hehe.  I work in the finance industry where transactions are required.  I think unless folks have had experience with high db loads don't understand the necessity.

Nothing feels worse than seeing records in the database that do not match reality.  Customers are NEVER understanding.

:)

---

### Post by dumbsnake on 2007-11-01
> **YetAnotherNoob said:**
>  As for SQL server, I have used it extensively.  It is a good database that has heaps of features not supported in mysql.  But obviously it is not what I need as it is windows based and expensive.

It doesn't support LIMIT and fails to support many standard SQL features.  PostGreSQL puts SQL Server to shame on features.  One thing I do like about SQL Server though is enterprise manager.  Before I knew anything about databases, that was a sweet program to use.  It will build your indexes for you if you don't know what to index on.

---

### Post by ThinkBuntu on 2007-11-02
The percentage of developers (amateurs included) for whom this is a significant issue must be tiny. Here's how I see it: Don't sweat it voluntarily, you'll know when you need to.

---

### Post by dataw0lf on 2007-11-02
> **dumbsnake said:**
> 
SQL Server is a pathetic excuse of a relational database.  It is crap.  Period.


I don't know if you're saying this because of the general aura of "OMG WE LUV LINUX SO WE MUST H8 WINDOZE LOL!!!1ONE" in this forum, but MS-SQL is an excellent database.  It's clustering mechanisms are excellent, and it's a solid and reliable.  I know a DBA who has had a MS-SQL cluster with ten nodes, doing an amazing amount of writes, that has had 100% uptime for the past 4 years.

Yes, imagine that.  There are good Microsoft products as well.  C#, and Visual Studio, are two others.

---

### Post by LaRoza on 2007-11-02
> **dataw0lf said:**
> I don't know if you're saying this because of the general aura of "OMG WE LUV LINUX SO WE MUST H8 WINDOZE LOL!!!1ONE" in this forum, but MS-SQL is an excellent database. 

Yes, imagine that.  There are good Microsoft products as well.  C#, and Visual Studio, are two others.

Perhaps it is, but it doesn't run on anything other than Windows, whereas MySQL and PostgreSQL do. It mostly likely has a price, the others don't, and it probably has a very restrictive EULA. 

C# has good reviews, it has been describe as "What Java should have been", and VS may be good, if that is all the programmer knows, but I see no reason to pay for it.

I know, there is a "free" version, but that still requires a "valid" Windows installation. Geany, and others are Free and work on Windows and Linux.

If you are willing to be tied to a platform, and a restrictive environment, MS's products may be fine. We on Ubuntu forums usually do not use Windows as are primary OS, and value freedom to do as we please. 

Nobody is knocking MS-SQL, because it is a MS product. Some things that they produce are good for some people.

---

### Post by pjkoczan on 2007-11-02
> **YetAnotherNoob said:**
> Does anyone use PostgreSQL?  I am thinking about using it for some development.  Seems powerful and free.

PostgreSQL seems to have more features than mySQL, and be slightly more industrial strength.  MySQL has slightly more prohibitive licensing.  

Does anyone have any experience with Postgres?  What are your gripes with it?  have you used other databases: Oracle, SQL server, mySQL?

I use PostgreSQL extensively, and I have used Oracle, DB2, Sybase/MSSQL, MySQL, and many other small DBMSs in my day.

I like Postgres the best, because:
- completely open source
- great community support
- lots of choices to authenticate (mysql only has its own)
- you don't have to create a bunch of config files and muck with your environment just to use a client (but you can if you want to)
- great multiuser support and performance
- tons of features
- great SQL compliance, and where they break compliance makes sense.

There is, however, one frustration I have about it. Permissions and ownership are greatly tied together, to the point where you have to do a lot if you want to change them (even permissions themselves have ownerships). Take this with a grain of salt since no other enterprise DBMS I've seen offers this...it's actually part of the SQL standard.

Also, the debate for the longest time has been mysql's speed vs. postgresql's features. Each has closed the gap on the other with recent releases, but I've also found that mysql's speed to be very limited. A tweaked mysql is faster than an untweaked postgresql in single-client, read-mostly workloads (and this is most of the published benchmarks), though a comparably tweaked postgres in multi-user or more write-intensive workloads completely blows mysql out of the water.

Anyway, I'm on a few of the postgres mailing lists, if you decide on that and need some mail advice, you might see me respond.

---

### Post by dataw0lf on 2007-11-02
> **LaRoza said:**
> 
If you are willing to be tied to a platform, and a restrictive environment, MS's products may be fine. We on Ubuntu forums usually do not use Windows as are primary OS, and value freedom to do as we please. 


And I'm fine with that.  I, too, have been using Debian as my primary OS (and later, Ubuntu), for over 10 years.  However, people seem to bash Windows because it's, well, what Linux users do.  Rather than formulating their own opinion, they make a blanket statement regarding any product that is in any way associated with Microsoft.  All this does is dilute real debates, and turn them into a mockery, thus not allowing reasonable and thoughtful discussion to continue.  

If he wants to bash MS-SQL, let him cite examples.  Otherwise, it's just more FUD, but this time spread by Linux fanatics.  Microsoft may hold a monopoly on some things;  but on FUD, it does not.

---

### Post by dumbsnake on 2007-11-02
> **dataw0lf said:**
> And I'm fine with that.  I, too, have been using Debian as my primary OS (and later, Ubuntu), for over 10 years.  However, people seem to bash Windows because it's, well, what Linux users do.  Rather than formulating their own opinion, they make a blanket statement regarding any product that is in any way associated with Microsoft.  All this does is dilute real debates, and turn them into a mockery, thus not allowing reasonable and thoughtful discussion to continue.  

If he wants to bash MS-SQL, let him cite examples.  Otherwise, it's just more FUD, but this time spread by Linux fanatics.  Microsoft may hold a monopoly on some things;  but on FUD, it does not.

Dude, I threw a rock at your database and you threw one at me.  As much as I love flame wars, I may just opt out and let you win.  I used SQL server for years and I suggested that I infact like Enterprise manager.  I learned on microsoft products.  I have formed my own opinions.  I'm sorry for insulting something you like, but please don't insult me personally.  That is not called for, ever.

---

### Post by LaRoza on 2007-11-02
<snip />

Misread thread.

---

### Post by dataw0lf on 2007-11-03
> **dumbsnake said:**
> Dude, I threw a rock at your database and you threw one at me.  As much as I love flame wars, I may just opt out and let you win.  I used SQL server for years and I suggested that I infact like Enterprise manager.  I learned on microsoft products.  I have formed my own opinions.  I'm sorry for insulting something you like, but please don't insult me personally.  That is not called for, ever.

I never insulted you personally, but I'm sorry you feel that way.  I hope you'll reread the thread and come to the same conclusion.  And MS-SQL isn't my database;  PostgreSQL is.  But claiming, with no substantiated examples or evidence, that something is terrible, isn't advisable.  I would've taken no issue  if you had cited specific problems that you had previously had with MS-SQL, or known bugs / deprived features;  I probably would've agreed with you on some of them.  But to maintain integrity, you shouldn't make a blanket statement about a database, or any other technology, with no examples or at least a personal anecdote.

It's tantamount to me saying "GOD!  LINUX IS TERRIBLE!", or "PERL JUST SUX DONT USE IT", and just leaving it at that.  At best, people will ignore you;  at worst, people will take your word for granted.  Neither is very appealing.

---

### Post by CptPicard on 2007-11-03
> **dataw0lf said:**
> "PERL JUST SUX DONT USE IT", and just leaving it at that.

Sounds good to me. There is a definite ring of fundamental truth to it, so why waste time on further explanation :-k

---

### Post by pmasiar on 2007-11-03
before slavik will join the discussiont, let me try: Perl is unbeatable in oneliner for parsing files, especially if someone is skilled in Perl craft.

Not I would anyone advise to become skilled, but if anyone is, it is hard to beat. ...

---

### Post by davidomundo on 2008-01-30
I posted some differences in [http://www.wikivs.com/wiki/MySQL_vs_PostgreSQL]("http://www.wikivs.com/wiki/MySQL_vs_PostgreSQL") .

If there are discrepancies or inaccuracies, please correct!

(I'm pro postgresql, by the way)

---

### Post by CptPicard on 2008-01-30
> MySQL's MyISAM engine performs faster than PostgreSQL, but at the cost of transactions, data safety, and various constraints.

Which pretty much sums it up. You really don't need speed if it comes at such a cost.

---

### Post by pmasiar on 2008-01-30
People say that MySQL/MyISAM without transactions is great for databases which are read 99% of the time, and lost transaction is not a disaster - which is case in web apps like forums web shops etc.

---

### Post by nanog on 2008-02-02
> Permissions and ownership are greatly tied together, to the point where you have to do a lot if you want to change them

My frustration with this is what caused me to switch to mysql.

Also, I love phpmyadmin!

---

