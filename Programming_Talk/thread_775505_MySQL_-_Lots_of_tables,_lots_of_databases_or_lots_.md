---
title: "MySQL - Lots of tables, lots of databases or lots of rows.. ?"
date: 2008-04-30
forum: Programming Talk
---

### Post by wrightee on 2008-04-30
I always wonder this when about to start a new project involving more than a few clients on a project, so I thought I'd ask the opinion of those who might know... 

We're going to have numerous people (up to about 500) storing about 1000-3000 rows of data per month in "a" database.  The data all looks similar in that it could all go merrily into one table - no requirements for different table structures per user; users will continue to pour data in with no opportunity for cleansing older records.

So here's the question - would you go for:

1 database per user, or
1 table per user,
or 1 big table 

.. and why?

Thanks in advance for your opinions!

---

### Post by Zugzwang on 2008-04-30
Normally, you should try to [normalize]("http://en.wikipedia.org/wiki/Database_normalization") you database. This removes a lot of the practical problems in practice. Roughly half of the problems people have with the design of queries are due to unnormalized database design.

Since having such a high number of tables or databases looks like the design isn't normalized, I would suggest using one big table and suitable indices.

---

### Post by pedro_orange on 2008-04-30
Normalizing a database is to stop repeating data.
Running a query against a monolithic table will be slow. And the bigger it gets, the slower it gets.

I would normalize my database structure into a few well structured tables. You can do this using those Entity Relationship Diagrams (I think thats what they're called - Many to One etc)

Seperating the data dependant on who enters it is a bit of a random way to seperate the data. You want to seperate the data by what kind of data it is/what it tells you.

The front end of the database where users enter data can be the same for every record. They don't have to see the back end. Perhaps even just an html page with a link to a php file that inserts the data.

---

### Post by pmasiar on 2008-04-30
What kind of data are that?

Will you need data which are 3 years old, or can you safely archive/delete them?

Around 100K row a month is still reasonable. I would not bother table per user, but you need to normalize tables (remove redundancy). Be careful about creating correct indexes, wrong query (full search) kills performance.

Be careful if different users want different variations of data. If you plan hosting it at Google, GAE DB has Expando class which is flexible Entity-attribute-value storage, but AFAIK no other major database has it (yet :-), they will).

---

