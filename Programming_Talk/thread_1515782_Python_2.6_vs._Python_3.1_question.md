---
title: "Python 2.6 vs. Python 3.1 question"
date: 2010-06-22
forum: Programming Talk
---

### Post by xb12x on 2010-06-22
Python 2.6.5 (r265:79063, Apr 16 2010, 13:57:41) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>>
>>> numbers = range(1, 11, 3)
>>> print(numbers)
[1, 4, 7, 10]
>>> 

Python 3.1.2 (r312:79147, Apr 15 2010, 15:35:48) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>>
>>> numbers = range(1, 11, 3)
>>> print(numbers)
range(1, 11, 3)
>>> 

How can I get python3.1 to output '[1, 4, 7, 10]' instead of 'range(1, 11, 3]'

Thanks

---

### Post by wmcbrine on 2010-06-22
Just put a "list()" around it.

Python 3's "range" == Python 2's "xrange".

---

