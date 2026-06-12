---
title: "PHP echo mysql_real_escape_string($sql2);  causes a mysql to fail"
date: 2011-01-30
forum: Programming Talk
---

### Post by sdowney717 on 2011-01-30
> SELECT COUNT(*) AS numrows FROM bookdata where MATCH (titles, author, callnumberpre, callnumber, catalogcard, generalnote, summary) AGAINST (\' +home\' IN BOOLEAN MODE)

returns this from mysql

> You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '\' +home\' IN BOOLEAN MODE)' at line 1

I was looking into safe queries, but get errors, any ideas why?
you cant use the function
mysql_real_escape_string() 
easily?

---

### Post by Some Penguin on 2011-01-30
You need to escape passed-in string literals.  You don't want to escape such things as the + in a boolean query, because that + is valuable syntax.

---

### Post by sdowney717 on 2011-01-30
ok, I was hoping to just escape the whole query.
So run that function on the input from the user, then assemble the query?

---

