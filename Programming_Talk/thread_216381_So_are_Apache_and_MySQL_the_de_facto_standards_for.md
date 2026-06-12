---
title: "So are Apache and MySQL the de facto standards for web development?"
date: 2006-07-15
forum: Programming Talk
---

### Post by Frostmourne on 2006-07-15
On my Windows box I have both programs installed for use with PHP and Rails. I am, however, interested in alternatives that supposedly offer better performance with lower memory requirements, such as lighttpd and SQLite. Although web programming is just a hobby of mine, I would like the option of distributing what I create. If I want my programs runnable almost anywhere, should I stick to developing on Apache and MySQL, or is ensuring compatibility among web servers and database systems not that hard?

Mostly what work on is trivial stuff like message board software and whatnot so I am not sure if I am using advanced Apache or MySQL-specific methods. I would appreciate any input on the subject.

---

### Post by infoburner on 2006-07-15
ive found that rails just runs better when deployed on lighttpd. it is a pain in the *** to set up though. as far as rails is concerned, i think you should develop on whatever platform you are comfortable with. switching a rails app from one platform to another is not much different from deploying it in the first place, especially if you use migrations for your database schema.

---

### Post by Enter on 2006-07-15
well SQL is generally same for every database software although there are some functions like LIMIT which is Mysql extension is not part of ANSI SQL thus not all db servers support it

SO if you want to use a different database software all it takes is making a function libary in php which is swichble etc etc

---

### Post by infoburner on 2006-07-15
the thing about rails migrations is that you write your code in ruby, for example ```
TableName.find_all_by_date(Date.today)
``` so if you use migrations you can change your database backend in two steps. 1) rake migrate target=postgresql (this isnt verbatim) 2) change your database.yml file to reflect new database backend and presto! rails will generate the proper queries for you.

---

### Post by LordHunter317 on 2006-07-15
> **Enter said:**
> well SQL is generally same for every database softwareNot especially.  Basic DML is the same.  DDL is frequently quite different in annoying ways.  Most useful features: triggers, sprocs and UDFs, operators and types, schemas and so on aren't standardized.

Obvious set operations aren't either: UNION's pretty much the only one you're assured of.

As far as the OP: hosting sites worth their salt will host pretty much anything.  More people host Apache, PHP, and MySQL but the sites that only host that aren't worth dealing with.

---

### Post by Oler1s on 2006-07-15
With respect to PHP:

Apache is the standard way to go. It's scalable, industry-standard and backed, etc. I don't think Lighttpd should break compatibility over trivial applications, but if you already have Apache on your system, stick with it.

MySQL is very popular, but on enterprise level Oracle is also widely used. If you're doing trivial applications, stick with MySQL. Because of popularity, anyone who gets your application most like has an AMP stack. SQLite is a library. It's not a standalone relational database like MySQL.

---

### Post by LordHunter317 on 2006-07-15
I wouldn't ever design for MySQL, evne MySQL 5.0 if your target is widespread webhosting (many/most hosts haven't switched yet).  I would design for a real database (PostgreSQL, SQL Server, DB2, Oracle, anything !MySQL really) and then adopt your code to work on MySQL.

It's much eaiser to get schema and ACID requirements correct anywhere else, then get your code working on MySQL where they can't always be met.

---

