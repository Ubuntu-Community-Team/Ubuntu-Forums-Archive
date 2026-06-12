---
title: "SQL to select unique record based on a single field"
date: 2009-05-12
forum: Programming Talk
---

### Post by fokuslee on 2009-05-12
I want to select unique record based on one single field, meaning even if other fields are complete different i still consider them the same, and then display each unique record w/ all the attributes  
Im doing this in access 
Maybe below is more clear  

Select CustID, [Date], PartNo, Qty
From Orders
Where CustID IN (Select CustID From Orders Group By CustID Having Count(*) >
1)

but i just want to see one record from each group by custid.  
ie 
CustID Date PartNo Qty
122    9/11 block  5
122    6/22 wood   4
122    5/30 wine   6

i just want the query to return 
122  9/11  block  5  (or any 1 row for that matter) 
thats it

is this possible i am having a really hard time
thanks:confused:

---

### Post by unutbu on 2009-05-12
```
Select CustID, [Date], PartNo, Qty
From Orders
**GROUP BY CustID**;
```

For more info, see [http://dev.mysql.com/doc/refman/5.0/en/group-by-modifiers.html](http://dev.mysql.com/doc/refman/5.0/en/group-by-modifiers.html)

---

### Post by fokuslee on 2009-05-14
SELECT tblLog.WO, tblLog.MapType, tblLog.MB, tblLog.Count, tblLog.MapType
FROM tblLog
GROUP BY tblLog.MapType;

you tried to execute a query that does not inlcude 'WO' as part of an aggregate function 
i get this error when trying to excecute this query

---

### Post by s.fox on 2009-05-15
Hi,

Have you tried something like:


SELECT DISTINCT 
CustID, [Date], PartNo, Qty
 FROM Orders

Hope it helps,

-Ash R

---

### Post by bloeper on 2009-05-15
You could also add a LIMIT 1 expression.. So it doesn't look for any other results...

---

### Post by mike_g on 2009-05-15
Queries with a GROUP BY clause can only pull columns which are either the result of an aggregate function aggregate (IE: COUNT, AVG, etc) or the group by field. I think you might need a sub query here.

---

