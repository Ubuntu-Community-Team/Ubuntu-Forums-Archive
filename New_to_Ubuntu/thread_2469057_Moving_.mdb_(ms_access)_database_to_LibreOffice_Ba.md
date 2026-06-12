---
title: "Moving .mdb (ms access) database to LibreOffice Base"
date: 2021-11-18
forum: New to Ubuntu
---

### Post by mjetrying on 2021-11-18
Looking at options to move a .mdb (ms acccess) database over to LibreOffice Base.

I know it's not straight forward. It's been suggested that I could export the main table as CSV then import that to Base and rebuild the forms, queries and reports.

Just wondering if anyone had done the same and  could comment.

---

### Post by ActionParsnip on 2021-11-18
Can newer MS Office versions save in LibreOffice format now? Is that a thing? I know that Word can save in ODF/ODT etc. Is this a solution?

---

### Post by oldfred on 2021-11-18
Not recent info.

I tried converting several .mdb data bases years ago. Did not go well.
I decided I wanted more flexibilty, but paid a price on learning a variety of new tools. MS Access is a nice integrated database tool. 
I ended up using sqlite database.
I had used sql queries in all my forms & reports, by copying query from query form into report or form. Then using SQL with sqlite was relatively easy.
But I then used DB Browser for SQLlite to test queries.
And python as form & report tool using the SQL queries. But to use python I also had to learn it, and used Geany as a tool to help develop python scripts.
It was a bit of learning, but I consider it worthwhile.
If you want to jump into the deep end not really knowing how to swim, I can post some links & references.

---

### Post by TheFu on 2021-11-18
+1 for not using the GUI program data files for databases.  Go with a different DBMS.  For single user, non-networked, needs, SQLite is fine.  If multiple users will need to update OR the DB is on shared storage and accessed by multiple clients concurrently, then go with a more capable DBMS like postgress or mariaDB.

The great thing about SQLite is how small, light it is. It runs on pretty much anything - every smartphone in the world uses it and many dumbphones as well.  But ... it doesn't perform validation that the datatype put into any field is actually the correct data type. Everything is stored as a string, so date-time entries aren't just the numeric-equivalent, but strings. That means it is actually possible to place bad data into the wrong field.  Just be aware and it should be fine, but I know that SQLite does not support *stored procedures*.  There are techniques to trick SQLite into having stored procedures, but those seem to be hacks.
In my normal DBMS use, we avoided using stored procedures and kept that code outside the DBMS to make any DB swap-able with our program.Our code supported many platforms and many DBMSes - from IMS to Oracle to Postgres to MS-SQL and everything in-between for production use.  We even supported MS-Access for a pre-sales guys - what a pain.   But we didn't support SQLite because it didn't support transactions - which is a big deal for atomic data protection.

Please avoid switching from 1 highly proprietary language (MS-Access) embedded in a tool to some other just-as-proprietary language (OO-base). Learn a language with more than 1 use. As oldfred says - python would be a reasonable choice. There are others.  I love they way Ruby or Perl had plug-ins for different DBMS, but I don't know python's answer. It is probably very good.  But Perl's DBI suite is really amazing for strong intermediate -to- expert perl programmers.  Not so great for beginners, I'm sorry to say. Python is probably best.

My nickle comment.

---

### Post by mjetrying on 2021-11-19
Thank you for the replies. Sounds like my database is simpler perhaps than some of those mentioned. I think if I do go ahead I'll export/import the data as xml and build new forms/queries/reports.

Any of you have any experience of Juno Computers? I'm thinking of getting one of their machines

---

### Post by TheFu on 2021-11-19
If they are really simple, CSV with '|' as the delimiter is probably best.  XML is ugly and hard for humans to deal with compared to lots of other formats - YAML, JSON, but CSV for each table ... if there aren't too many joins is the easiest.  For less than 5000 rows, then you might be able to use a Spreadsheet rather than the DBMS - assuming it won't grow.

---

### Post by Holger_Gehrke on 2021-11-19
@TheFu: You might want to give LO Base another look, because it's not using some half-baked self-written database engine. The database it uses per default is [HSQLDB]("http://hsqldb.org") but it can use any database for which there is a JDBC-driver (yes, that means you need to have Java installed and integrated with LibreOffice, but it also means you can use MySQL / MariaDB or PostgreSQL as a backend for Base).
Sadly, the JDBC-driver for SQLite is kind of minimal and because of that SQLITE can't be used with LO Base.

Holger

---

### Post by TheFu on 2021-11-20
> **Holger_Gehrke said:**
> @TheFu: You might want to give LO Base another look, because it's not using some half-baked self-written database engine. The database it uses per default is [HSQLDB]("http://hsqldb.org") but it can use any database for which there is a JDBC-driver (yes, that means you need to have Java installed and integrated with LibreOffice, but it also means you can use MySQL / MariaDB or PostgreSQL as a backend for Base).
Sadly, the JDBC-driver for SQLite is kind of minimal and because of that SQLITE can't be used with LO Base.

Holger

I didn't know it was using HSQLDB.  I avoid java stuff, much to the heckling of my friends who love Java and make their living coding with it. ;)

---

