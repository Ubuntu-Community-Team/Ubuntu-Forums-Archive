---
title: "Best database / data storage options for C/C++ on linux system"
date: 2011-01-07
forum: Programming Talk
---

### Post by TMagic*04 on 2011-01-07
Hi,

I'm planning to build a simple application, using c/c++ on a ubuntu 10.10 platform. It's essentially just a database, with a CLI interface giving the user options to input new data, or to search based on certain tags associated with the data. 

In the past similar programs I've done would just store the data in a text file in a grepable or easily searchable/extractable fashion, however these dealt with rather small data sizes.

I'm worried that if the data-end of the system gets quite large this will become a slow and inefficient way of managing the data. This leads me to my actual question, can anyone recommend a good database that is to be used locally and is easily interfaceable with c, or recommend another method of managing this data which will allow fast extraction, but still the ability to store data, with tags/keys attached to it for identification purposes?

Thanks for any help

---

### Post by ssam on 2011-01-07
sqlite is the standard tool for this sort of thing.

---

### Post by dwhitney67 on 2011-01-07
Post #2

---

### Post by dwhitney67 on 2011-01-07
Post #3.

In the past, I used the MySQL database, and the MySQL++ API to interface with the database from my C++ programs.

---

### Post by TMagic*04 on 2011-01-07
thanks a lot, and sincere apologies for the multiple posts, my internet went a bit funny, the posting never completed and everytime I dis-connected and reconnected the last commands must've refreshed....

Anyway apologies for it, it wasn't on purpose.

And thanks for the advice

---

### Post by MadCow108 on 2011-01-07
non-exclusiv list of what works good for wide range of applications:

SQL:
MySQL
PostgreSQL
Sqlite3 (designed for being embedded)
...

NoSQL:
CouchDB
MongoDB
Redis
...

you could consider using an database abstraction layer to be independent of the underlying database. E.g. soci (SQL/C++, can do mysql, postgres, oracle, odbc, sqlite3, firebird)
If an abstraction is a good idea depends on your requirements (scalability, complexcity of queries etc.)

---

### Post by WRDN on 2011-01-07
I would recommend the use of sqlite - a sample application of this is Mozilla Firefox. The main reason for the recommendation is that it is lightweight, especially compared to other products such as MySQL.

Further, it is **serverless** - MySQL and PostgreSQL are both Database Management Systems (DBMS) - they run a server, which you log in to and modify data. As the term suggests, sqlite does not have this overhead.

---

### Post by bouncingwilf on 2011-01-07
I would endorse the sqlite option. As has been said, it's small, powerful, fast and server-less (although there are one or two SQL commands unsupported - can't remember which ones offhand) I use it myself in writing GTK+ / C GUI applications and the C API is relatively simple.


Bouncingwilf

---

### Post by drdos2006 on 2011-01-07
Check this out, it may be of interest.

[http://dabodev.com/](http://dabodev.com/)

regards

---

