---
title: "Create function in an SQL query..."
date: 2007-12-16
forum: Programming Talk
---

### Post by Enissay on 2007-12-16
Hello,
I'm trying to create a function which take a string, do some tests (if...ifelse...else) and return another string....
Goggling, i found some examples, but when i try them i got error 1064:
> CREATE FUNCTION test (s CHAR(50)) RETURNS CHAR(20)
DEFINE temp CHAR(50)
IF (s LIKE '%Bus%')
THEN LET temp = 'Bus';
ELSE IF (s LIKE '%Car%')
THEN LET temp = 'Car';
ELSE
THEN LET temp = 'Plane';
RETURN temp;
END FUNCTION;
And my query is:
> SELECT name, suname, test(trans) AS transport FROM mytable;
Hope someone can help me... :KS

---

