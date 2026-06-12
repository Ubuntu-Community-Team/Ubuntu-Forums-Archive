---
title: "how to connect a c programme to database ??"
date: 2011-02-24
forum: Programming Talk
---

### Post by Praveen30 on 2011-02-24
I have installed oracle 10g express edition. i want to know how to connect  a c programme to the oracle database...?? any tutorial or any sites....

---

### Post by nickleboyblue on 2011-02-24
Hopefully this is what you want:
[http://download.oracle.com/docs/cd/B19306_01/appdev.102/b14251/toc.htm]("http://download.oracle.com/docs/cd/B19306_01/appdev.102/b14251/toc.htm")

It's a guide for application programmers, and I'm pretty sure it will explain all you need to know.

Though, I must say, if you want a good sql server without the licensing issues, just use Postgresql.  It's in the repositories, as are all of the api's that people generally care about, like c, c++, and python.

---

### Post by Praveen30 on 2011-02-24
> **nickleboyblue said:**
> Hopefully this is what you want:
[http://download.oracle.com/docs/cd/B19306_01/appdev.102/b14251/toc.htm](http://download.oracle.com/docs/cd/B19306_01/appdev.102/b14251/toc.htm)

It's a guide for application programmers, and I'm pretty sure it will explain all you need to know.

Though, I must say, if you want a good sql server without the licensing issues, just use Postgresql.  It's in the repositories, as are all of the api's that people generally care about, like c, c++, and python.

hey thanks for your reply..can you tell me something more about postgresql and is it better to use this than oracle database???

---

### Post by nickleboyblue on 2011-02-24
Installing Postgresql:
[https://help.ubuntu.com/community/PostgreSQL]("https://help.ubuntu.com/community/PostgreSQL")

The c api:
[http://www.postgresql.org/docs/8.2/static/libpq.html]("http://www.postgresql.org/docs/8.2/static/libpq.html")

Make sure to install libpq using synaptic if you want to use the c api, and libpqxx if you want to connect to the database from a c++ application.

Postgresql is not commercial, but it is high quality and is used a lot for dynamic web pages, database-backed applications, etc.  It also has a server that you can set up on one computer that can be accessed from other computers.  This setup would allow you to create database clients on computers that don't have the database and have a dedicated server to host your database.  The best part is that you can use it without paying licensing fees for any reason, commercial or private.

---

### Post by SeijiSensei on 2011-02-24
PostgreSQL also has ODBC drivers so it can interact with Windows software like Access and Excel.  It is the only database I've ever used except when installing applications that demand MySQL.  I once had to interact with an Oracle database using PHP (both server and client were running on Linux).  That was one of the hardest DB applications I've ever written, even with PHP's native Oracle hooks, because Oracle (at the time, at least) required a lot of obscure configuration settings on the clients.

Unless you have a commercial reason to use Oracle, I'd strongly endorse nickelboyblue's suggestion of using PostgreSQL instead.

---

