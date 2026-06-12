---
title: "CSV joins using mysql?"
date: 2009-03-24
forum: Programming Talk
---

### Post by pzs on 2009-03-24
I do a lot of work with CSV files.

- Give me all the lines where the third column is x

- Give me all the unique values in column y

- Give me all the rows from file a where column x is one of the values in column y of file b

and so on. I use Python, which works, but after a few hours of this my brain is dribbling out of my ears. Obviously a lot of this is basic relational database calculus. Does anybody know of a mysql or similar approach that will work?

It needs to be really lightweight. What I want is a GUI that allows me to read in a few files and right some 2 line SQL queries. Are there tools on Ubuntu for this?

---

### Post by albandy on 2009-03-24
try squirrel-sql
[http://squirrel-sql.sourceforge.net/](http://squirrel-sql.sourceforge.net/)

---

