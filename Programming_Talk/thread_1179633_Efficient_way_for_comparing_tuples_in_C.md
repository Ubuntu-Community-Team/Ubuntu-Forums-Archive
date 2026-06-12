---
title: "Efficient way for comparing tuples in C"
date: 2009-06-05
forum: Programming Talk
---

### Post by ittiam on 2009-06-05
I would like to compare each element of a tuple with all the elements of another tuple in C. For example 

```
Tuple 1 [20,30] [70,90].[100,150] ......
Tuple 2 [10,40] [80,120] [220,300] ......
```

I need to verify whether any of the element in tuple 1 fits into any of the element in tuple 2. Above example, [20,30] of tuple 1 fits in [10,40] of tuple 2. Also I will have to update tuple 1 if there are any overlapping. Element 2 of tuple 1, [70,90] on comparison with [80,120] should be updated to [70,120]. Get the gist?

Now that the question is stated, my problem is efficiency. The number of if checks is just too much and any suggestions for an efficient implementation will be helpful.

The programming language is strictly C. No python.

---

### Post by simeon87 on 2009-06-05
As you say, you want to compare each element in one tuple with those in another tuple. You can't do this more efficiently than comparing each element with each other element (i.e., you can't skip any elements). Same for the updating. Unless there's additional information about the problem that you can exploit.

Second, are you sure it is too much? Comparing integers doesn't take that much time and you can perform many comparisons without noticing. I'm just saying that it may be premature optimization to build a complex data structure for this.

---

### Post by ittiam on 2009-06-05
I don't think I am trying for premature optimization. I am trying to integrate this in an already existing embedded code base environment and I am just trying to explore options for an efficient implementation.

---

### Post by MadCow108 on 2009-06-06
if the tules are sorted you can use a binary search (with a good pivot near the start of the tuples) to find the first match of tuple 1 to tuple 2 and use this position for the rest of the entries.
should be a O(N) operation.

if not sorted you'll have to caluclate at which tuplesize it's faster to sort them first.

---

