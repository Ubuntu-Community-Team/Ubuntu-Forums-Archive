---
title: "SQL order by order by a dynamic column not returned"
date: 2010-06-05
forum: Programming Talk
---

### Post by uncleBez on 2010-06-05
Wasnt exactly sure how to phrase the title for this.
ok so an example to get started.

SELECT IF(column1 is null,column1,column2) as orderbyme, column3 FROM table1 ORDER BY orderbyme

This does 'almost' exactly what I want. However I dont want orderbyme returned in the resultset. I only want column3...
Make sense?

How can I write this SQL to only return me column3, but still order the results by the resulting value of the if function?

Someones gonna find this easy!!! :D

---

### Post by Some Penguin on 2010-06-06
That SELECT looks like it should return a temporary table of two columns.  One of those columns is 'orderbyme', and one of them is 'column3'.   So one approach is to use that as input for another SELECT call.

---

