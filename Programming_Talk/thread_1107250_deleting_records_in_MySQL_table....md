---
title: "deleting records in MySQL table..."
date: 2009-03-26
forum: Programming Talk
---

### Post by qmqmqm on 2009-03-26
I have some tables in a database. The fields of each table are like this:
Table 1: id, value
Table 2: table1_id, value

I wish to perform kind of a "clean-up" to the datebase: delete all entries in Table 1 if it is not in table 2.

Does anyone know the syntax to do this?

Thanks,

Tom

---

### Post by kpatz on 2009-03-26
> Table 1: id, value
Table 2: table1_id, value

The standard (ANSI SQL) way of doing it is:
```

delete from table1
  where not exists
    (select * from table2 where table1.id = table2.table1_id);

```

There's a MySQL syntax that works too:

```

DELETE table1
   FROM table1
   LEFT JOIN table2
    on table1.id = table2.table1_id
    where table2.table1_id is null;

```

---

### Post by qmqmqm on 2009-03-26
Thank you kpatz !

---

