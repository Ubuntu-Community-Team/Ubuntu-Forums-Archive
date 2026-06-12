---
title: "how to make a Database under linux"
date: 2006-07-05
forum: Programming Talk
---

### Post by nazakthul on 2006-07-05
the title show in a short way my problem I am new in linux, a rookie or something like that  
I want to make a database project like a CD music collection an adress book and so on but i am tired to use the buggy windows My question is what program can i use to make such programs. I want to be a local database not one on a server like a database created by ms accessI tried BASE from open offic org but that not satisfied me 
I want one or two names of programs i want to forget about Ms bill gates
 and co.

My regards 
Nazakthul

---

### Post by Daverz on 2006-07-05
Are you looking for something for an end user or a programmer?

For an end user, you could try glom or kexi.

For developers, check out dabodev.com.

---

### Post by nazakthul on 2006-07-05
most of it for programming i make programs in java and i want memorize data in a database i don/t want to use oracle or my sql for a few records 
Thanx this information is very usefull for me

---

### Post by johnnymac on 2006-07-05
If you want quick and dirty I use XML quite a bit for small simple databases I create for some of my applications.  It's a great way for keeping settings and saving off information that would require something as big as a SQL Server or MySQL engine

---

### Post by Daverz on 2006-07-05
[QUOTE=nazakthul]most of it for programming i make programs in java and i want memorize data in a database i don/t want to use oracle or my sql for a few records 
Thanx this information is very usefull for me[/QUOTE]

For Java you have a lot of choices.  HSQLDB, a pure Java SQL database engine, is very good.  You might want to combine it with a object-relational mapper like Hibernate.  Combine both of those with Netbeans and nbxdoclet, and it's about as easy as working in Java gets (which means that those will do a lot of the work for you, but eventually you have to do some coding in Java :( ).

---

### Post by nagilum on 2006-07-06
There's also SQLite, it doesn't need a server but is just a library which let you store data in a single file and yet use the SQL syntax. Another possibility is BerkeleyDB which also stores data in a single (or multiple) files but has no sophisticated query method like SQL. Instead everything is stored in a simple key-value format, it's up to the developer to organize his data. BerkeleyDB is yet very powerful and can ensure data integrity with transactions.

BDB Java Edition: [http://www.sleepycat.com/products/bdbje.html](http://www.sleepycat.com/products/bdbje.html) 
SQLite: [http://www.sqlite.org](http://www.sqlite.org) (Java wrappers available)

---

### Post by nazakthul on 2006-07-06
Thanks guys the post are very helpfully

---

