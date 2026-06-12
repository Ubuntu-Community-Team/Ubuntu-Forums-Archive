---
title: "SQL Current Time"
date: 2007-09-26
forum: Programming Talk
---

### Post by SNYP40A1 on 2007-09-26
I have a SQL script that pulls data including a column that has a timestamp.  I want to only show timestamps from the last day.  How do I do that?  I tried using SYSTIMESTAMP (using Oracle 9i), but that did not work.

---

### Post by Martin Witte on 2007-09-26
suppose your column is called timestamp and your table is called timestampeddata you could go for 'select * from timestampeddata where trunc(timestamp) = trunc(sysdate)'

---

### Post by CptPicard on 2007-09-26
In PostgreSQL I use ... where now()-timestamp < '1 day'. You might want to look into how Oracle expresses time intervals and what the corresponding function to now() is :)

---

### Post by SNYP40A1 on 2007-09-26
> **Martin Witte said:**
> suppose your column is called timestamp and your table is called timestampeddata you could go for 'select * from timestampeddata where trunc(timestamp) = trunc(sysdate)'

Yup, this works perfectly:
trunc(sysdate) < trunc(ts.end_date)+1

Thanks!

---

