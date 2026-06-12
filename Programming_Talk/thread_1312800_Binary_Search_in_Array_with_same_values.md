---
title: "Binary Search in Array with same values"
date: 2009-11-03
forum: Programming Talk
---

### Post by TzaB on 2009-11-03
Hello community! I have a problem with Binary Search.

I need to search an Array (that is sorted) using Binary Search, for a specific value and get its position.

The problem is that i don't know if the specific value exists on more than one place in the Array. (The client inputs the contents of the Array)
If there are multiple elements with this value, then i need to get their positions. Not only the first that Binary Search will find.

I searched at Java API and i found that the Binary Search that Java includes has the following comment:

"*If the array contains multiple elements with the specified value, there is no guarantee which one will be found*"

If someone can help me, i would be very grateful :D 

Thanks in advance,
TzaB

---

### Post by CptPicard on 2009-11-03
A binary-searched array has to be in sorted order before searching, so when you find one of the values, the rest will be next to it. So it is enough to scan left and right from the found value to discover the bounds of the area.

Theoretically this can cause the search to become linear-time in worst case (all equal values). It is possible to adapt the search for the upper and lower bound of the array segment, by finding, for example, for the upper bound two consequent elements where first one is the size you're trying to find, and the next one is larger.

---

### Post by TzaB on 2009-11-03
Thanks for the answer CptPicard. I will try to code it.

---

### Post by MadCow108 on 2009-11-03
two boundary searches will do the trick when O(logN) has to be preserved in all cases.
a little speedup is archived by using the iterator returned by the first search as start/end of the second
here some implementation help:
[http://www.cplusplus.com/reference/algorithm/lower_bound/](http://www.cplusplus.com/reference/algorithm/lower_bound/)
[http://www.cplusplus.com/reference/algorithm/upper_bound/](http://www.cplusplus.com/reference/algorithm/upper_bound/)

---

