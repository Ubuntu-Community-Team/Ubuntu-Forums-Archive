---
title: "Open Source Database"
date: 2013-05-07
forum: New to Ubuntu
---

### Post by wolfabc999 on 2013-05-07
What is a good open source database software?

---

### Post by slickymaster on 2013-05-07
Hi, wolfabc999. Welcome to the forum.

Two words, [MySQL]("http://www.mysql.com/") and [PostgreSQL]("http://www.postgresql.org/").
Despite their different histories, engines, and tools, no clear differentiation distinguishes either PostgreSQL or MySQL for all uses.
Many favor PostgreSQL because it is so reliable and it is assumed to be a more densely featured database system often described as an open-source version of Oracle. 
MySQL on the other hand is more flexible, faster and has more options for being tailored for different workloads, but is the less full-featured of the two.

---

### Post by SeijiSensei on 2013-05-07
I have been using PostgreSQL for over a decade now and would never consider switching to MySQL.  Postgres is designed to compete with Oracle and MS-SQL in the "enterprise" market, but it is no harder to manage than MySQL.  (In fact in areas like user management and access control I find PostgreSQL much easier to manage than MySQL.)  PostgreSQL also adheres firmly to ISO standards for SQL, while MySQL has some non-portable features.  I also don't trust Oracle, now the owner of MySQL.  I prefer to use a product built entirely by open-source coders.  There is an open fork of MySQL called MariaDB, but why bother dealing with all that when PostgreSQL is free, powerful, and well-supported?

I've also never really seen the speed question arise in production.  I've written quite a number of websites with PostgreSQL as the backend and never thought it was slow.  Performance depends a lot more on database design and, especially, proper indexing.  A poorly indexed database is going to be slow on any platform.  A well-designed database will run just fine on PostgreSQL.

---

### Post by Lars Noodén on 2013-05-07
It depends on what you want to use the database for.  For larger, more complex activities MySQL (or its replacement MariaDB) or Postgresql will do fine.  For smaller tasks Sqllite or,  if you are working with just key pairs, even BerkelyDB.  

There are also MongoDB, CouchDB, GT.M and many others for other tasks.  It's worth reading up on each of them a little.

What do you plan to do with the database?

---

### Post by wolfabc999 on 2013-05-08
I have a large supply of books and I want to create an access catalog.

---

### Post by rewyllys on 2013-05-08
> **wolfabc999 said:**
> I have a large supply of books and I want to create an access catalog.
For buildling a database of your books, I'd recommend your taking a look at the software available from [Readerware.com]("http://www.readerware.com/index.php").

Its chief potential virtue for you is that it's a sophisticated database-management system that already incorporates features whose usefulness you could easily overlook in designing your own book database system. Furthermore, it lets you enter data by scanning barcodes or keyboarding in ISBNs, which leads to an online search of sources that you have selected, e.g., the Library of Congress, and/or Amazon.com, and/or Barnes & Noble, and/or foreign national libraries.  Adding books to your database this way is FAR easier than keyboarding in all the data you want from a book in your collection.

It's not free but it's inexpensive, and there are versions not only for  Linux but also for Android, iPhone, iPad, Mac OS-X, and Windows.  I've  used it, and found it quite capable.  Readerware offers similar  database-management systems for music and for videos.

---

### Post by Archit88 on 2013-05-09
go with mysql

---

### Post by iamkuriouspurpleoranj on 2013-05-09
MariaDB is the brainchild of the man who originally developed and sold MySQL to Sun, who were themselves bought by Oracle from some rough-looking men with foreign accents in a dodgy part of town, on a dark night in winter, many years ago. They were smoking, wore leather jackets and hadn't shaved and it was raining heavily, etc. etc. 

MariaDB is getting more and more use in Linux distributions and I believe it will be the default MySQL (with which it is 97%-98% compatible) in Fedora, Gentoo and openSUSE and is already the default in Mageia.

Not sure if there are compatibility issues involved in migrating a site developed with a MariaDB database to a hosted MySQL db. Perhaps someone else here who knows more about this can say.

You might also want to check out their licenses. Open source != GPL.

---

### Post by iamkuriouspurpleoranj on 2013-05-09
Hold on, hold on. If it's just for something like Access, you'll get a lot out of LibreOffice Base.

---

### Post by slickymaster on 2013-05-09
> **wolfabc999 said:**
> I have a large supply of books and I want to create an access catalog.

LibreOffice Base or OpenOffice Base would be your answer but I would not recommend them for projects needing a DB of 2 GB or more. I would rather use a more proven DB engine like MySQL, Postgresql or MariaDB and then eventually use either LibreOffice Base or OpenOffice Base as a GUI front-end.

Theoretically it's possible to increase both LibreOffice Base or OpenOffice Base size limit of the .data file from 2GB to 8GB, by setting the **hsqldb.cache_file_scale** property, which by default is 1 (equivalent to a 2 GB .data file size) to 8, but personally I've never work with these applications so I cannot ensure you how reliable is that. More about this possibility [here]("http://hsqldb.sourceforge.net/doc/guide/ch04.html").

---

### Post by wolfabc999 on 2013-05-10
Thanks Guys.  I'm still looking.

---

### Post by oldfred on 2013-05-10
I have not used either of these. But they do not use a SQL data base.
Best choice may depend on size of database you need.

 Collections - music, books, etc: both in repositories
Tellico - qt4 & python, xml for data
[http://tellico-project.org/](http://tellico-project.org/)
Gcstar - perl & gtk, xml for data
[http://www.gcstar.org/](http://www.gcstar.org/)

---

### Post by vipin4u on 2013-08-14
PostgreSQL for sure. It is the most advanced open source database system having a lot of functionality which are in par with proprietary systems. Also there is an extension postGIS which enables advanced GIS features using postgres.

-------------------------------
[adobe flex, postgreSQL and dojo tutorials  ]("http://technobytz.com")

---

### Post by ian-weisser on 2013-08-14
For very small (20k records, single index, nonrelational) databases, like my list of weather stations, good old BerkleyDB or gdbm works just fine. Robust, safe, small, fast.

---

