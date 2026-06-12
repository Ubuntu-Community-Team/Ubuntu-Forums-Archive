---
title: "Programming tools alternatives"
date: 2010-10-11
forum: Programming Talk
---

### Post by cap10Ibraim on 2010-10-11
I have two courses now pushing me back to windows 
- database , we will be using MS SQL server 
- VB.NET 
I know a little about mySQL and mono project but are they really reliable ? (especially mono !)

---

### Post by directhex on 2010-10-11
Mono provides a VB.NET compiler, (as a second-class citizen compared to C#), and the System.Data.SqlClient class is provided to access remote MSSQL servers. You can use a different database class if you prefer, i.e. since MSSQL doesn't run on Ubuntu (e.g. Oracle, MySQL, SQLite, Postgres, DB2, Firebird)

---

### Post by juancarlospaco on 2010-10-11
Gambas2 *(?)*

---

### Post by directhex on 2010-10-11
> **juancarlospaco said:**
> Gambas2 *(?)*

The problem, really, is going to be submission of work. Gambas is very VB-like, but it's not gonna help when the OP submits coursework which doesn't just run on the lecturer's computer.

---

### Post by cap10Ibraim on 2010-10-11
thanks guys i'll try mono  mySQL and SQLite 
SQLite has some really impressive sponsors

---

### Post by cap10Ibraim on 2010-10-12
I can't figure out how to draw a VB.net interface using mono 
I installed it from software center , can you show me how ?

---

### Post by lykwydchykyn on 2010-10-12
Despite both being relational databases using SQL, MySQL and MS SQL Server are very different.  Unless you're going to be strictly sticking to ANSI SQL there will be a lot of queries that won't work from one database to the other.

I don't know of any database that runs on Linux that is very MSSQL-like in terms of syntax or structure.  That doesn't mean they aren't reliable (MySQL is the workhorse of the world wide web, after all), but if this is a school thing you don't want an extra complication in the way.

---

### Post by cap10Ibraim on 2010-10-13
I installed XP SP2 on VBox , that was the most convenient solution to focus on the course rather than tweaking my system

---

