---
title: "Looking for simple database that supports DATEs"
date: 2008-07-18
forum: Programming Talk
---

### Post by cwaldbieser on 2008-07-18
I am looking for a simple database I can use.
I want to import some data in CSV files into it.
I want to do some analysis on the data given some date ranges.

My first thought was to use SQLite / pysqlite, but the database doesn't seem to recognize DATE formats, so my queries don't always end up picking the right rows in a range.

Does anybody have any idea if there is an easy way to deal with this issue, or if there is a different database I should be using?  I have had a little experience with PostgreSQL, but I think a multi-user DB would be overkill for what I want to do.

---

### Post by pmasiar on 2008-07-18
Simple Google search for "SQLite date" returns plenty of info: Seems like dates are possible but format needs careful formatting:
[http://www.sqlite.org/cvstrac/wiki?p=DateAndTimeFunctions](http://www.sqlite.org/cvstrac/wiki?p=DateAndTimeFunctions)
[http://www.sqlite.org/lang_datefunc.html](http://www.sqlite.org/lang_datefunc.html)
[http://www.perturb.org/display/entry/629/](http://www.perturb.org/display/entry/629/)

---

### Post by themusicwave on 2008-07-18
If are using Java,[Apache Derby]("http://db.apache.org/derby/")is a great choice.  It is also known as JavaDB I believe.

It is very simple to use, works on lots of platforms.  It is primarily for Java, but I have heard of people connecting to it with Python.

You didn't say what language you want to use, so it may work for you.

Almost every database supports dates, some of them are just picky on the formatting.  Usually my solution is to write myself a function called String DateToSQL(date) or something like that to convert my internal date variables to whatever format my database wants.  Then you can also do the reverse and make Date SQLToDate(sqlData).

---

