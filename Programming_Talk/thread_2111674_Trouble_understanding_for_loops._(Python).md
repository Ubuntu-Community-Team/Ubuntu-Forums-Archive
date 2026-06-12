---
title: "Trouble understanding for loops. (Python)"
date: 2013-02-02
forum: Programming Talk
---

### Post by horizons187 on 2013-02-02
So I understand that a for loop will do something for each something in a list but is the first variable you pick for the loop completely arbitrary? For example:

[PHP]
a = [1, 2, 3]
for i in a
     print(i)
[/PHP]

is the I completely arbitrary and made up? Meaning it could be any variable there?

---

### Post by Bachstelze on 2013-02-02
Any variable that is not already in use, yes.

---

### Post by lavinog on 2013-02-02
Don't forget you need a colon at the end of the for line:
[php]
a = [1, 2, 3]
for i in a:
     print(i)
[/php]

You can replace 'i' with any variable name you want.
You might see that i is used a lot in examples because it is common to use it to represent an index or iterator.

---

### Post by iMac71 on 2013-02-03
Variable names should be sufficiently clear for allowing people, who read the source code, to understand the meaning (and consequentially the purpose) of each variable.
A single letter variable name may be used as index, e.g. in mathematics programs to indicate a specific element of a vector, but it is generally preferable to use longer variable names, for the reason above explained.
Each programming language has its own rules about variable names: for Python, you might read the [PEP 8](http://www.python.org/dev/peps/pep-0008/#naming-conventions)

---

### Post by greenpeace on 2013-02-03
> **horizons187 said:**
> is the I completely arbitrary and made up? Meaning it could be any variable there?

Yes, in the same way that assigning names for your variables at any point in your code is arbitrary.

```
a = 1
banana = 2
charles = 3
```

Just make sure it's clear to the person reading it (which could be you in 6 months time!) what it is used for.  Programs full of a=1, tr=32, vfm=2 can be very difficult for someone else to follow.

---

### Post by AstroLlama on 2013-02-03
you could even use a word:
```
for item in list:
     print(item)
```

---

### Post by horizons187 on 2013-02-04
Thank you all so much for the replies.

---

