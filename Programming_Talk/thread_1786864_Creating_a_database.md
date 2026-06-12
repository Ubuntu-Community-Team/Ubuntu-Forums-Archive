---
title: "Creating a database"
date: 2011-06-20
forum: Programming Talk
---

### Post by Petrolea on 2011-06-20
Hi everyone!

Most of the programming I do is related to storing and reading information. Usually I do it in C, where I store the information in a text file, then read it. But for a bit bigger database that isn't the easiest way.

My question is: Which languages should I use so I can handle reading and writing to some kind of a database?

But don't get me wrong. I don't want something like SQL, I want some language like C, Python or Java that will export my data to a db and then will be able to read it. 

I already tried Common Lisp, which has a great system for handling database, but Lisp itself is what I don't like. 

I'm aware of SQL bindings for C, they are great, but I need a program that will create **its own database** (it can be of any kind as long as it can be read by a program in a SQL kind of way).

**To make this shorter: I'm looking for a programming language or some library that will be able to create a database, read it, and write to it, and edit its entries without too much complication.**

---

### Post by JupiterV2 on 2011-06-20
SQLite3 is my favourite DB library. Single file database with SQL  syntax. It is not a client/server system like MySQL or PostgreSQL. It has a VERY permissive license. Short of that, BerkeleyDB maybe? It's non-relational but gets the job done if you don't need dynamic SQL queries.

---

### Post by PaulM1985 on 2011-06-20
I did a Java/Db course last year where we edited a database using Java.

Using the Java Persistance you are able to create "entity classes" which map to rows in your database tables.  You create a class which has member variables that matching attributes from your table and provide annotations for each of these variables so that Java knows how to map them.

You are then able to use a EntityManager to add/remove rows (instances of your entity class) to your table.

I like this since it allows you to use databases in a more object oriented way.

Paul

EDIT: Here is a link to an example: [http://glassfish.java.net/javaee5/persistence/persistence-example.html](http://glassfish.java.net/javaee5/persistence/persistence-example.html)
EDIT 2: I think it was Derby DB that I was using for this.

---

### Post by BkkBonanza on 2011-06-20
SQLite3 is probably your best bet. Has many language bindings including C and Python. It's fast, easy to use, commonly used by many, many current applications on Linux and Windows. It's a good choice and there are tools to create/alter the db files outside your own application too. Since it's well known it's easy to find support and example code.

---

### Post by Petrolea on 2011-06-20
SQLite was exactly what I was looking for :) Thanks!!

---

