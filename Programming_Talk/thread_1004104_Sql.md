---
title: "Sql"
date: 2008-12-06
forum: Programming Talk
---

### Post by cyclobs on 2008-12-06
hey guys.

i'm doing a school project on a swimming carnival and i need to make certificates of the age champion of each age and gender. but the problem i'm having is that i can't make SQL show only the highest of each age and gender instead it shows everyone in each age and gender... if you understand that.

so anyone know how i could make SQL only show the highest point scorer of each age and gender. need anymore information just ask.

---

### Post by slavik on 2008-12-06
say you have the following fields in the table:
-name
-age
-gender
-score

what you can do is the following:
select *,max(score) as a from table where gender='male' and score=a;

I think the above would work ... I haven't done much SQL. I think the following would be better.
select name,gender,age,max(score) from table where gender='female' group by gender

and such ...

---

### Post by cyclobs on 2008-12-06
This is my current coding for the query

```

SELECT TblEntries.ID, [firstname] & " " & [lastname] AS Name, Sum(tblResults.Points) AS Points, TblEntries.age, TblEntries.gender, TblEntries.house
FROM TblEntries INNER JOIN tblResults ON TblEntries.ID = tblResults.StudientID
GROUP BY TblEntries.ID, [firstname] & " " & [lastname], TblEntries.age, TblEntries.gender, TblEntries.house
ORDER BY Sum(tblResults.Points) DESC , TblEntries.age, TblEntries.gender;

```

---

### Post by slavik on 2008-12-07
have you thought of having separate SQL for each category?

---

### Post by cyclobs on 2008-12-07
> **slavik said:**
> have you thought of having separate SQL for each category?
what do you mean?

---

### Post by drubin on 2008-12-07
> **slavik said:**
> 

what you can do is the following:
select *,max(score) as a from table where gender='male' and score=a;


As far as I know you need a group by with a aggregate functions, like max,min, count, sum...

---

### Post by pp. on 2008-12-07
I think you need two queries. The inner one does an aggregate function of an aggregate function, i.e. max(sum(scores)) by age and gender. The outer one selects only those where sum(scores) equals inner.max(sum(scores)) for an individual's age and gender.

---

### Post by unutbu on 2008-12-07
Maybe something like this would work:

```
SELECT s3.ID,s3.age,s3.gender,s3.house,s4.Points 
FROM TblEntries AS s3
JOIN tblResults AS s4 ON s3.ID=s4.StudentID
JOIN (SELECT s2.age AS age, s2.gender AS gender, MAX(s1.Points) AS Points 
      FROM tblResults s1, TblEntries s2 
      WHERE s1.StudentID=s2.ID 
      GROUP BY s2.age,s2.gender) AS s5 ON s3.age=s5.age AND s3.gender=s5.gender AND s4.Points=s5.Points;


```
For info on:
[list]
[*]the syntax: [http://dev.mysql.com/doc/refman/5.0/en/twin-pool.html](http://dev.mysql.com/doc/refman/5.0/en/twin-pool.html)

[*]the joins: [http://www.devshed.com/c/a/MySQL/MySQL-Table-Joins/](http://www.devshed.com/c/a/MySQL/MySQL-Table-Joins/)

[*]finding group-wise maximums: [http://dev.mysql.com/doc/refman/5.0/en/example-maximum-column-group-row.html](http://dev.mysql.com/doc/refman/5.0/en/example-maximum-column-group-row.html)
[/list]

---

