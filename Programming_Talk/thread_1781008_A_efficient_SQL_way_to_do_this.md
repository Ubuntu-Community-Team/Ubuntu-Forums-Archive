---
title: "A efficient SQL way to do this?"
date: 2011-06-12
forum: Programming Talk
---

### Post by sefs on 2011-06-12
I have a table that looks like this

FLD1   FLD2   FLD3
---------------
val1   val2   val3
val1   val3   val2
val1   val2   val4
val1   val3   val4

I only want to select distinct rows.  
Looking at the table above there are no duplicate rows in the strictest sense.

In my case though I want identify a duplicate row as a row that contains the same values  but not necessarily do they have to be equal column for column

Hence I want to identify row1, and row2 above as a duplicate of each other. 

Is there a sql statement I can use to filter out duplicate rows when I define it like that?

Thanks.

---

### Post by JupiterV2 on 2011-06-12
Your first weapon as a programmer is a search engine. A simple search for "select distinct multiple columns" got me many hits. The first one I think can help you: [http://stackoverflow.com/questions/54418/how-do-i-or-can-i-select-distinct-on-multiple-columns-postgresql]("http://stackoverflow.com/questions/54418/how-do-i-or-can-i-select-distinct-on-multiple-columns-postgresql").

---

### Post by Petrolea on 2011-06-13
> **JupiterV2 said:**
> Your first weapon as a programmer is a search engine. A simple search for "select distinct multiple columns" got me many hits. The first one I think can help you: [http://stackoverflow.com/questions/54418/how-do-i-or-can-i-select-distinct-on-multiple-columns-postgresql]("http://stackoverflow.com/questions/54418/how-do-i-or-can-i-select-distinct-on-multiple-columns-postgresql").

I agree. And word 'distinct' actually exists in SQL.

---

### Post by PaulM1985 on 2011-06-13
Although I agree with the idea of using search engines, the "select distinct" is not going to work in this case because the OP also wants to be able to re-order the columns for matches, (see the part where row 1 and row 2 are to be considered as duplicates).

Have you any extra information about what types your valX are?  varchar, ints, etc...

Paul

---

### Post by r-senior on 2011-06-13
> **PaulM1985 said:**
> Although I agree with the idea of using search engines, the "select distinct" is not going to work in this case
+1

Tricky one. My first thought was to concatenate string representations of the columns, sort the characters and then select distinct:

```

**val1 val2 val3 -> 123aaalllvvv**
val1 val3 val2 -> 123aaalllvvv
**val1 val2 val4 -> 124aaalllvvv**
**val1 val3 val4 -> 134aaalllvvv**

```

But that doesn't work if there are anagrams of values:

```

**val1 val2 val3 -> 123aaalllvvv**
val1 val3 val2 -> 123aaalllvvv
[COLOR="Red"]val1 alv3 alv2 -> 123aaalllvvv[/COLOR] (missing row)
**val1 val2 val4 -> 124aaalllvvv**
**val1 val3 val4 -> 134aaalllvvv**

```

So you'd have to treat the column values as tokens, sort the tokens without disturbing their individual letters and select distinct on that result.

Paul's question about data types is an important one I think.

---

### Post by roccivic on 2011-06-14
Databases are not supposed to be able to do cross columns ordering. If you find yourself in a situation where you have to, it's probably because you made a design error at some earlier stage. That said, if you really want to, you can sort by columns, concatenate and select distinct. But that does not fit well with the title of this thread, which includes the word "efficient". It will be everything, but efficient. For an example of a cross-column sort, see here: [http://stackoverflow.com/questions/2814244/best-way-to-sort-n-concatenate-5-columns]("http://stackoverflow.com/questions/2814244/best-way-to-sort-n-concatenate-5-columns")

---

### Post by Maheriano on 2011-06-14
Do a select on each column so you have 3 separate record sets, but do each SQL query as not in the next.

For example, something like:
select column1 from tablename as value1 where value1 not in (select column2 from tablename as value2)

---

