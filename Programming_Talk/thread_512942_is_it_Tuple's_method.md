---
title: "is it Tuple's method ?"
date: 2007-07-29
forum: Programming Talk
---

### Post by mocqueanh on 2007-07-29
x = ([0,1], 2)
x[0][1] = 'Python'

I've cheat Python, right ?:confused:

---

### Post by Jessehk on 2007-07-29
> **mocqueanh said:**
> x = ([0,1], 2)
x[0][1] = 'Python'

I've cheat Python, right ?:confused:

As far as I understand it the structure of the tuple itself is constant, not the objects contained within it.

---

### Post by pmasiar on 2007-07-30
> **mocqueanh said:**
> x = ([0,1], 2)
x[0][1] = 'Python'


try type(x[0]): x[0] is a list. You would be surprised if you could not change a list? If you do instead:

z = ((0,1), 2) 

you see you cannot assign to the tuple:

z[0][1] = 's' # this fails: TypeError: 'tuple' object does not support item assignment

---

