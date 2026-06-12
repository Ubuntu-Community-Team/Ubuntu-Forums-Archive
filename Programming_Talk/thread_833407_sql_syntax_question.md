---
title: "sql syntax question"
date: 2008-06-18
forum: Programming Talk
---

### Post by lapubell on 2008-06-18
i am trying to count the rows of two tables and get a return set of the totals in one SQL command.  Any idea how to do this?

I could do a SELECT count(*) FROM (Table name here) for both tables, but I don't want to run the sql twice.  Also, I don't want the totals from the tables added together, but two different numbers in one call.  does this make sense?

Thanks to everyone!

---

### Post by leg on 2008-06-18
I suppose you could use sub queries to do this.
```

select
...
(select count(*) from table1) as tb1_count
(select count(*) from table2) as tb2_count
from
...
where
...
```
if you want some other data at the same time you could look at this method.

---

### Post by lapubell on 2008-06-18
thanks dude.  on it. :)

---

### Post by dtmilano on 2008-06-19
You dind't mention which db. If you are using postgresql

> select count(distinct t1.ctid), count(distinct t2.ctid) from t1, t2;

in one query with no subqueries. You may try it and should be much more efficient than the subqueries alternative.

If you have some performance results please share them.

---

### Post by jonathan.gardner04 on 2008-06-19
You could also run a union:

SELECT COUNT(*)
  FROM t1
  WHERE...
UNION
SELECT COUNT(*)
  FROM t2
  WHERE...

---

