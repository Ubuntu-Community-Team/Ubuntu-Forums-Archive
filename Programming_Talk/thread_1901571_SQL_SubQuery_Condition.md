---
title: "SQL SubQuery Condition"
date: 2011-12-28
forum: Programming Talk
---

### Post by era86 on 2011-12-28
SQL Wizards, I need your help!

I'm trying to put together a rather complex query using some obfuscated crazy framework... details aside, I'd like to do something like the following:

SELECT A.ATT_1, A.ATT_2, (SELECT COUNT(*) FROM TABLE_B) AS B_COUNT, A.ATT_3 FROM TABLE_A A WHERE B_COUNT = '2';

I keep getting an error that B_COUNT doesn't exist. Is there a way I can write conditions on the sub-query returned? Thanks so much in advanced!

:popcorn:

---

### Post by m0zilla on 2011-12-28
I believe you get the error because you have to join the tables in order to use the column from table B in your where clause, I'm not entirely sure though. I think I've had very similar queries in some of my projects, and I've almost always had to do a INNER or LEFT JOIN.

---

### Post by r-senior on 2011-12-29
I believe m0zilla is correct, specifically something like this:

```
select a.att1, a.att2, a.att3, count(*)
from table_a a
inner join table_b b
on a.<primary_key> = b.<foreign_key>
group by a.att1, a.att2, a.att3
having count(*) = 2
```

The <primary_key> and <foreign_key> columns are up to you to designate. It's not clear from your post what these columns are in table_a and table_b.

[http://www.w3schools.com/sql/sql_having.asp](http://www.w3schools.com/sql/sql_having.asp)

---

