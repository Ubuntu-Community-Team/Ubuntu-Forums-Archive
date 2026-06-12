---
title: "Parsing and comparing very large data sets"
date: 2008-12-09
forum: Programming Talk
---

### Post by Tim Sharitt on 2008-12-09
First of all, I'm not exactly sure of what I'm looking for (which may be my biggest problem).
In my current project I need to be able to be able compare data from different different customer orders and find similarities in order to make recommendations on other products. The problem is that the customer data is spread across several text files which add up to several gigabytes. Loading all that data into memory is out of the question, but I don't really know how to handle it while still being able to use it.
I haven't settled on a language yet. I like lispy languages for this kind of work, mainly because I find them easier to work with. 
Any help or suggestions (even knowing what to google would help a lot) would be greatly appreciated.

---

### Post by geirha on 2008-12-09
There's a reason databases got invented. You'll want to get that data into a database.

---

### Post by iponeverything on 2008-12-09
> **geirha said:**
> There's a reason databases got invented. You'll want to get that data into a database.

Indeed. If your going to be doing it on the fly and you don't want your customers falling asleep while waiting for the recommendations -- this is the only way to go.

---

### Post by Tim Sharitt on 2008-12-09
I won't actually be implementing the system, and databases aren't my specialty. All I need is something to try the different sorting algorithms. Any suggestions on a database system to use on my machine which doesn't include a lot of over head? Speed really isn't a factor for me.

---

### Post by iponeverything on 2008-12-09
MYSql or PostgreSQL -- For me MYSql was easier to learn. For implementing and testing simple algorithms, it should not take you too long to get up to speed putting something together with Apache/MYSql/PHP .

Starting from 0 experience with MYSql and PHP - it took me about a week working on it 4-5 hours a day, to throw something together that would analyse squid logs.

---

### Post by thk on 2008-12-09
PostgreSQL definitely. Take a look at R ([http://www.r-project.org](http://www.r-project.org)) a algol-lispy data mining language. There are add-on packages for sending queries to PostgreSQL and retrieving the results as a table that can be easily analyzed. Python would be the obvious alternative.

---

### Post by pmasiar on 2008-12-09
Databases are fine for transactions processing, but large data analysis is not what DB were designed to: if you dump your data into a database, and then want to read big chunk of it, **sequential** reading out of DB would be **slower** than parsing the text files. Although couple gigs is not **that much** data, doing statistics in SQL is pain, lot of pain, and unnecessary pain.

R is the way to make stat analysis, and (because R sucks in scripting) Python has RPy bindings.

[http://www.r-project.org/](http://www.r-project.org/)

Parsing huge text files effectively can be done  in Python using generators : [http://www.dabeaz.com/generators/](http://www.dabeaz.com/generators/)

If not, you need to look into [http://en.wikipedia.org/wiki/Data_warehouse](http://en.wikipedia.org/wiki/Data_warehouse) : not [http://en.wikipedia.org/wiki/OLTP](http://en.wikipedia.org/wiki/OLTP) but [http://en.wikipedia.org/wiki/Olap](http://en.wikipedia.org/wiki/Olap)  - and try to avoid writing statistics in SQL if you can avoid it, it is hard to do it right (and takes forever on big data sets to test it).

---

### Post by moberry on 2008-12-09
SQLite would be a good option too, would store the DB in a flat file instead of a client/server model. A couple 10 line python scripts would be all you need to get the data from the text file into the db all pretty.

---

### Post by Tim Sharitt on 2008-12-09
Thanks for the pointers. Now maybe I don't have to beg the programmers to write something for me.:)

---

