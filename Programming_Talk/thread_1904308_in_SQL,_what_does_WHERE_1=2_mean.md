---
title: "in SQL, what does WHERE 1=2 mean?"
date: 2012-01-04
forum: Programming Talk
---

### Post by anon0 on 2012-01-04
SELECT *
INTO my_new_table
FROM my_old_table
WHERE 1=2

I think this copies the old table to the new one. It looks like 1 means the new table and 2 means the old table, but what is the format of this syntax, how does 1 get assigned the meaning of my_new_table?

---

### Post by squenson on 2012-01-04
The WHERE clause filters the records and only considers those for which the WHERE clause is true. As 1=2 is always false, no records are copied. The usual syntax is WHERE table1.fieldx = table2.fieldy.

---

### Post by CoffeeRain on 2012-01-04
Yes. With the statement-- ```
SELECT password FROM table1 WHERE user='myusername'
```The password of the user 'myusername' is returned. Password could be changed to '*' which returns all.:)

---

### Post by anon0 on 2012-01-05
> **squenson said:**
> The WHERE clause filters the records and only considers those for which the WHERE clause is true. As 1=2 is always false, no records are copied. The usual syntax is WHERE table1.fieldx = table2.fieldy.

Thanks. I didn't read the information carefully, it actually stated "copy the structure of the table without copying data. ...This code copies the structure of table my_old_table and creates a new table called my_new_table with identical structure."

---

