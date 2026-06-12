---
title: "[SOLVED] SQL- Using AND with OR"
date: 2009-01-03
forum: Programming Talk
---

### Post by s.fox on 2009-01-03
Hi,

I am having a little trouble with some SQL and wondered if somebody had any ideas.  Basically I want the query below to only return cars where the owner ID is 5 and the  the reg and model match some other criteria.

```
SELECT * from cars WHERE ownerID ="5" 
AND carReg LIKE "%ABC123%" 
OR carModel LIKE "%Fiesta%" 

```

At the moment the query seems to ignore my mandatory requirement of the ownerID and returns all records that are like the reg or model.   Would something like a JOIN be what I need or am I totally wrong?

If I have not been clear on what I am trying to acomplish please say and I will try to explain better.

Many thanks for any help,

Ash R

---

### Post by s.fox on 2009-01-03
Hey,  I figured it out :D.   I found a useful site [here]("http://www.w3schools.com/Sql/sql_and_or.asp").  

Thanks anyway

---

