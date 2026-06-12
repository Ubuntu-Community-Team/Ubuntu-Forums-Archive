---
title: "will redesigning a schema improve database performance?"
date: 2007-10-06
forum: Programming Talk
---

### Post by DouglasAWh on 2007-10-06
I've got a database schema that does not include tables for relationships.  Will making a relationship table improve performance?  It's really only getting rid of one foreign key, so I'm skeptical.

---

### Post by CptPicard on 2007-10-06
Doesn't adding a relationship table actually add a join, and make performance worse?

---

### Post by DouglasAWh on 2007-10-06
the other table isn't used much, so that's not a problem.  I'm just trying to fix performance on the table that will be losing the column.

---

### Post by pmasiar on 2007-10-07
JOIN is always slower than SELECT from one table only, especially if properly indexed. Of course, without JOIN data are not normalized. So not sure what your design is: you denormalized data and now you want to nrmalize them, and are afraid to lose performance? But again, you do have to maintain your denormalized data, and it is also a drag on performance?

With no real input to base advice on, any advice would be [WAG](http://www.acronymfinder.com/af-query.asp?Acronym=wag)

---

