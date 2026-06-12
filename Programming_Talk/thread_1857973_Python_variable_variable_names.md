---
title: "Python variable variable names"
date: 2011-10-11
forum: Programming Talk
---

### Post by Michaël-D on 2011-10-11
Hi all,

is there a way to make python variable names variable (compose them out of different variables)?

an example:

so that
```
var = 1
("string", var) = "variable value"
print string1
```gives
```
variable value
```is this possible (and how...)?

thx in advance,

M.

---

### Post by karlson on 2011-10-11
> **Michaël-D said:**
> Hi all,

is there a way to make python variable names variable (compose them out of different variables)?

an example:

so that
```
var = 1
("string", var) = "variable value"
print string1
```gives
```
variable value
```is this possible (and how...)?

thx in advance,

M.

Is there a reason to use reference by name instead of a list/array?

I don't think Python something like Perl reference by name.

---

### Post by Erdaron on 2011-10-11
I can't think of a way to do exactly what you want, but at least there is a workaround using dictionary keys. Since the keys can be any string, it's kind of like a variable with a variable name?
```
>>> a = {}
>>> a['eek' + 'whoa'] = 1
>>> a['eekwhoa']
1
```

The name of the dictionary stays fixed, of course.

---

### Post by ofnuts on 2011-10-11
> **Michaël-D said:**
> Hi all,

is there a way to make python variable names variable (compose them out of different variables)?

an example:

so that
```
var = 1
("string", var) = "variable value"
print string1
```gives
```
variable value
```is this possible (and how...)?

thx in advance,

M.See the various forms of the ***exec()*** built-in:
```

>>> exec('%s=%d' % ('x',12345))
>>> print x
12345

```

---

### Post by Tony Flury on 2011-10-11
If i had to do this, I would go with a dictionary, either one you construct yourself, or you can access the dictionaries which are built that contain the locals, globals, and instance varibales (__locals__, __globals__ and <instance>.__dict__) I think. 
Note : I think they are the right names (but i might be wrong - I don't have python on this PC).

---

