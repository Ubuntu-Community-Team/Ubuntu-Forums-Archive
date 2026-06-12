---
title: "SQL Update query"
date: 2012-05-14
forum: Programming Talk
---

### Post by psycho5 on 2012-05-14
Hi,
 

I have this code in SQL that works fine. 

```

update Electronics_01 set categories = right(categories;len(categories)-2) where left(categories;2)="1,"

```

How do I make it so that it works for multiple tables such as

```
update Electronics_01,Electronics_02 set Electronics_01.categories = right(Electronics_01.categories;len(Electronics_01.categories)-2 where left (Electronics_01.categories;2)="1,"
```

Need to make changes to around 9 tables. What is the correct syntax for performing that task for multiple tables?

Thanks!

---

### Post by Tony Flury on 2012-05-14
I think we need to know more about your tables, and how they connect together.

Can you describe the structure of your database.

at first glance - if you have tables called Electronics_01, Electronics_02 etc - you may well have a troublesome data base structure.

---

### Post by psycho5 on 2012-05-14
> **Tony Flury said:**
> I think we need to know more about your tables, and how they connect together.

Can you describe the structure of your database.

at first glance - if you have tables called Electronics_01, Electronics_02 etc - you may well have a troublesome data base structure.

The tables represent 7 attributes of products:

electronics
media
home and living
health and beauty
toys
others
sports

each with categories which are basically 'child' of the 'mother' 
electronics is huge so its divided into 01-07, the rest are as is. 

I hope this helps.

---

### Post by codemaniac on 2012-05-14
You cant update multiple tables with one update statement. What you can do though is command Oracle to write your multiple update statements for you i.e.
```

select 'update '||table_name||' set categories = right(categories;len(categories)-2) where left(categories;2)=1;'
from user_tab_columns
where column_name = 'categories'

```
and then paste it into sqlplus or something similar.

---

### Post by psycho5 on 2012-05-14
> **codemaniac said:**
> You cant update multiple tables with one update statement. What you can do though is command Oracle to write your multiple update statements for you i.e.
```

select 'update '||table_name||' set categories = right(categories;len(categories)-2) where left(categories;2)=1;'
from user_tab_columns
where column_name = 'categories'

```
and then paste it into sqlplus or something similar.

Hey! Thanks man! I'll give this a try.

---

### Post by Tony Flury on 2012-05-17
> **psycho5 said:**
> The tables represent 7 attributes of products:
each with categories which are basically 'child' of the 'mother' 
electronics is huge so its divided into 01-07, the rest are as is. 

Why divide it ? Too many columns or too many rows ? If you db engine can't handle large numbers of rows in your table - use a different db engine. If you have two many columns - then dividing it might be the right solution - but i would think of a better naming system.

---

