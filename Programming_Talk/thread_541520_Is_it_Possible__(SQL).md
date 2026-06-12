---
title: "Is it Possible ? (SQL)"
date: 2007-09-02
forum: Programming Talk
---

### Post by 008325 on 2007-09-02
hi all ,

i have a problem on doing the SQL 

i have two table , package and item 

package table structure :

Code , item1 ,item2 , item3 , item 4 

item table structure :

Code , TotalCost 

P.S in the package table , item1~4 is a item code 

==============

now , how can i sum item 1~4 item cost  of the package table ???

i dont know how to do this, is it possible ?

---

### Post by pmasiar on 2007-09-02
Your table is denormalized, so you have to sum it manually (you cannot use sum over rows). What will happen if package has more that 4 items?

---

### Post by Mirrorball on 2007-09-02
I think it can be done with four (!!!) inner joins.
```

SELECT item1.TotalCost + item2.TotalCost + item3.TotalCost + item4.TotalCost FROM package INNER JOIN item AS item1 ON package.item1 = item1.Code  INNER JOIN item AS item2 ON package.item2 = item2.Code INNER JOIN item AS item3 ON package.item3 = item3.Code INNER JOIN item AS item4 ON package.item4 = item4.Code GROUP BY package.Code WHERE 1

```
Horrible. Use LEFT JOIN instead of INNER JOIN if some packages have less than four items, also (and especially) consider normalization.

---

### Post by 008325 on 2007-09-03
> **Mirrorball said:**
> I think it can be done with four (!!!) inner joins.
```

SELECT item1.TotalCost + item2.TotalCost + item3.TotalCost + item4.TotalCost FROM package INNER JOIN item AS item1 ON package.item1 = item1.Code  INNER JOIN item AS item2 ON package.item2 = item2.Code INNER JOIN item AS item3 ON package.item3 = item3.Code INNER JOIN item AS item4 ON package.item4 = item4.Code GROUP BY package.Code WHERE 1

```
Horrible. Use LEFT JOIN instead of INNER JOIN if some packages have less than four items, also (and especially) consider normalization.

thanks ..Mirrorball 

may i ask more 1 question ?

if the packagelist have 8 item field

i want first 4 item cost - 4~8 item cost to get the profit 

is it the same ? may u showing the SQL ?

really really thanks

---

### Post by 008325 on 2007-09-03
deleted

---

