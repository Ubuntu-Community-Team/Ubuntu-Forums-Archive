---
title: "SQL index returning different results"
date: 2007-10-08
forum: Programming Talk
---

### Post by DouglasAWh on 2007-10-08
I'm learning indexing in my database class and I'm supposed to:

> 
        Contrast four different solutions:
      1) using no index (be sure to drop any existing indexes created by MySQL),
      2)standard index on text field,
      3) shortened character index (char(10)) on subject, and
      4) fulltext index (use MATCH AGAINST in your query). Demonstrate all four versions in MySQL, including showing run times. Describe what you think is the best overall choice, and why.


However, the different indexes don't return the same values.  All of the indexes seem to return 175 and the non-index returns over 2000.  I don't feel like the shortened char(10) index should return as many values as the others because not all the values of the query are within the first 10 queries?

Thoughts?

---

### Post by DouglasAWh on 2007-10-08
I've done some more reading, and it appears the syntax for wildcards in MATCH()AGAINST() is different than in LIKE.

However, I am still getting 2425 rows in set (2.51 sec) using MATCH AGAINST versus 2587 rows in set (2.16 sec) when I use LIKE.  Why on earth would this be happening?

---

