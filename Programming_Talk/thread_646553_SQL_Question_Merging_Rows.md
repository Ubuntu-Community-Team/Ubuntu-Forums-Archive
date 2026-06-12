---
title: "SQL Question: Merging Rows"
date: 2007-12-21
forum: Programming Talk
---

### Post by dhtseany on 2007-12-21
Hi all,

Is there a way to merge data from 2 rows in a table into one row? Check out my sweet mspaint skills for a better understanding of what I mean :)

Peace

Sean

Before:
[IMG]http://img406.imageshack.us/img406/8915/temp1zv8.png[/IMG]

After:
[IMG]http://img512.imageshack.us/img512/9543/temp2ho2.png[/IMG]

---

### Post by Paulmd on 2007-12-21
> **dhtseany said:**
> Hi all,

Is there a way to merge data from 2 rows in a table into one row? Check out my sweet mspaint skills for a better understanding of what I mean :)

Peace

Sean

Before:
[IMG]http://img406.imageshack.us/img406/8915/temp1zv8.png[/IMG]

After:
[IMG]http://img512.imageshack.us/img512/9543/temp2ho2.png[/IMG]


Sure. Those are columns, btw. Rows go the other way.

SELECT COLUMN1 + COLUMN2 AS MY_LINE FROM MY_TABLE; 

You can insert string literals, too

SELECT COLUMN1 +"some text" + COLUMN2 AS MY_LINE FROM MY_TABLE;

---

### Post by dhtseany on 2007-12-21
So if I had a Column named "NPA" and another called "NXX" and I wanted to combine them, I would:

```
Select NPA + NXX AS [New Column Name] From Tablename
```

Right?

---

### Post by Paulmd on 2007-12-21
> **dhtseany said:**
> So if I had a Column named "NPA" and another called "NXX" and I wanted to combine them, I would:

```
Select NPA + NXX AS [New Column Name] From Tablename
```

Right?

Correct. You must be careful of data types, though. Since if the values are numbers, the '+' operator will add them. If they are strings, they are concatenated.

Most sql implementations have functions to force data types, so as to not confuse the issue.

---

### Post by CptPicard on 2007-12-22
Check your database manual for the operator... at least on PostgreSQL string concatenation is "||", not "+".

---

