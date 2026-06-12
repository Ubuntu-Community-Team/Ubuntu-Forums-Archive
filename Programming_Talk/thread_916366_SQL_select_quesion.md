---
title: "SQL select quesion"
date: 2008-09-10
forum: Programming Talk
---

### Post by tc101 on 2008-09-10
I have a table with a field named "book_id".  How do I write a select statement to get the value for the book_id in the last record in the table?

I tried 

SELECT LAST(book_id) FROM phototable 

and it didn't work

---

### Post by slavik on 2008-09-10
in a relational database, rows (records) do not have a relationship among themselves. there is also no real understanding of first/last record.

---

### Post by raptor2552 on 2008-09-10
Hello
give this a try:
```

select max(book_id) from phototable 

```

---

### Post by slavik on 2008-09-10
> **raptor2552 said:**
> Hello
give this a try:
```

select max(book_id) from phototable 

```
good point, but is book_id auto_increment or could it be the book;s ISDN number?

---

### Post by tc101 on 2008-09-10
Thanks to you both.  

select max(book_id) from phototable

works in this particular case, but I see slavik's point that it would only work in certain cases.

---

### Post by pmasiar on 2008-09-11
Oracle has rownum - seq number of the row in resultset. Other databases might have similar tricks. It's ridiculous how unstandard the 'SQL standard' is. Pure mirage.

get last 10 records (gets you first, but sorted as descending)

SELECT (some fields) FROM ... WHERE ... rownum < = 10 ORDER BY field DESC

Many databases can also return id of last inserted ID, which is probably what you want.

---

### Post by Mickeysofine1972 on 2008-09-11
```
select book_id, COUNT(book_id) offset from phototable LIMIT offset, 1;

```

This would probably do the trick too in mysql or oracle

Mike

---

