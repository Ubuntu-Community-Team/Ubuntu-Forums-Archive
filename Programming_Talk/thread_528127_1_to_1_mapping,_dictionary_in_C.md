---
title: "1 to 1 mapping, dictionary in C"
date: 2007-08-17
forum: Programming Talk
---

### Post by Lster on 2007-08-17
Hi again all

I have search google but was unable to find how to program a dictionary that maps 1 integer to another. I have thought of a few methods... I am dealing with very large amounts of data...

Thanks,
Lster

---

### Post by Mirrorball on 2007-08-17
I would use a binary tree, or if I were really storing a huge amount of data, I'd consider a database.

---

### Post by aks44 on 2007-08-17
A not-so-bad method would be to have an array of (key, value) sorted by key, and apply a dichotomic search on it. This is the best bet if your dataset does not change much. If the data changes too often, you will spend way too much time copying/sorting the array.


Using a BTree is the best method if your data is very dynamic. Search time is quite close to a dichotomic search, and insert/delete time is quite good too. There's a reason why all database engines use a (variation of) Btree for their indexes. ;)
Expect to have hard times implementing it though, unless you can find an implementation that fits your needs.


Oh BTW, a linked list is the worst you could do performance-wise. You can't randomly access elements so you'd have to go through the whole list for each and every search.


Hope this helps a bit. :)


EDIT: or as Mirrorball said, consider using a database. You won't notice the little performance loss, and the gains will be amazing (guaranteed correctness, development time, scalability, ...). A good product for small projects is SQLite, it is an embedded SQL engine with very little overhead. Of course it has many drawbacks, as it isn't a fully fledged DB engine, but it's enough for most cases (and anyway way better than what one could quickly hack by himself).

---

### Post by Lster on 2007-08-17
Thank you guys! :)

---

### Post by moma on 2007-08-18
Here is a tar-ball that contains some advanced data types written in c.
[http://home.online.no/~osmoma/adt/](http://home.online.no/~osmoma/adt/)
Open the "adt-0.1.tar.gz" ball  and look for ptree.[ch] files in the /src directory.

There is also an example in the /test directory.

The code in the ptree.[ch] implements a self balancing binary search tree using the fast [Red-Black balancing]("http://en.wikipedia.org/wiki/Red-black_tree") algorithm. It's an iterative (non recursive) implementation.

Use that code and **create a hash-function** that will return a (hopefully unique ) key to find a correct node in the red-black binary tree.  The example code (in the /test dir) just uses integers as keys. The _key_ and _data value_ are the same.

There are 2 pictures in [http://home.online.no/~osmoma/adt/](http://home.online.no/~osmoma/adt/)  
The README file tells how to compile and run the tests.  The "adt-0.1.tar.gz" ball contains also ADTs (abstract data types) Parray and Plist which also will provide a good solution.

The code is GPL.

---

### Post by Lster on 2007-08-18
Thank you. I will enjoy taking a look at that!

---

### Post by CptPicard on 2007-08-18
Of course, the first question is "how dense is your dataset". If between keys 1..N most of the keys are in use, I'd use a simple array where the index is key and element is value :)

If not, go with your idea of array with structs, keep it sorted, and then use binary search. Will be much more efficient and simpler than a tree.

Whatever you do, database is probably overkill and will be the slowest solution of all.

---

