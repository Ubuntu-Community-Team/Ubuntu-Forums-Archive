---
title: "Python Tuple Comparison Question"
date: 2008-11-11
forum: Programming Talk
---

### Post by Luggy on 2008-11-11
Hello everyone, I encountered something strange when trying to perform some tuple comparison while using python.

In a python terminal I try and compare one tuple with another. I expect to get a boolean but I get another tuple? Here is what I enter:
```

>>> 1,1 == 1,1
(1, True, 1)
>>>

```

However if I set the tuples as variables and compare them I get a boolean!
```

>>> a = 1,1
>>> b = 1,1
>>> a == b
True
>>>

```

So I have away around the problem, but why was I getting that in the first place?

---

### Post by imdano on 2008-11-11
Precedence rules. 1, 1 == 1, 1 is evaluated as 1, (1 == 1), 1, which is why you get a tuple as a result.  Also, the a = 1,1 assignment actually becomes (1, 1), which will be evaluated as you expect.
```
>>> a = 1,1
>>> print a
(1, 1)
>>> b = (1,1)
>>> print b
(1, 1)
>>> (1,1) == (1,1)
True
>>> 1, 1 == 1, 1
(1, True, 1)
>>> 1, (1 == 1), 1
(1, True, 1)
```

---

### Post by unutbu on 2008-11-11
```
1,1==1,1
``` is the same as

```
1,(1==1),1
```  or
```
1,True,1
```

---

### Post by pmasiar on 2008-11-11
> **Luggy said:**
> So I have away around the problem, but why was I getting that in the first place?

because == has higher preference than comma?

To make tuple, use (a,b,c). Comma just separates list arguments, () makes list into tuple.

To make "one-ple" (tuple with just one item), canonical trick is (a,)

---

### Post by ichi@YUKI on 2008-11-11
yup.. you need to be careful with variable assignments.. in the end it's just syntax.

---

### Post by Luggy on 2008-11-11
Awesome, thanks for the quick answer. I had a feeling it would be something simple like that.

---

