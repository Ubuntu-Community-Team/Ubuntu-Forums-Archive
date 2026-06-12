---
title: "end=' '...please explain"
date: 2013-01-25
forum: Programming Talk
---

### Post by Taz2012 on 2013-01-25
Okay new to programming and am using python and keep seeing (end=' ') as arguments within print functions what exactly does end=' ' mean.

---

### Post by sffvba[e0rt on 2013-01-25
*Thread moved to **Programming Talk**.*


404

---

### Post by Bachstelze on 2013-01-25
[http://docs.python.org/3/library/functions.html#print](http://docs.python.org/3/library/functions.html#print)

---

### Post by micahpage on 2013-01-26
python3.x print is a function. This function has the argument end, which is defaulted to a newline, '\n'. So when you execute print() it gives a newline. If you do not want to use a newline, you could change the argument end='' for example, to end in nothing so to speak.

so print could be "somewhat" the equivalent to:
```
import sys

def myprint(stringer='', end='\n'):
    sys.stdout.write(stringer + end)
```

---

