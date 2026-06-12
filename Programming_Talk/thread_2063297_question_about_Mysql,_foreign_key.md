---
title: "question about Mysql, foreign key"
date: 2012-09-26
forum: Programming Talk
---

### Post by sid0972 on 2012-09-26
hey

i have 2 databases, say db1 and db2

db1 contains a table with unique id, db2 contains a table with some info
suppose i have to extract data from db2, and i have to group it according to unique id from db1, would that be very slow if kept referencing a separate database all the time? 

if this is gonna have an impact, how big will it be?

and any other solution to write a query apart from creating table in single table itself?

thanks

---

### Post by akvino on 2012-09-26
> **sid0972 said:**
> hey

i have 2 databases, say db1 and db2

db1 contains a table with unique id, db2 contains a table with some info
suppose i have to extract data from db2, and i have to group it according to unique id from db1, would that be very slow if kept referencing a separate database all the time? 

if this is gonna have an impact, how big will it be?

and any other solution to write a query apart from creating table in single table itself?

thanks

That is what relational databases do. For the best performance within the database, make sure to use integer type keys. 

Otherwise you can do it programmatically in your app, but I am not sure that will be faster. 

Pending on what you need this to do, it is possible to load the info from the database into some sort of data structure (many many many variables and options need to be considered here), and then utilize data structure to read from.

---

### Post by SeijiSensei on 2012-09-26
If you can consolidate the two related tables into a single database that would be the easiest and most efficient solution.  Suppose you have two tables, one called "people" with each person's information and a primary key, and a second called "memberships" with ordered pairs of person keys and group memberships.  Then you can run a query like

```
SELECT * FROM memberships LEFT JOIN people USING (person_key) WHERE group='soloists'
```

and get all the records for people who belong to the soloists group. The "USING" construct works in PostgreSQL; I don't use MySQL but I'm sure it has an equivalent construct.

---

### Post by donsy on 2012-09-26
To enforce referential-integrity constraints both the parent and the child tables must both use the InnoDB engine.

---

### Post by sid0972 on 2012-09-27
thank you all
i figured its databasename.tablename
not sure about innodb though

---

