---
title: "Recursion in Python"
date: 2009-11-02
forum: Programming Talk
---

### Post by blazemore on 2009-11-02
I need some help implementing the following as a Python (Or anything really) function. 
```

myLuc(0) = 0
myLuc(1) = 1
myLuc(n) = 3 × myLuc(n &#8722; 1) &#8722; myLuc(n &#8722; 2) if n > 1

```

Can anyone do this, in python or a c-like pseudocode?

---

### Post by Paul Miller on 2009-11-02
This sounds distressingly like a homework assignment, but I'm going to assume it's not.

In Python:

[php]
def myLuc (n):
    if n == 0 or n == 1: return n
    else: return 3 * myLuc (n-1) - myLuc (n-2)
[/php]

will do the right thing assuming n is a positive integer.  However, it will be very slow.

---

### Post by blazemore on 2009-11-02
Actually I'm just teaching myself Python.

---

### Post by fiddler616 on 2009-11-02
> **blazemore said:**
> Actually I'm just teaching myself Python.
Why don't you get a tutorial?

---

### Post by fiddler616 on 2009-11-02
> **blazemore said:**
> c-like pseudocode?
> Actually I'm just teaching myself Python. 
??

---

### Post by blazemore on 2009-11-02
I just needed the logic. I know the Python syntax.

---

### Post by Arndt on 2009-11-03
> **blazemore said:**
> I just needed the logic. I know the Python syntax.

My first thought was that what you wrote in the first post already was perfectly clear pseudo-code.

---

### Post by blazemore on 2009-11-03
It was that "if n > 1" at the end. I understand it now.

---

