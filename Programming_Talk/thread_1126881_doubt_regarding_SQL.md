---
title: "doubt regarding SQL"
date: 2009-04-15
forum: Programming Talk
---

### Post by 65daysofstatic on 2009-04-15
hi,

I am new to SQL, and I am wondering if there's a way to select the first tuple/row of a table.

65dos.

---

### Post by cabalas on 2009-04-15
This code should select the first row from a table

```
select * from table_name limit 1
```

---

### Post by CptPicard on 2009-04-15
First of all, without an order by clause, SQL does not specify an ordering, so there is no well-defined "first" row. Otherwise, use a "LIMIT 1" at the end of the query.

---

### Post by 65daysofstatic on 2009-04-15
lol sql server doesn't support the clause limit but it helped me to find the clause set rowcount and top.

Thank you.

---

