---
title: "(My)SQL trouble (select+from+group by+having+count)"
date: 2019-07-14
forum: Programming Talk
---

### Post by s3a on 2019-07-14
Hello, everyone. :)

I'm using MySQL 8.

Here is what I'm trying to do:
"Find ID, first name, last name and number of programs of students who are enrolled in at least two different programs in the Computer Science department."

Here are the queries, along with the ability to run them and see the error.:
[https://www.db-fiddle.com/f/6ttTaf7AW8wGnaZ7kKopcW/0](https://www.db-fiddle.com/f/6ttTaf7AW8wGnaZ7kKopcW/0)

I'll also post the error here, just in case.:
Query Error: Error: ER_WRONG_FIELD_WITH_GROUP: Expression #2 of SELECT list is not in GROUP BY clause and contains nonaggregated column 'test.Student.FirstName' which is not functionally dependent on columns in GROUP BY clause; this is incompatible with sql_mode=only_full_group_by

I'm very confused about why the part of the right is not working. The part on the right is as follows.:
SELECT Student.STID, FirstName, LastName, count(Program.PName)
FROM Belong, Student, Program
GROUP BY Student.STID
Having count(Program.PName)>1;

Could someone please help me figure that out? I feel like if I see examples of proper syntax, I'll begin to understand these scenarios.

Any input would be greatly appreciated!

---

### Post by SeijiSensei on 2019-07-15
You have to include all the static variables in the GROUP BY statement, so
```
GROUP BY Student.STID,FirstName,Lastname
```

I use PostgreSQL which might have a different syntax, but I'd handle the last part of the query by using a subquery:

```

SELECT * FROM
(SELECT Student.STID, FirstName, LastName, count(Program.PName) AS NProgs
FROM Belong, Student, Program
GROUP BY Student.STID,FirstName,LastName) AS foo
where NProgs>1;

```
I don't know whether MySQL works the same way.

---

### Post by SeijiSensei on 2019-07-19
Did that help? Is your problem solved? Please don't walk away from threads you start.

---

