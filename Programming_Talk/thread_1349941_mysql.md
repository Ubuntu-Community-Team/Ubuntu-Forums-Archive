---
title: "mysql"
date: 2009-12-08
forum: Programming Talk
---

### Post by djshaw on 2009-12-08
Hey,

So I have a MySQL table that looks like this

```

CREATE TABLE marks
(
    assignment INT NOT NULL,
    submissionNumber INT NOT NULL,
    student CHAR(64) NOT NULL,
    grade INT NOT NULL
)

```

For all rows with the same assignment value, all of the submission numbers are incremented by one.

For instance,
```

mysql> SELECT * FROM marks;
+------------+------------------+---------+-------+
| assignment | submissionNumber | student | grade |
+------------+------------------+---------+-------+
|          1 |                1 | djshaw  |    50 |
|          1 |                2 | djshaw  |    56 |
|          1 |                3 | djshaw  |    60 |
|          1 |                1 | newGuy  |    60 |
+------------+------------------+---------+-------+
4 rows in set (0.00 sec)

```

Now, if I were to insert a new submission for "newGuy" assignment 1, the submission number would be two. I can do this in code easily. The new submission number would be "SELECT MAX( submissionNumber ) + 1 FROM marks WHERE student = "newGuy" AND assignment = 1", however this means that there is too much database contention. I want to be able to insert in one command.

I've tried "INSERT marks( assignment, submissionNumber, student, mark ) SELECT 1, MAX( submissionNumber ) + 1, "newGuy", $(NEW_MARK) FROM marks WHERE student="newGuy" AND assignment = 1". This works. Unfortunately, I can not use this method because I need to get the submissionNumber (I'm doing all of this from PHP, and I can't risk another thread doing an insert on the same table, so I can use "SELECT MAX( submissionNumber ) where student = "newGuy" AND assignment = 1"; this would work if LAST_INSERT_ID() always returned the last insert id even if the last insert id was specified (and if I made the column auto increment)).

Does anyone know how I can auto increment the submissionNumber field over the aggregate of assignment?

Thanks
-djshaw

---

### Post by mike_g on 2009-12-09
> (I'm doing all of this from PHP, and I can't risk another thread doing an insert on the same table,
If you are worried about multiple simultaneous inserts screwing things up, then you could try using MyIASM engine, as it supports concurrency:

[http://dev.mysql.com/doc/refman/5.0/en/concurrent-inserts.html](http://dev.mysql.com/doc/refman/5.0/en/concurrent-inserts.html)

---

