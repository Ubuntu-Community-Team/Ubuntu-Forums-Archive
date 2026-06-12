---
title: "Arrays in Python"
date: 2009-01-09
forum: Programming Talk
---

### Post by 7raTEYdCql on 2009-01-09
I have a simple question in Python.

How do you initiate an array of a given number of variables.

such that all the initial elements are all '0'.

Note this is a part of my program therefore time is a constraint.

---

### Post by Modred on 2009-01-09
To create a list of length n with a default value x for all values in the list, try the following:

```

[x]*n

```

For example, [0]*10 gives the list [0, 0, 0, 0, 0, 0, 0, 0, 0, 0].

---

### Post by geforce123 on 2009-01-09
What about
```
a=[0]*10
```

EDIT: dang too late!

---

