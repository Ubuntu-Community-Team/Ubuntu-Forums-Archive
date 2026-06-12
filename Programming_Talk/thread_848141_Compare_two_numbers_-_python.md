---
title: "Compare two numbers - python"
date: 2008-07-03
forum: Programming Talk
---

### Post by Xavieran on 2008-07-03
Hello All,

I need to compare the value of two variables in python to see
which is closer to 0 and then two order them from closest to farthest.

eg.
a=-2
b=-4
c=3
How do I get python to order them from closest and farthest to 0?

Thanks,
Emmanuel

---

### Post by Wybiral on 2008-07-03
Use sort, and the absolute value for the comparison:
```

lst = [5, -2, 9, 1, -6, -3, 2]
f = (lambda a, b: cmp(abs(a), abs(b)))
print sorted(lst, f)

```

---

### Post by thelugnut on 2011-08-05
I was looking for the answer to this and just happened to stumble across this thread. I would like to thank Wybiral. Solved my problem very nicely.:)

---

### Post by stchman on 2011-08-05
To compare two numeric values use the 
==, >, <, >=, <=, !=

[http://docs.python.org/library/stdtypes.html](http://docs.python.org/library/stdtypes.html)

To sort an array simply use the .sort(), I believe it is in the sys library.

---

