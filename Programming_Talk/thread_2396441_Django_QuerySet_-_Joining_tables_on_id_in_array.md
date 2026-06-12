---
title: "Django QuerySet - Joining tables on id in array"
date: 2018-07-16
forum: Programming Talk
---

### Post by Crafty Kisses on 2018-07-16
I've been having some difficulty figuring out how to implement the following PostgreSQL query using Django query set notation:

```
SELECT *
FROM table1 
JOIN table2 ON table1.id_column = ANY(ARRAY[table2.array_column]);
```

Any help would be greatly appreciated!

---

