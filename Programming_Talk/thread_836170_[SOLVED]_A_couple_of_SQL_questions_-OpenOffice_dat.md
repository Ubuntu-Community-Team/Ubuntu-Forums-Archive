---
title: "[SOLVED] A couple of SQL questions -OpenOffice database"
date: 2008-06-21
forum: Programming Talk
---

### Post by fatality_uk on 2008-06-21
Apologies if these questions seem too simple to answer!!! I haven't picked up a keyboard to programme in years :D

I have a table in an OOo DB.
A couple of tables I am trying to query are

```
product_desc = Text[VARCHAR]
offer_start_date = Date[DATE]

```
And here is the query I am trying to run, obviously without too much joy.```

SELECT * FROM "slw_offer_table" WHERE "product_desc" LIKE 'Car%' AND 'offer_start_date' > '19/06/08'
```

The results are coming back with everything **LIKE** Car. I wanted to filter out by date.

Anyone please point me in the right direction.

---

### Post by fatality_uk on 2008-06-22
Marked as solved.
Just installed LAMP stack

---

