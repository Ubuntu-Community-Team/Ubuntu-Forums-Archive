---
title: "'best' sql for python?"
date: 2008-12-04
forum: Programming Talk
---

### Post by jmauster on 2008-12-04
I've just installed Ubuntu and I have a small project I am going to be working on using Python. 

I'm new to both Ubuntu and Python, but I have experience developing in C# and SQl 2005. 

I was wondering what would be the best sort of SQL database to get running. From what I understand MySQL is easy but with limits, and SQL lite and PostGre are better but more complicated.  Frankly, I'm not really afraid of complicated, but I want to know what better means. 

How should I evaluate which to use? I know I'm going to have a large database (+/-700mb) with only a few tables. 

Any imput would be super appreciated.

---

### Post by stevescripts on 2008-12-05
I would recommend starting with SQLite - it is certainly no more complicated than MySQL, and you already have it installed.  Python appears to have nice tools for using SQLite.

The size of the db you reference will not be a problem.

Steve

---

### Post by kripkenstein on 2008-12-05
SQLite is by far easier to use, in particular since it comes with Python (as of 2.5 or so). Not that MySQL/PostgreSQL are hard, but SQLite is the easiest to get started with.

Quality-wise, SQLite is not suitable for large projects. For example, only one thread can access the database, and data types are not enforced (you can put a string in an INT field in SQLite...). But for simple stuff it should be fine.

I don't have experience myself with 700MB SQLite tables, but I believe it should be able to handle that.

You might consider using an ORM (object relational mapping) if that is applicable for your project, like Storm or SQLAlchemy. Aside from the object-relational benefits, they also wrap around a lot of database-specific things, so you can switch databases later on more easily.

---

### Post by snova on 2008-12-05
Another vote for SQLite. No server to set up! So much simpler... Although I don't use SQL often.

I asked, and SQLite should have no problems with large database files. I hear that concurrency is a weakness, though.

---

### Post by Luggy on 2008-12-05
The right database to use depends on what your application is, not what language you use.

If you are making a small application I would recommend SQLite as it will get the job done without making things too complicated.

---

### Post by The Cog on 2008-12-07
Aother vote for sqlite as a starter database. 

I also recommend you install the SQLite Manager add-on into Firefox. This givees you a nice GUI to see the table contents which is very useful while debugging.

What SQLite driver do people here recommend? I currently use apsw but would be interested in opinions.

---

