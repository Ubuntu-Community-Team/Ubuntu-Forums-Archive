---
title: "[SOLVED] Python - Return x chars from right of string"
date: 2008-10-28
forum: Programming Talk
---

### Post by MaxVK on 2008-10-28
Hi there. I'm looking for something that will return x number of chars from the right or left of a string - similar to the old VB Left() and Right() functions.

At the same point something along the lines of Mid() would be just as good!

Iv done lots of searching for this, but somehow it seems that nothing will actually return x number of chars and I'm sure that there must be a way to do this.

Please note that I'm using Boa Constructor and Python - I don't know if this will make any difference or not (I cant see how for this).

regards

Max

---

### Post by y-lee on 2008-10-28
String slicing in python is similar to list slicing. Consider:
 
```

>>> a = "hello world"
>>> b = a[-3:]
>>> print b
rld
>>> b = a[:3]
>>> print b
hel
>>> b = a[3:9]
>>> print b
lo wor
```

---

### Post by MaxVK on 2008-10-28
Ahh! Its always so easy once you see it!

Very many thanks

regards

Max

---

