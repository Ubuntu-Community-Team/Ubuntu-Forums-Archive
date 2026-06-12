---
title: "Cant make the table in sql"
date: 2013-02-23
forum: Programming Talk
---

### Post by azi90 on 2013-02-23
I have college assignment to do .. what im suppose to do is create a table in sql. i have ubuntu 12.04 all updated all the sql files and programs installed. What happens is i can succesfully login into sql by mysql -u root -p command. but at the prompt mysql>  when i enter CREATE TABLE xyx and press enter it gives me another little prompt "->" which does nothing at all .. how do i get around this what am i doing wrong

---

### Post by KdotJ on 2013-02-23
You need to actually define your table structure (e.g. the columns and constraints etc). However, there's more to be done first... You should create a database and then select to use it. Your mysql server is capable of maintaining multiple databases at one time.

```

mysql> CREATE SCHEMA MyDatabase;

mysql> USE MyDatabase;
```


Then create your table. Don't forget the ;

---

### Post by azi90 on 2013-02-23
> **KdotJ said:**
> You need to actually define your table structure (e.g. the columns and constraints etc). However, there's more to be done first... You should create a database and then select to use it. Your mysql server is capable of maintaining multiple databases at one time.

```

mysql> CREATE SCHEMA MyDatabase;

mysql> USE MyDatabase;
```
Then create your table. Don't forget the ;
OHHH so i was missing ";" .. done 
now how do i create the table

---

### Post by Lars Noodén on 2013-02-23
Isn't that your assignment then?

First, try to get familiar with the [create table syntax](http://dev.mysql.com/doc/refman/5.1/en/create-table.html).  Then once you're familiar enough to formulate specific questions, look around for examples.

---

