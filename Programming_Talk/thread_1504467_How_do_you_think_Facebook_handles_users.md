---
title: "How do you think Facebook handles users?"
date: 2010-06-08
forum: Programming Talk
---

### Post by jrab227 on 2010-06-08
Hey all. I was recently intrigued as to how Facebook or any other social networking site stores and accesses user data. As far as I'm aware, only nodes would work. But at the same time, accessing nodes is difficult since one has to go through all the users just to find one. Also, a user has friends, and it wouldn't make sense to make a new node of users since you'd end up with a terrible endless loop of users who have users who have users. Any thoughts?

---

### Post by DanielWaterworth on 2010-06-08
Websites invariably store there data in databases. Databases work on binary trees generally, see [http://en.wikipedia.org/wiki/Database_storage_structures](http://en.wikipedia.org/wiki/Database_storage_structures) . For the part where users have friends, google 'relational databases'

---

### Post by jrab227 on 2010-06-08
So Nodes and Strings and Arrays are one category and Databases are another? Do these have names?

---

### Post by DanielWaterworth on 2010-06-08
Basically, for storing data you have, arrays, lists, trees, hash tables. Databases are an abstraction of data structures, you have a schema, that tells the database what to store and the database sets up a set of data structures to store the data that you want. You then run queries over the database to change and read from it.

You know about arrays and lists (you call them nodes), strings are just arrays of characters, generally. There is a reasonable introduction to binary trees here [http://spider.usask.ca/resources/csconcepts/1998_6/bintree/2-1.html](http://spider.usask.ca/resources/csconcepts/1998_6/bintree/2-1.html)

---

### Post by Some Penguin on 2010-06-08
Look up [URL="http://en.wikipedia.org/wiki/Apache_Cassandra"]http://en.wikipedia.org/wiki/Apache_Cassandra
[/URL]

---

### Post by trent.josephsen on 2010-06-08
> **DanielWaterworth said:**
> Websites invariably store there data in databases. Databases work on binary trees generally, see [http://en.wikipedia.org/wiki/Database_storage_structures](http://en.wikipedia.org/wiki/Database_storage_structures).
B-trees, actually, which are not nearly the same thing.  (The B+ tree, which the Wikipedia page links to, is a variation.)  But the point of a database is that the actual data structures used don't matter; you use a query to pull out the data you want ignorant of the actual storage method.  It's the job of the database engine to ensure that the most efficient storage method is used, and the job of the database designer to ensure that the most common operations are reasonably efficient.

MySQL and Sqlite3 are popular free database engines.  *Almost* every database requires working knowledge of SQL (you can get by without it in MS Access, if you can call that a database).  Database design is a complicated topic in its own right.

---

### Post by DanielWaterworth on 2010-06-08
> **trent.josephsen said:**
> B-trees, actually, which are not nearly the same thing.

B-trees isn't short for binary trees, that does make me feel like an idiot. Thanks for pointing that out. A day where you learn about new data-structures is not a day wasted.

---

### Post by Zugzwang on 2010-06-08
Let me give a different explanation which hopefully better fits to the original question asked (for the protocol).

The OP wrote about "nodes". So I assume that he/she thought about a graph model of the "relationships" in Facebook.

So formally, one could describe the friendship structure of Facebook as a graph **<N,E>** where **N** denotes a set of nodes (the users) and **E** is the edge relation and a subset of **N x N**. So far, so good. Typically one whould store this graph in practice as follows:
[LIST]
[*]We have a database table containing a list of all users. This table includes an ID number for every user in the list.
[*]Then, we have a database table with two columns: One for the "source person" and one for the "destination person".
[/LIST]

This is in fact a relational database in which **E** is treated as a relation (which it actually is). Using this database, all necessary operations (such as finding out the neighbours in ** <N,E>** for a user **n** in **N** can how be done via database operations. Read more on relational databases and indexing to find out more.

---

