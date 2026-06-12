---
title: "What can I use to practice SQL?"
date: 2010-08-29
forum: Programming Talk
---

### Post by Kdar on 2010-08-29
I want to learn SQL. What can I use to practice it?

I heard about Oracle 10g express edition, but it doesn't start for me, for some reason.

---

### Post by CptPicard on 2010-08-29
MySQL, PostgreSQL?

---

### Post by bouncingwilf on 2010-08-29
sqlite3/sqliteman - It's lightweight and in the repos with a simple frontend

---

### Post by James78 on 2010-08-29
You should learn MySQL or SQLite, those are the best ones in my opinion.

---

### Post by CptPicard on 2010-08-29
> **James78 said:**
> You should learn MySQL or SQLite, those are the best ones in my opinion.

Of the "real server" ones, PostgreSQL has always been the more feature-complete and compliant...

---

### Post by Lars Noodén on 2010-08-29
+1 for postgresql or sqllite

---

### Post by James78 on 2010-08-29
> **CptPicard said:**
> Of the "real server" ones, PostgreSQL has always been the more feature-complete and compliant...
I've never used PostgreSQL, however I will take your word for it. +1 for MySQL, PostgreSQL, or SQLite. ;)

---

### Post by memilanuk on 2010-08-29
Something for you to practice generic SQL without the hassle of setting up your own database first...

[http://sqlzoo.net/](http://sqlzoo.net/)

---

### Post by ja660k on 2010-08-29
database is the easy part.
relational modeling is the hard part.

get a database.
think of an idea
design tables.

i remember when i was learning SQL and database's we used a videostore schema. films, genres, members, rentals.
and a few other tables.
Recreate tables and then query it.
ie: how many members rented <movie name> in a month,
which movies are the least popular
which genre is most popular to <member name>

sure, a videostore doesnt really need all this information
but practice makes perfect

---

### Post by Kdar on 2010-08-29
I have LAMP server installed on my computer, with MySQL. But whenever I try to run some SQL code in phpmyadmin (I am guessing that what I have to use? or I am wrong?) it give me errors.

for example I enter this:
```
create table members
{
id number,
first_name varchar2(30),
last_name varchar2(30),
phone varchar2(15)
}
```
I get this:
> #1064 - You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '{ id number, first_name varchar2(30), last_name varchar2(30), phone varchar2' at line 2

----
I will try others which y'all recommended.

---

### Post by memilanuk on 2010-08-29
If you look at the link I provided, there are specific sections on 'CREATE TABLE', etc.  I think you'll find your mistake fairly quickly...

---

### Post by Kdar on 2010-08-29
> **memilanuk said:**
> If you look at the link I provided, there are specific sections on 'CREATE TABLE', etc.  I think you'll find your mistake fairly quickly...

ah ok. I got it. thanks!

I guess the tutorial which I used to learn some basic SQL was wrong. It told to use 'varchar2' and 'numbers', instead of VARCHAR and INT

---

