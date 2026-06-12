---
title: "sqrt: 3^3 (python)"
date: 2006-06-11
forum: Programming Talk
---

### Post by Ubuntuud on 2006-06-11
Hi,
I learned math in Dutch, so until a short while I didn't even know about sqrt, in the Netherlands it's standard to write... a sign that I can't find in OOo's special characters list. So my question might be stupid.

If you do:

x = 3
y = x^3

How can I get back to 3 from y (if I don't know x, only y (27)). I used to write the... "sign"... with a tiny 3 in front of it. How can you do this with sqrt (in python).

Hope you can understand my question, if not please say so.
Thanks in advance!

---

### Post by Hanj on 2006-06-11
One way is to write y**(1.0/3.0), but there's probably a more elegant way.

---

### Post by Ubuntuud on 2006-06-11
OK. Thanks. I'll use that until a more elegant one turns up.

---

### Post by Hikaru79 on 2006-06-11
In english, this is called a "cube root". In general, it is the "nth root" for some number n.  There is no built-in method in Python to calculate roots beyond 2 (sqrt), but it is trivial to implement one yourself:
```
>>> import math
>>> def nroot(x, n):
...     return math.pow(x, 1.0/n)
...
>>> nroot(8,3)
2.0
``` There's really no more "elegant" way to do this, it is enough.

---

### Post by Ubuntuud on 2006-06-12
OK. Thanks alot!

---

### Post by wmcbrine on 2006-06-14
[QUOTE=Ubuntuud]I learned math in Dutch, so until a short while I didn't even know about sqrt, in the Netherlands it's standard to write... a sign that I can't find in OOo's special characters list.[/QUOTE]Something like this?

[IMG]http://upload.wikimedia.org/math/f/e/b/feb3e57da7b041973a0105adbfe5a95e.png[/IMG]

---

### Post by bieber on 2006-06-15
Yeah, that's the standard math notation for a root, and I don't think it changes between countries.  sqrt is just an abbreviation for what we call the symbol in English; square root.

---

