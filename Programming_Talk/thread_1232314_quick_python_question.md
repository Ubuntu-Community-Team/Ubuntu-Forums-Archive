---
title: "quick python question"
date: 2009-08-05
forum: Programming Talk
---

### Post by JDShu on 2009-08-05
How do I make a copy of a two dimensional list? I know the quickest way to make a copy of a one dimensional list is:

ListA=ListB[:]

Yet a two dimensional list (a list within a list) using that code ends up with only one dimension being a copy and the the seocnd dimension being references. ListA = ListB[:][:] also doesn't seem to work.

---

### Post by Bodsda on 2009-08-05
> **JDShu said:**
> How do I make a copy of a two dimensional list? I know the quickest way to make a copy of a one dimensional list is:

ListA=ListB[:]

Yet a two dimensional list (a list within a list) using that code ends up with only one dimension being a copy and the the seocnd dimension being references. ListA = ListB[:][:] also doesn't seem to work.

Use the copy module.
```
>>> import copy
>>> a = [[0]*4]*2
>>> a
[[0, 0, 0, 0], [0, 0, 0, 0]]
>>> b = copy.deepcopy(a)
>>> a, b
>>> print a,"\n",b
[[0, 0, 0, 0], [0, 0, 0, 0]]
[[0, 0, 0, 0], [0, 0, 0, 0]]
>>> a[0][0] = 1
>>> print a,"\n",b
[[1, 0, 0, 0], [1, 0, 0, 0]]
[[0, 0, 0, 0], [0, 0, 0, 0]]
>>>

```

Hope this helps,

Bodsda

---

### Post by JDShu on 2009-08-05
Thanks very much! I suppose thats the only way? I had hoped to avoid importing new modules, to avoid confusion but it definitely helps.

---

### Post by Bodsda on 2009-08-05
> **JDShu said:**
> Thanks very much! I suppose thats the only way? I had hoped to avoid importing new modules, to avoid confusion but it definitely helps.

I'm not sure, I asked in #python but didnt get much of a response. But tbh, dont worry about confusion, just add a comment

```

import copy #To duplicate an object
b = copy.deepcopy(a) #duplicates a as b

```
confusion avoided.

---

### Post by snova on 2009-08-05
> **JDShu said:**
> How do I make a copy of a two dimensional list? I know the quickest way to make a copy of a one dimensional list is:

ListA=ListB[:]

Yet a two dimensional list (a list within a list) using that code ends up with only one dimension being a copy and the the seocnd dimension being references. ListA = ListB[:][:] also doesn't seem to work.

Perhaps something like:

```
ListA = [i[:] for i in ListB]
```

Though the **copy** module might be simpler.

---

