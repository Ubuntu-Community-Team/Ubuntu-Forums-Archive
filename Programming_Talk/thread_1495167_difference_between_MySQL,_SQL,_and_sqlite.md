---
title: "difference between MySQL, SQL, and sqlite"
date: 2010-05-27
forum: Programming Talk
---

### Post by cybo on 2010-05-27
i started to learn web programming (brand new to it). after a lengthy research on what language to use i decided to go with ruby and ruby on rails. rails can use almost any database. since i never used databases before, i was wondering what is the difference between MySQL, SQL and sqlite?

i would appreciate any help.

thanks

---

### Post by nmccrina on 2010-05-27
MySQL and sqlite are two examples of database programs that create and manage databases. SQL is a language used to interact with those and other database programs. As I understand it there isn't really a "standard" version of SQL, though the basic features might be the same among all database programs. The whole database thing confused me for the longest time, too (and I'm still frantically learning :P ).

If you want to learn more, MySQL has excellent documentation available at [http://dev.mysql.com/doc/refman/5.1/en/index.html]("http://dev.mysql.com/doc/refman/5.1/en/index.html")

Ubuntu also makes it really easy to set up, just install the mysql-server package and everything is ready to go!

---

### Post by simeon87 on 2010-05-27
SQL is the query language, MySQL is a popular implementation of accessing a database using that query language and so is sqlite but that's a 'lite' version which is commonly used to embed in applications. MySQL is mainly used for managing data of websites.

---

### Post by slavik on 2010-05-28
> **nmccrina said:**
> MySQL and sqlite are two examples of database programs that create and manage databases. SQL is a language used to interact with those and other database programs. As I understand it there isn't really a "standard" version of SQL, though the basic features might be the same among all database programs. The whole database thing confused me for the longest time, too (and I'm still frantically learning :P ).

If you want to learn more, MySQL has excellent documentation available at [http://dev.mysql.com/doc/refman/5.1/en/index.html]("http://dev.mysql.com/doc/refman/5.1/en/index.html")

Ubuntu also makes it really easy to set up, just install the mysql-server package and everything is ready to go!
there are dialects some of which are ansi/iso standard.

---

### Post by iMisspell on 2010-05-28
Another one you might look into is, PostgreSQL [http://www.postgresql.org/](http://www.postgresql.org/)

---