### Post by fluffington on 2006-07-15
I generally prefer LightTPD and PostgeSQL. Most of my clients (and a few of my own sites, since they're hosted by [DreamHost](http://www.dreamhost.com/r.cgi?117623)) use Apache and MySQL, though, so I usually end up designing for those anyway. And then there are flat-file databases; you'd be amazed how frequently I'm asked to build a site that uses either CSV or XML files for a database, but that's a rant for another day.

---

### Post by ifokkema on 2006-07-16
If you're planning to distribute your project, and it's important for you that your code runs on as many servers out there as possible, I would go for Apache, PHP, MySQL.
- Apache is the world's most used webserver.
- PHP is a very powerful scripting language, written with the sole purpose to build dynamic web pages (it's much more powerful now, though). You can find support for it on tons of hosting providers.
- MySQL is, according to it's developers, the world's most popular open source database. Sure you can develop for Oracle, but that's not as easy to find installed on a hosting provider as MySQL is. Sure there are people putting MySQL down for lots of reasons, and we can fill whole threads with rants & raves about it. However, many big websites use it, such as Wikipedia and Yahoo. I'd say that does mean something.

Just take a look at this forum, and for instance, Wikipedia.org. They run Apache, PHP, MySQL. It's a powerful combination and you'll find this exact combination on tons of hosting providers, therefor capable of running your project.

> **fluffington said:**
> And then there are flat-file databases; you'd be amazed how frequently I'm asked to build a site that uses either CSV or XML files for a database, but that's a rant for another day.
Ouch.

---

### Post by LordHunter317 on 2006-07-16
> **ifokkema said:**
> Sure there are people putting MySQL down for lots of reasons, and we can fill whole threads with rants & raves about it. However, many big websites use it, such as Wikipedia and Yahoo. I'd say that does mean something.Yeah, it means you're not tellign the whole story.  Tehre isn't a single large deployment of MySQL out there that doesn't have heavy, complicated, and aggressive caching on top of it to met their needs, and other tricks to work around its many short comings.

Slashdot?  Wikipedia?  Yahoo?  All heavily use and rely on memcached (far more so than MySQL, in fact).

And regardless of final deployment target, like I said, there are tons of reasons not to do your development on MySQL.

---

### Post by ifokkema on 2006-07-16
> **LordHunter317 said:**
> Yeah, it means you're not tellign the whole story.  Tehre isn't a single large deployment of MySQL out there that doesn't have heavy, complicated, and aggressive caching on top of it to met their needs, and other tricks to work around its many short comings.

Slashdot?  Wikipedia?  Yahoo?  All heavily use and rely on memcached (far more so than MySQL, in fact).

And regardless of final deployment target, like I said, there are tons of reasons not to do your development on MySQL.
So enlighten us about something. Since you make it sound like it's a hundred times easier to switch over to a different DBMS than to apply various measures to 'work around its many short comings', how come they haven't? Or do you consider them (Slashdot/Wikipedia/Yahoo) fools to choose MySQL?

---

### Post by LordHunter317 on 2006-07-16
> **ifokkema said:**
> So enlighten us about something. Since you make it sound like it's a hundred times easier to switch over to a different DBMS than to apply various measures to 'work around its many short comings',No, that's not what I've said.

What I've said is do your development on a different database.  Mainly so you know your *schema is correct*.  Then, port the schema to MySQL and cope with it's shortcomings.  You're going to have to cope with them whatever path you take (it's clearly not optional), but my belief is that it's harder to write and verify a correct schema on MySQL than it is on other databases.

I never said, "Don't use MySQL" even though I could give a long list of perfectly valid reasons as to why to avoid it.  However, I accept that avoiding it may not be a pratical option, and I'm OK with that.  However, I don't believe that even if one must target it, that one should do initial schema design and verification with it.

OTOH, you have to be carefully to not totally rely on features or operations impossible to recreate on MySQL too.  So there's a downside to my solution.

> how come they haven't?The invested amount of work alone may be enough justification not to do it.  

> Or do you consider them (Slashdot/Wikipedia/Yahoo) fools to choose MySQL?Seeing as I don't know all the reasons why, I can't necessarily make that judgement.  What I do know is that choosing MySQL for high performance is going to require a substantial investment in caching and performance tuning to hit your scalability requirements.

I also know that designing correct schemas in MySQL is hard.  Verifying them is even somewhat harder.  MySQL 5.0 does go a long way to fixing that, but at this stage it's difficult to mandate it's presence.  That may change within a year or two.

---

### Post by ifokkema on 2006-07-16
Thanks for your explaination. I do have a question, though. You say that designing correct schemas in MySQL is hard. Which issues do you mean here? Are you referencing to things like enforcing primary/foreign key constraints on DBMS level? CHECKs? Views? Stored procedures?

---

### Post by LordHunter317 on 2006-07-16
Well, it's a small mixture of everything.  It's incorrect handling of NULL and DEFAULT values is one good example.  Lack of ACID-compliance for certain statements (LOCK TABLE being the real sore one).  Lack of sprocs/UDFs and views is another.  

One can find more if they dig far enough. 

I guess my real point is from a correctness POV it's easier to use a database that's stricter and write your code to it.  By writing your code to a stricter standard and then porting to a looser one, you maintain correctness, because you've already shown your code is correct to the stricter standard, even if the database cannot enforce it for you or enforce it as well.

---

### Post by Ryan H on 2006-07-16
You're all getting off topic. The Answer is yes. Apache is the most common Web Server, and MySQL is the most common SQL Database. I develop projects to be used by a large audiance. If I made my PHP applications for SQL Server I would have a lot smaller audiance than with MySQL.

-Ryan H

---

### Post by LordHunter317 on 2006-07-16
Generally though, the web server shouldn't matter at all and database indepedence is easy enough to achieve, so IMHO targeting just MySQL is silly.

---

