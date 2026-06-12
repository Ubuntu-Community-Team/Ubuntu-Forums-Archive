---
title: "python program"
date: 2009-01-21
forum: Packaging and Compiling Programs
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

### Post by tabor on 2009-01-28
Use x = input("entre x value")

instead of raw_input, and your program will work.  The problem is that with raw_input it will keep the number as a string, instead of an integer.

---

### Post by Taidgh on 2009-01-28
Or alternatively, int(x).

---

