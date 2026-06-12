---
title: "compare table rows fast"
date: 2009-05-11
forum: Programming Talk
---

### Post by fokuslee on 2009-05-11
if i want to compare two tables row by row, what is the fastest way? 
the table has blob and other mostly text attributes.  (actually a featureclass for gis pros out there)
can i treat each row as an object and calc hash value then just compare the hash values? 
i know reading each attribute out compare 1 by 1 is too slow. 

thanks abunch

---

### Post by Furat on 2009-05-11
generating hash value and compare them is a good  way to do it, and you can either calculate the hash value every time you want to compare or generate it when you create the row and every time you update the table depending on what you do more (comparing or updating

---

### Post by kknd on 2009-05-11
Loading the objects and calculating the hash it slower than comparing it directly, unless you can have another field that stores a pre-computed hash. But you would need to uodate it at every edition, so I think the best way is to just do a usual compare (in the database itself, before returning the rows, if you can).

---

