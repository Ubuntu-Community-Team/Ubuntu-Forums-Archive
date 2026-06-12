---
title: "Binary sorting?"
date: 2006-09-14
forum: Programming Talk
---

### Post by sankarv on 2006-09-14
What is Binary sorting?

How can it be performed on linked lists (in C)?

Please help.

---

### Post by beathan on 2006-09-14
Are you referring to binary insertion sort, in which you have a small data set and use binary search to find the proper location for the new data before inserting it? If that's the case, then you'll be unable to use it with linked lists since they are not random access, which binary insertion sort would require.

You can implement a binary search tree that will give you the speed of binary search with inexpensive add/removal of nodes.

[Here's a link]("http://en.wikipedia.org/wiki/Insertion_sort") to Wikipedia with information on insertion sort, including binary insertion sort.

---

