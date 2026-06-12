---
title: "compiling python"
date: 2009-01-21
forum: Programming Talk
---

### Post by abhilashm86 on 2009-01-21
i am just starting to learn python,when i complied following conditonal statement,compiler gave error,i just don't find any error here

x=raw_input ('entre x value')

if x%2 == 0:
print x," is even"
else:
print x," is odd"


error by compiler,
abhilash@abhi:~$ python p1.py
entre x value 10
Traceback (most recent call last):
File "p1.py", line 3, in <module>
if x%2 == 0:
TypeError: not all arguments converted during string formatting

---

### Post by eightmillion on 2009-01-21
> **abhilashm86 said:**
> i am just starting to learn python,when i complied following conditonal statement,compiler gave error,i just don't find any error here

x=raw_input ('entre x value')

if x%2 == 0:
print x," is even"
else:
print x," is odd"


error by compiler,
abhilash@abhi:~$ python p1.py
entre x value 10
Traceback (most recent call last):
File "p1.py", line 3, in <module>
if x%2 == 0:
TypeError: not all arguments converted during string formatting

The problem is that raw_input always returns a string. You need to convert it to an int before you can do any math on it. This will fix your code:

```
x=int(raw_input ('entre x value'))

if x%2 == 0:
    print x," is even"
else:
    print x," is odd"
```

---

### Post by abhilashm86 on 2009-01-21
yes thanks,you were correct,by default it was returning a string, i got it

---

### Post by djbushido on 2009-01-21
Also a warning:
watch type conversions, as Python is tricky to debug in this respect. However, remember that in general 'string' is always a string and a plain number or something without quotes is a number.

---

