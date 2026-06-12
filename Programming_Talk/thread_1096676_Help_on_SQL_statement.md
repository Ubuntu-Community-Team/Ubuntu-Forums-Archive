---
title: "Help on SQL statement"
date: 2009-03-15
forum: Programming Talk
---

### Post by dollylamb on 2009-03-15
Hi guys,

In my program, i have 2 table as below:

table1:
productID ____Value1
1_______________2
3_______________2
4_______________1

table2:
productID_____Value2
1_______________1
3_______________3
4_______________2
5_______________1

now, my goal is build a new table which is consist of all columns from table1 & table2 like this:
productID_____Value1______Value2
1_______________2___________1
3_______________2___________3
4_______________1___________2
5___________________________1

i use a query like this:
SELECT table1.productID, Value1, Value2 FROM table1, table2
WHERE table1.productID = table2.productID
GROUP BY table1.productID, Value1, Value2
The sql command works but not produce my expected result :( could someone suggests me what to do in this case?

thanks in advance

---

### Post by asimon on 2009-03-15
How about
```

SELECT * from table1 NATURAL JOIN table2

```

See the [Wikipedia entry on SQL joins](http://en.wikipedia.org/wiki/Join_(SQL)).

---

### Post by dollylamb on 2009-03-15
thanks for your reply asimon, but my db is ms access and it not support natural join type :(

---

### Post by dunkar70 on 2009-03-15
What database are you using? The syntax varies slightly if you use any extensions beyond the ANSI standards. For example, I am not familiar with the "natural join" suggested by Asimon. The ANSI query you are looking for is below. The trick is to make sure you get all of the unique product IDs from both tables and only the values that exist.

> 
SELECT
[INDENT]
p.ProductId,
t1.Value1,
t2.Value2
[/INDENT]
FROM
[INDENT]
(SELECT ProductId FROM Table1 UNION SELECT ProductId FROM Table2) AS p
LEFT JOIN Table1 AS t1 ON p.ProductId = t1.ProductId
LEFT JOIN Table2 AS t2 ON p.ProductId = t2.ProductId
[/INDENT]


UPDATE: I was typing while you replied... MS Access (as of version 2003) is not fully compliant with ANSI standards, so the query above may need some tweaking. You should find a Microsoft Access forum to get the specifics you need.

---

### Post by dollylamb on 2009-03-15
thanks very much dunkar70, your suggestion works great for me. For a real look, my case is extract value from YES/NO column into 2 separate columns depend on it's value. My real table look like this:
tblData
id___________value (boolean YES/NO)
1_____________YES
3_____________NO
3_____________YES
1_____________NO
4_____________YES
4_____________YES
4_____________NO
5_____________NO

the goal is extract & count total YES values & NO values of each ID of tblData & put them into new table. the sql command after i try your suggestion is:

SELECT R.ID, R1.yVal, R2.nVal FROM
((SELECT ID FROM tblData GROUP BY ID) AS R
LEFT JOIN (SELECT ID, COUNT(*) AS yVal FROM tblData WHERE value = True GROUP BY ID) AS R1 ON R.ID = R1.ID)
LEFT JOIN (SELECT ID, COUNT(*) AS nVal FROM tblData WHERE value = False GROUP BY ID) AS R2 ON R.ID = R2.ID

the result set fit my expectation.
Thank you for your help dunkar70.

---

### Post by drubin on 2009-03-15
By your first posts.  value2 value2  table1 table2

This seems like the design of the tables isn't [normalized]("http://en.wikipedia.org/wiki/Normalization") enough. 

You might want to have.

Products
ProductID some other values

Values
ProductID TYPE VALUE
ProductID type value
ProductID type value


This way you can do a.

```
SELECT p.productID, v.value FROM products AS p INNER JOIN values AS v on productID where type=X
```

Hope this helps a little.

---

