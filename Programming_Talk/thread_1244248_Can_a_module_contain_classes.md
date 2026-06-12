---
title: "Can a module contain classes?"
date: 2009-08-19
forum: Programming Talk
---

### Post by colau on 2009-08-19
cat call.py
```

#!/usr/bin/python

class cl:
	def abc(a,b):
		........
	def abd(a,b):
		........
	def abg(a,b):
		.......

```
from call import abc

---

### Post by DaithiF on 2009-08-19
Yes, a module can contain classes.

(where else could a class be contained?)

you can't however import a method of a class, like you try below.  Instead you import the class, create an object of that class, and run the method on that object.

from call import c1
myobject = c1          # create an instance of class c1
myobject.abc()         # call method abc on myobject

also, your class methods need a parameter representing their parent object:
def abc(self):
    # do something

---

### Post by colau on 2009-08-19
Is it possible to import classes without using [COLOR="Red"]from[/COLOR]?
As it's possible to import the file and then using the functions of that file.

[COLOR="SeaGreen"]import file
......using functions....[/COLOR]

---

### Post by DaithiF on 2009-08-19
sure, you just need to include the module name when referencing the class.

import call
x = call.c1
x.abc()

---

### Post by colau on 2009-08-19
Thank you.

---

### Post by nvteighen on 2009-08-19
In Python classes also act as namespaces... moreover, it is the only way to use namespaces in Python :p

---

### Post by CptPicard on 2009-08-19
> **nvteighen said:**
> In Python classes also act as namespaces... moreover, it is the *only way* to use namespaces in Python :p

:confused:

Modules... nested modules...?

---

### Post by abhilashm86 on 2009-08-19
basically packages and modules are defined as containers of classes, each module performs its own task like input or loading or message passing........

---

