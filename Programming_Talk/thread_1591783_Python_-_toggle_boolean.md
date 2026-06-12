---
title: "Python - toggle boolean"
date: 2010-10-09
forum: Programming Talk
---

### Post by kroq-gar78 on 2010-10-09
is there an easy way to toggle a boolean in python, like
```
bool1 = !bool1
```
?

Thanks in advance.

---

### Post by unknownPoster on 2010-10-09
```


Python 2.6.5 |EPD 6.2-2 (32-bit)| (r265:79063, May 28 2010, 15:13:03) 
[GCC 4.0.1 (Apple Inc. build 5488)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> b = True
>>> print not b
False
>>> b = not b
>>> print b
False

```

literally:

```

bool = not bool

```

---

### Post by MadCow108 on 2010-10-09
bool1 = not bool1

---

### Post by kroq-gar78 on 2010-10-09
thanks for the fast responses! works like a charm!

---

### Post by takeda on 2012-03-21
Discovered this today, but am still posting it in case someone searching on the web will be looking for it.

Alternative solution to toggling the boolean:

```
b ^= True
```

example:

```
Python 2.7 (r27:82500, Aug 07 2010, 16:54:59) [GCC] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> b = True
>>> b ^= True; b
False
>>> b ^= True; b
True
>>> b ^= True; b
False

```

---

