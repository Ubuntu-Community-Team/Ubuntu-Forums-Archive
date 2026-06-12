---
title: "Unique in Java?"
date: 2011-07-06
forum: Programming Talk
---

### Post by abraxas334 on 2011-07-06
Simple problem really:
I have a Vector definied like this:
Vector<int []> v;

now the int array passed is always  of length 2 so I end up with vectors looking like this:
0 15
0 15
12 18
15 12
15 12
15 12
18 19
18 19
19 21
19 21
19 21

I just want all single occurances of each set of numbers. In C++ I 'd just sort my 2-d vector and then use unique on it. Is there an equivalent in java?
I guess it is already sorted in this case, but how do I get rid of the duplicates?
Thanks,

---

### Post by PaulM1985 on 2011-07-06
You could use a hash set. [http://download.oracle.com/javase/6/docs/api/java/util/HashSet.html](http://download.oracle.com/javase/6/docs/api/java/util/HashSet.html)

This will only contain unique entries.

Paul

---

### Post by cgroza on 2011-07-06
Use a set. It will take care of that for you.

---

