---
title: "Is this possible in SQL?"
date: 2008-11-23
forum: Programming Talk
---

### Post by cl333r on 2008-11-23
Hi folks,
I have a request (to MySQL 5.0) which looks like this:
```

SELECT * FROM my_table WHERE user_id=17 LIMIT 0,20

```
I also need to tell the user how many rows that comply to "user_id=17" exist at all, but since I use "LIMIT 0,20" it seems impossible.

For now to do that I'm just issuing a second call like:
```

SELECT COUNT(*) FROM my_table WHERE user_id=17

```

but I would like to do this within one call to MySQL to minimize the amount of calls to the database, is this possible?
I tried using code like:
```

SELECT COUNT(*), * FROM my_table WHERE user_id=17 LIMIT 0,20

```
but it seems illegal.
Any hint would be appreciated.

---

### Post by slavik on 2008-11-23
I don't think it is possible to do what you want, since you are asking two separate things.

---

### Post by jflaker on 2008-11-23
Unless you want more specific code, you can try the following:
*create Table TempTableUniqueTimeStamp Like The originalTable (time stamp so others web users dont trample all over the temp table you are trying to create.

*Alter table and add a count field of type INT

Insert into TempTableTimeStamp fields values(Select * from ProductionTable)

Update table TempTableTimeStamp set CountField = (select count(*) from bla bla bla)

PHP out from your TempTableTimeStamp

drop table TempTableTimeStamp



You may notice some overhead, but will likely get the job done....the code idea is very rough, tweaking is likely needed.




> **cl333r said:**
> Hi folks,
I have a request (to MySQL 5.0) which looks like this:
```

SELECT * FROM my_table WHERE user_id=17 LIMIT 0,20

```
I also need to tell the user how many rows that comply to "user_id=17" exist at all, but since I use "LIMIT 0,20" it seems impossible.

For now to do that I'm just issuing a second call like:
```

SELECT COUNT(*) FROM my_table WHERE user_id=17

```

but I would like to do this within one call to MySQL to minimize the amount of calls to the database, is this possible?
I tried using code like:
```

SELECT COUNT(*), * FROM my_table WHERE user_id=17 LIMIT 0,20

```
but it seems illegal.
Any hint would be appreciated.

---

### Post by CptPicard on 2008-11-24
It can be done, but it's contrived, and I am not sure MySQL allows inner queries...

You need to create a join between the select of users and the select count() such that for each row of the left side you get the same single result row of the right side (that is, it's a cross join). Then, you can limit that.

However, I have a feeling that just using two queries is the better option, unless your latency to db is really significant.

---

### Post by pp. on 2008-11-24
I seem to remember that some database systems' APIs include a call which returns the number of rows affected by the last database function. I can't remember, however, if it was for changes only or for queries as well.

---

### Post by cl333r on 2008-11-24
Thanks guys I'll try out your suggestions and eventually report back.

---

### Post by drubin on 2008-11-24
> **CptPicard said:**
> It can be done, but it's contrived, and I am not sure MySQL allows inner queries...

Mysql does support inner queries.

---

