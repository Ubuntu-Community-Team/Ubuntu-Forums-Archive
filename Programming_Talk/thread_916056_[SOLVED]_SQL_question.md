---
title: "[SOLVED] SQL question"
date: 2008-09-10
forum: Programming Talk
---

### Post by xlinuks on 2008-09-10
Hi,
I have 2 tables in MySQL (all columns are varchar if it matters):
1) "countries" contains the countries of the world in 2 columns (iso,full_name) for example ("it", "Italy").
2) "locations" has 2 columns (source_country,dest_country) both of which correspond to a iso value from table "countries".

When I query the "locations" table I get the iso names, but I would like that based on the "countries" table to get the full names of the countries, how do I do that?
I think it has to do with subqueries, read a few tutorials still can' figure it out.

I hope I made myself clear.

Example:
instead of getting ("it", "de") (source_country and dest_country correspondingly) I would like to get ("Italy", "Germany") based on the full names I have in the "countries" table.

---

### Post by cb951303 on 2008-09-10
first get the location isos. then get the full country names in a secong query using WHERE clause :popcorn:

---

### Post by drubin on 2008-09-10
I would recommend reading up on JOINS instead of running 2 queries this is often more resource intensive then a single join.

[http://dev.mysql.com/doc/refman/5.0/en/join.html](http://dev.mysql.com/doc/refman/5.0/en/join.html)

Basically what a join does is takes the values from 2 or more tables and "links" them.

---

### Post by xlinuks on 2008-09-10
> **cb951303 said:**
> first get the location isos. then get the full country names in a secong query using WHERE clause :popcorn:

Thanks, I probably forgotten to mention that I wanna do it within a single query.

rubinboy - thank you, I'll have a look at that and post if successfull, but a simple example would be great.

---

### Post by drubin on 2008-09-10
> **xlinuks said:**
> Thanks, I probably forgotten to mention that I wanna do it within a single query.

rubinboy - thank you, I'll have a look at that and post if successfull, but a simple example would be great.

It is possible to do with in one query it will not be a "simple" query though. 

Linking a table to another is fairly simple but having a table link 2 times 2 another table is a little bit more complex. I am rather puzzled all of my simpler examples fail under this situation.

---

### Post by drubin on 2008-09-10
Some one gave this to me. [http://www.wellho.net/solutions/mysql-left-joins-to-link-three-or-more-tables.html](http://www.wellho.net/solutions/mysql-left-joins-to-link-three-or-more-tables.html)

[http://codepad.org/f0l4MWQG](http://codepad.org/f0l4MWQG) 

In case the paste times out
```

SELECT
  sc.name,
  dc.name
FROM
  locations l
  JOIN countries AS sc ON l.source_country = sc.iso
  JOIN countries AS dc ON l.destination_country = dc.iso

```

---

### Post by xlinuks on 2008-09-10
> **rubinboy said:**
> Some one gave this to me. [http://www.wellho.net/solutions/mysql-left-joins-to-link-three-or-more-tables.html](http://www.wellho.net/solutions/mysql-left-joins-to-link-three-or-more-tables.html)

[http://codepad.org/f0l4MWQG](http://codepad.org/f0l4MWQG) 

In case the paste times out
```

SELECT
  sc.name,
  dc.name
FROM
  locations l
  JOIN countries AS sc ON l.source_country = sc.iso
  JOIN countries AS dc ON l.destination_country = dc.iso

```

Thank you very much! it works!

---

