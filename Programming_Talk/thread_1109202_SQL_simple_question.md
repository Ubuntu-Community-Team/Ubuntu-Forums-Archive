---
title: "SQL simple question"
date: 2009-03-28
forum: Programming Talk
---

### Post by cl333r on 2009-03-28
Hi folks,
Can't figure out how to google for such a question, a link or example would be much appreciated.
Say I have a table with a column 'colors' (like yellow, green,..).
How do I write an SQL query to get the list of different colors in that table?

Say there are 5 rows: yellow, yellow, green, green, blue
so that the request returns: yellow, green, blue

---

### Post by miken79 on 2009-03-28
select distinct colors from table.

---

### Post by simeon87 on 2009-03-28
Use SELECT DISTINCT: [http://www.w3schools.com/sql/sql_distinct.asp](http://www.w3schools.com/sql/sql_distinct.asp)

---

### Post by riksweeney on 2009-03-28
> **cl333r said:**
> Hi folks,
Can't figure out how to google for such a question, a link or example would be much appreciated.
Say I have a table with a column 'colors' (like yellow, green,..).
How do I write an SQL query to get the list of different colors in that table?

Say there are 5 rows: yellow, yellow, green, green, blue
so that the request returns: yellow, green, blue

```
SELECT DISTINCT COLORS
FROM COLOR_TABLE
```

This will select all the unique values from the COLORS column in the COLOR_TABLE table.

---

### Post by davec64 on 2009-03-28
It all depends which SQL you are using MSSQL, MYSQL, PLSQL (Oracle) etc.

As far as I know all the above are correct unles you are using MSSQL which would be:

```

Select Distinct (Colors)
From Colors_Table

```

It has the addition of brackets around the column name.

---

### Post by cl333r on 2009-03-28
Wow! thanks a lot to all of you!

---

### Post by s1ightcrazed on 2009-03-28
> **davec64 said:**
> It all depends which SQL you are using MSSQL, MYSQL, PLSQL (Oracle) etc.

As far as I know all the above are correct unles you are using MSSQL which would be:

```

Select Distinct (Colors)
From Colors_Table

```

It has the addition of brackets around the column name.

Informix and possibly DB2 use Select Unique, unless my memory is mistaken.

---

