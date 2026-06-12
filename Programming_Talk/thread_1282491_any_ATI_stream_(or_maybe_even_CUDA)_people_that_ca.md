---
title: "any ATI stream (or maybe even CUDA) people that can help me out?"
date: 2009-10-04
forum: Programming Talk
---

### Post by dracule on 2009-10-04
Ok

So I have a problem

I have 2 3 dimensional arrays (arr1, arr2)
and 1 2 dimensional array (arr3)

So I need to sum all the values in arr1 and arr2 and use them to modify the things in arr3

so if we have a loop(these are just arbitrary equations in there):
```

for i..
    for j....
         for k....
            sum+=arr1[i][j][k]+arr2[i][j][k]
    arr3[i][j] = arr3[i][j]-sum

```

everything in the j dimension can be calculated independantly, so naturally it can be put through Stream. But im fuzzy on the archetecture of the Brook+ kernel and how it would do this.

---

