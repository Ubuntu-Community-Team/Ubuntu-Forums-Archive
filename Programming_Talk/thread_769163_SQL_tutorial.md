---
title: "SQL tutorial?"
date: 2008-04-26
forum: Programming Talk
---

### Post by MDSmith2 on 2008-04-26
Does anyone know were i could find a good free sql tutorial?

---

### Post by evymetal on 2008-04-26
It depends how far you want to go...

If you don't know any SQL then I'd suggest:
[http://www.w3schools.com/sql/default.asp]("http://www.w3schools.com/sql/default.asp")

Several people I know learnt their first SQL here, and it's very simple to understand. (although unfortunately they don't explain how to set up a database or table in the first place, but you can google that- "CREATE DATABASE", "CREATE TABLE")

I'd start out by opening a terminal and running whatever commands you want from the MySQL command line - then you can see what's going on.

If you want to get more in-depth then I find reading over the manual for MySQL is very good (assuming you're using MySQL) - whatever you're looking up there are always loads of comments that mention more advanced topics that you can then go and look up.

---

### Post by pmasiar on 2008-04-26
It might also depend what you want. If you want to use some advanced web app framework, like Django in Python, it comes with object-relational mapper (and admin interface), so all you need to do is to define your tables in ORM. All the basic  SQL statements (90% what you ever need, and 100% of what you need first 3 months) can be done as ORM methods, IMHO simpler than SQL (and is already accessible for rest of your code).

HTH, YMMV

---

### Post by MDSmith2 on 2008-04-26
The reason i want to learn sql (I'm using postgresql, btw) is because it sounds interesting and i like to at least get some of the basics down.

---

### Post by LaRoza on 2008-04-26
> **pmasiar said:**
> It might also depend what you want. If you want to use some advanced web app framework, like Django in Python, it comes with object-relational mapper (and admin interface), so all you need to do is to define your tables in ORM. All the basic  SQL statements (90% what you ever need, and 100% of what you need first 3 months) can be done as ORM methods, IMHO simpler than SQL (and is already accessible for rest of your code).


Simpler than SQL? Than that is simple indeed. I will have to look into this ORM (wikipedia, here I come)

Although I do recommend learning SQL. The basics can be learned very quickly, and an interactive MySQL prompt can be a quick way to learn it. The most basic SQL (and the most commonly used) can be learned in one sitting.

---

### Post by LaRoza on 2008-04-26
> **MDSmith2 said:**
> The reason i want to learn sql (I'm using postgresql, btw) is because it sounds interesting and i like to at least get some of the basics down.

The basics of SQL are very easy, you'll get it in no time.

It reads like English, and its most common use can be learned rapidly.

---

### Post by MDSmith2 on 2008-04-26
Cool.
Now, what could i use postgresql databases for in everyday use?

---

### Post by LaRoza on 2008-04-26
> **MDSmith2 said:**
> Cool.
Now, what could i use postgresql databases for in everyday use?

When I learned SQL, I used MySQL (I think Postgresl works the same way in this regard).

I used it for keeping track of my classes and grades, and my ISO collection.

I practiced by using the mysql prompt (sort of like a Python interactive shell).

---

### Post by dempl_dempl on 2008-04-26
There are three tutorials on my site.
You can find them on this page:

[http://www.stosha.net/component/option,com_mtree/task,listcats/cat_id,153/Itemid,/](http://www.stosha.net/component/option,com_mtree/task,listcats/cat_id,153/Itemid,/)

If you have any programming experience, this will be peace of cake for you :) . 
LaRoza is right: SQL it reads almost like English. 

LaRoza: He he... English is sometime a lot harder to read :) . If you live in non-English-speaking country, you'll probably grok MySql a lot easier :D


Cheers!

---

### Post by jflaker on 2008-04-26
Try this 
[http://www.filedump.net/dumped/sqlintro1209260580.pdf](http://www.filedump.net/dumped/sqlintro1209260580.pdf)

It is an SQL Intro....basic, but a good start.

---

### Post by MDSmith2 on 2008-04-26
Thanks guys.
I will read them tomorrow.

---

### Post by pmasiar on 2008-04-26
LaRoza, here is bonus link for you: TurboGears ORM, SQLObject quick intro:
[http://turbogears.org/about/sqlobject.html](http://turbogears.org/about/sqlobject.html) and page2 from 'wiki in 20 minutes': [http://docs.turbogears.org/1.0/Wiki20/Page2](http://docs.turbogears.org/1.0/Wiki20/Page2) which shows template and ORM in action. 

That example seems of course trivial, because it does trivial things. But if you need tricky things, only your controller changes, and you return dict as before, populated with whatever structures you need. Once I needed tree of dictionaries :-)

Can you see now why IMHO ORM is preferable to wrestling plain SQL?

---

### Post by Quikee on 2008-04-27
The good thing about ORM is also that it acts like a additional abstraction and security level above the database. Which means you can switch databases (supported by the ORM framework) in most cases without changing anything in the code (which is not always true if you use SQL) and because the ORM framework takes care of querying the database, security issues like SQL-injection are less likely to happen.

pmasiar: Do you know if some python ORM supports query-by-example so I can construct a example object (tree), feed it to the ORM framework and the framework will return all objects that match my example object?

---

### Post by LaRoza on 2008-04-27
This thread caused me to add SQL to my wiki. 

I hope it helps.

---

### Post by pmasiar on 2008-04-27
> **Quikee said:**
> The good thing about ORM is also that it acts like a additional abstraction and security level above the database. Which means you can switch databases (supported by the ORM framework) in most cases without changing anything in the code (which is not always true if you use SQL) and because the ORM framework takes care of querying the database, security issues like SQL-injection are less likely to happen.

Good comment.

And ORM abstraction can go beyond SQL: Google App Engine database is non-SQL, but Turbogears and Django ORMs can abstract that away - it needs some work, but it is being done.

> Do you know if some python ORM supports query-by-example so I can construct a example object (tree), feed it to the ORM framework and the framework will return all objects that match my example object?

I don't, but surely it would be a nifty feature! :-)

Take a look at SQLAlchemy in TG2 (and Elixir). You can build query by adding filters, it is not by example but is close.

Unfortunately in my work I cannot use those helper wrappers, I query Oracle RDF tripple store using proprietary ORACLE SQL extensions, so... no ORM for me :-(

---

### Post by unutbu on 2008-04-27
Hi MDSmith2, you might also want to check out
the postgresql-doc package. 
```

% apt-cache show postgresql-doc

Description: documentation for the PostgreSQL database management system
 This package contains all README files, user manual, and examples for
 the latest available PostgreSQL version. The manual is in HTML format.

```

PS. I notice a lot of people use MySQL and my unscientific gut feeling is fewer people use postgresql. Does anyone else feel this way, and/or suspect a reason why?

---

### Post by CptPicard on 2008-04-27
> **unutbu said:**
> 
Does anyone else feel this way, and/or suspect a reason why?

It's probably true, and is the subject of yet another emacs vs. vi style holy war on of the tech community. Personally I have always had a preference for PostgreSQL because it was much more mature and a "real database" (ACID and all that) long before MySQL reached that state. It has since caught up I hear.

And regarding ORMs, the "switching databases" argument is IMO a little bit of a red herring... SQL is standardized enough, and the whole use case sounds a little dubious to me... "oh, I had this great idea for our system, let's change databases!". The DB is a fairly integrated component -- the central component often of a system. Then there's the "impedance mismatch" between tables and objects... if you've got a greatly optimized relational database, why hide it behind object abstractions that destroy your ability to leverage the db?

From the Wikipedia page for SQLAlchemy, another ORM... "SQLAlchemy's philosophy is that SQL databases behave less and less like object collections the more size and performance start to matter, while object collections behave less and less like tables and rows the more abstraction starts to matter."

---

### Post by pmasiar on 2008-04-27
ORM is more to simplify SQL use (especially for newbie; and avoid trivial bugs like SQL injection) than to get DB independence.

Of course ORM will soak some performance, but if it simplifies programming, it is same compromise as using HHL instead of C or ASM, no? Why HHL is good in coding but bad in DB access?

Of course it depends on how clunky ORM is, and after a while all but the most trivial SQL is easier to write in SQL, after you learned SQL, and if you need the performance.

OTOH every web app developer should have one eye on GAE (Google App Engine) DB, because if it will gain the traction, it would be substantial change.

---

### Post by Quikee on 2008-04-27
> **CptPicard said:**
> 
And regarding ORMs, the "switching databases" argument is IMO a little bit of a red herring... SQL is standardized enough, and the whole use case sounds a little dubious to me... "oh, I had this great idea for our system, let's change databases!". 

Well if you have a customer that insists on using a specific database this is really important. Besides it helps if you want to run the whole test suit locally on a clean database - you can just use a in-memory SQLite like database and run them without much configuring and installing the database itself. 

Also SQL might be standardized yes, but not to full extend (not all features are standardized (yet) ), and as with HTML/CSS and web browsers - also here you find "bitches" (for example Oracle with its idiotic empty string == NULL, which causes problems even if you have ORM).

> **CptPicard said:**
> 
The DB is a fairly integrated component -- the central component often of a system. Then there's the "impedance mismatch" between tables and objects... if you've got a greatly optimized relational database, why hide it behind object abstractions that destroy your ability to leverage the db?

Do you need the speed and optimization? Always? IMHO mostly you don't.

Dealing only with objects (especially if you have a central object model and program generically) and let the ORM do the magic is way easier, faster and safer than to use SQL querying and dealing with results "by-hand". 

Still having an ORM doesn't mean you can't use SQL at all - you just use it for things that need to be done faster and optimized.

> **CptPicard said:**
> 
From the Wikipedia page for SQLAlchemy, another ORM... "SQLAlchemy's philosophy is that SQL databases behave less and less like object collections the more size and performance start to matter, while object collections behave less and less like tables and rows the more abstraction starts to matter."

Yes, I agree.

---

### Post by howlingmadhowie on 2008-04-27
personally i'm very suspicious of orm. i know it can save a lot of work, but i prefer to write a collection of stored procedures and think through things in advance. in my experience of seam, using a framework to generate sql queries tends to result in bloated code which obscures what is actually going on. of course that could just be a problem with seam and not with other frameworks, but i can't shake the idea that writing stored procedures is a lot safer than using an abstraction layer such as hibernate (and thus one more layer of programming to go horribly wrong).

---

### Post by LaRoza on 2008-04-27
> **howlingmadhowie said:**
> personally i'm very suspicious of orm. i know it can save a lot of work, but i prefer to write a collection of stored procedures and think through things in advance. in my experience of seam, using a framework to generate sql queries tends to result in bloated code which obscures what is actually going on. of course that could just be a problem with seam and not with other frameworks, but i can't shake the idea that writing stored procedures is a lot safer than using an abstraction layer such as hibernate (and thus one more layer of programming to go horribly wrong).

Read the links, and you'll see that the SQL is not hard to figure out.

---

### Post by howlingmadhowie on 2008-04-28
> **LaRoza said:**
> Read the links, and you'll see that the SQL is not hard to figure out.

i meant stored procedures for *SQL :)

---

### Post by pmasiar on 2008-04-28
> **howlingmadhowie said:**
> personally i'm very suspicious of orm. ... an abstraction layer such as hibernate (and thus one more layer of programming to go horribly wrong).

Of course if you use sucky ORM in sucky language like Java, you get appropriately ugly results. Avoiding that is the whole point using dynamic languages, which can generate functions on the fly by inspecting classes, and can use overloading and other advanced trick which were deemed unworthy by Java designers to be used by 'plain' coders.

---

### Post by MDSmith2 on 2008-05-04
Found something to practice sql with.
I play flightgear alot so i could use sql to log my flights and such.

---

### Post by hasan2000 on 2009-11-18
> **MDSmith2 said:**
> Does anyone know were i could find a good free sql tutorial?

If you like to learn by watching then you can try SQL video tutorials at [http://sqlzerotopro.com](http://sqlzerotopro.com) , [SQL Tutorial]("http://sqlzerotopro.com")

Regards

---

### Post by mbeach on 2009-11-20
> **unutbu said:**
> 
PS. I notice a lot of people use MySQL and my unscientific gut feeling is fewer people use postgresql. Does anyone else feel this way, and/or suspect a reason why?

my gut feeling is that the mysql crowd has an apparent easier to use interface and helper type tools - like utilities to assist with migration from dbs like ms access. I use both depending on mood/requirements. I am tending toward mysql of late for no particular reason. Good question.

[http://ubuntuforums.org/showthread.php?t=877056](http://ubuntuforums.org/showthread.php?t=877056)

---

### Post by greenberry on 2010-07-15
1Keydata.com has a good [SQL Tutorial]("http://www.1keydata.com/sql/sql.html") for beginners.

---

### Post by slavik on 2010-07-15
Zombies come back only once.

---

