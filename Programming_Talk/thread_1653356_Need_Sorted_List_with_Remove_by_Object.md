---
title: "Need Sorted List with Remove by Object"
date: 2010-12-26
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-12-26
I am trying to implement a calculation of median or percentile across a time series.  The calculation will be windowed (start with window of first 5000 elements, compute median, move window forward by 1, compute median...repeat many times).  I could use Apache's Descriptive Statistics class to do this, but I don't want to have to keep emptying and filling the container on every move.  To implement this more efficiently, I would need a sorted list where I can remove items by key (the item itself).  Does anyone know of such a container implemented in Java?  The items would be sorted from lowest value to highest value, but I want to occasionally remove the oldest (by time last inserted) 'x' elements in the set.  But lowest item in array would be at index 0, highest at index = size() -1 (or swapped, doesn't matter).

---

### Post by SNYP40A1 on 2010-12-26
[http://stackoverflow.com/questions/3738349/fast-algorithm-for-repeated-calculation-of-percentile](http://stackoverflow.com/questions/3738349/fast-algorithm-for-repeated-calculation-of-percentile)

---

