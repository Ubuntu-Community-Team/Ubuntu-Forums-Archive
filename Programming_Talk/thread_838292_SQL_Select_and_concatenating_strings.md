---
title: "SQL Select and concatenating strings"
date: 2008-06-23
forum: Programming Talk
---

### Post by mikeym on 2008-06-23
Hi,

Sorry this isn't really the place for this but I was wondering if anyone could tell me quickly how to concatenate strings together in an SQL statement like:


```
SELECT `page` + '#' + `section` AS 'url'
FROM `bbcode`
```

Which currently returns '0' for each field.

---

### Post by Keith Hedger on 2008-06-23
I think this is what u need```
mysql> SELECT CONCAT('My', 'S', 'QL');
        -> 'MySQL'
mysql> SELECT CONCAT('My', NULL, 'QL');
        -> NULL
mysql> SELECT CONCAT(14.3);
        -> '14.3'
```

u might want to install the docs for my sql via synaptic (mysql-doc-5.0)

---

### Post by CptPicard on 2008-06-23
The standard string concatenation operator in SQL is ||. Like 'Add this' || ' to this'.

---

### Post by henchman on 2008-06-23
There's an useful overview of mysql's string manipulation functions (including CONCAT and CONCAT_WS) here:

[http://dev.mysql.com/doc/refman/5.0/en/string-functions.html](http://dev.mysql.com/doc/refman/5.0/en/string-functions.html)

---

### Post by CptPicard on 2008-06-23
The OP isn't saying anything about MySQL... there are other SQL databases you know :)

---

### Post by henchman on 2008-06-23
Sorry... sql seem to be automatically mysql for me...:(

---

### Post by Keith Hedger on 2008-06-24
yeah same here but isn't the basic syntax on sql standard?

---

### Post by CptPicard on 2008-06-24
> **Keith Hedger said:**
> yeah same here but isn't the basic syntax on sql standard?

Yes. That's why he should be using the standard '||' (IIRC) instead of nonstandard mysql functions :)

---

