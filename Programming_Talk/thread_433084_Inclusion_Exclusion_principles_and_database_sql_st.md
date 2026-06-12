---
title: "Inclusion Exclusion principles and database sql statements"
date: 2007-05-04
forum: Programming Talk
---

### Post by theorem_hunter on 2007-05-04
i just need something cleared up here...

i am studying for a discrete maths test, inclusion-exclusion principles is on of the topics being covered, and i was wondering if that is the same principle for SQL statements.

inclusion-exclusion - here is 1 part of a question:

In a class of 200 students 75 take maths, 70 take stats & 75 take zoology. 

35 take maths & zoology
20 take stats & zoology
40 take maths & stats

15 take all 3 subjects

so this becomes...

|U| = 200

|M| = 75
|S| = 70
|Z| = 75

|M&#8745;Z| = 35
|S&#8745;Z| = 20
|M&#8745;S| = 40

|M&#8745;S&#8745;Z| = 15

Q. How many take at least 1 of the 3 subjects?

A. 
|M&#8746;S&#8746;Z| = |M| + |S| + |Z| - |M&#8745;S| - |M&#8745;Z| - |S&#8745;Z| + |M&#8745;S&#8745;Z|
             = 75 + 70 + 75 - 40 - 35 - 20 + 15
             = 140
140 students take at least 1 of the 3 subjects

sql - this is not a working sql statement... im just trying to show/understand the concept. 

my question...
could a sql statement for the above maths statement look like this? or what would the sql statement look like?

select *
from U
where ((M + S + Z) - ((M+S)-(M+Z)-(S+Z)) + (M+S+Z) <= U)

do sql select-from-where statements use inclusion exclusion principles to get their answers? thanks

---

### Post by ola on 2007-05-04
Hi! 

You could certainly get the same result using the were clause only, but I think you might want to look into SQL Joins instead ([http://en.wikipedia.org/wiki/Join_(SQL))](http://en.wikipedia.org/wiki/Join_(SQL))). I think you should picture each select - from -clause as a subset or a set and by joining those different select - from -clauses you can join them differently to get the desired result. But the Wikipedia page explains it better.. If you can set up a SQL database it might help you (it really helped me to understand it). If you run into more troubles just post another question and I'll try to answer it.

Good luck on your exam! I always had problems with the discrete math myself..

---

### Post by theorem_hunter on 2007-05-04
thank you, i will have a look at that :)

---

### Post by ola on 2007-05-04
To explain a bit furthrer. 

I think you should use the where part of the select more as a way to set up certain conditions for what data to include in your set (select). 

An example to retrieve all data from the salary table where salary.paycheck > 1000:
```

SELECT * 
FROM salary
WHERE salary.paycheck > 1000

```


Another example to retrieve all column in the person table and all columns in the salary table that also earns more than 1000:
```

SELECT *
FROM person, salary
WHERE person.id = salary.id AND salary.paycheck > 1000

```

Does it explain it?

---

### Post by theorem_hunter on 2007-05-04
yes, that explains it :) thanks

could it be modeled/mapped like this as well

the database is the set set U
tables are M, S & Z - lets just say that the tables just have integer keys
then to do grouping, like M &#8746; Z, you create select statements, like you have shown to get required results. :) 

i think i understand why i need to know inclusion & exclusion - in the bigger picture for a computer science student. inclusion & exclusion principles are used as algorithms for select-from-where an so on statements...

---

### Post by ola on 2007-05-05
Hi! If you look at the attached image sets.png you have 3 different examples.

Drawing 1: Intersection between M and Z (M &#8745; Z) would look something like:
```

SELECT * 
FROM M,Z
WHERE M.id = Z.id

```

Drawing 2: Union of M and Z (M &#8746; Z) would look something like I think:
```

SELECT * 
FROM M,Z

```

Drawing 3: I'm not sure what this is called but you could probably do it something like this in SQL:
```

SELECT * 
FROM M,Z
WHERE M.id <> Z.id

```

If you have a DB available it would be great if you could verify yourself..

---

### Post by theorem_hunter on 2007-05-05
thanks, the diagrams helped a lot... i have a DB.
i cant remember all the sql commands & syntax

for diagram 2: - i think you would use the unique clause so that you don't count the values that M & Z have in common... in other words make sure that you don't count them twice

---

