---
title: "Array datatype for columns in MySQL?"
date: 2007-03-14
forum: Programming Talk
---

### Post by jazzgossen on 2007-03-14
I'd like to store a 3-element array in my MySQL database. Is that possible? I've read about the spatial geometry data types. There is a POINT type specified there, which would be perfect for me, but it is only 2D. 

If there is no array type, am I forced to have one column for each array element, or store the array as a TINYTEXT or something instead?

---

### Post by tribaal on 2007-03-14
I'd say having a "points" table with 4 columns (ID, X, Y, Z) would probably be the best option... 
Storing an array in a singl field is not very effective, usually, since you need to retrieve the whole set of coordinates if you wish to change only a single parameter.

- trib'

---

### Post by jazzgossen on 2007-03-14
Thanks for the quick reply! Are there any advantages of making a separate table for the points as compared to adding those columns to my main table?

---

### Post by tribaal on 2007-03-14
Well generally speaking you want to keep your data logically organised in tables... and not put everything in a single table.

Since I don't know exactly how you plan to use your coordinates, I just went with the most simple example :)

The most simple would be to store only the coordinates and the point's identifier in a table... but depending on your application, it might make sense to add other things to it like a "label" field or what have you...

While it's probably a long read for a small application you should consider reading about [database normalisation]("http://en.wikipedia.org/wiki/Normal_forms"), the article outlines most of the pitfalls it helps avoiding :) EDIT: Most of it is pretty horrible to read, but the examples section makes it clear IMO.
EDIT2: here's [another article]("http://www.troubleshooters.com/littstip/ltnorm.html") about it that a little more... digest :)

Hope this helps... ;)

- trib'

---

### Post by lnostdal on 2007-03-14
I don't know much about MySQL but PostgreSQL has an array-type built in: 
[http://www.postgresql.org/docs/8.2/static/datatype.html](http://www.postgresql.org/docs/8.2/static/datatype.html)

..in general it seems PostgreSQL has support for more types than MySQL. It might be a better choice than MySQL if you're going to store a lot of complex data/types, but I might be missing something. :)

---

### Post by jazzgossen on 2007-03-15
Thanks a lot for the links on database normalisation. There's more to databases than I thought... but now I think I have a more sensible table setup than the one I first thought of (three tables instead of one, and I think it's on 3NF now). 

Maybe I should use PostgreSQL instead of MySQL to get the array indices. I've used mysql-admin to create the table layout, and I like that program a lot. Is there a similar GUI for PostgreSQL? On the other hand, I will do most of the interfacing with the database from C++ and shell scripts, so I guess a good GUI for table layouts isn't essential.

---

### Post by lnostdal on 2007-03-15
Try pgadmin.

---

