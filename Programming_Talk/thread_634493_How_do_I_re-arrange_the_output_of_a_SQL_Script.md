---
title: "How do I re-arrange the output of a SQL Script?"
date: 2007-12-07
forum: Programming Talk
---

### Post by SNYP40A1 on 2007-12-07
Say I have a query that tells me about how many items were sold at a hardware store for each week.  Then the output would look something like this:

Week,Item,Num_Sold
13,Hammer,15
13,Nail,594
13,Screw,398
14,Hammer,16
14,Nail,382
14,Screw,331
...

But I want my output to look like this:

<space>,13,14
Hammer,15,16
Nail,594,382
Screw,398,331

Can I do that in SQL?  Essentially, I want the column to be the week and have the rows be the item.

---

### Post by CptPicard on 2007-12-07
In theory you can, but it would require you to join separate queries for each week into the result. That would be a fixed number of joins (and weeks) too, and the query would look really complex and ugly, and would probably run slow.

If I were you, I'd just write some code on top of the database in your favourite language to handle this if possible. If you need the result in some subsequent query, I'd reconsider how that in turn is written...

---

