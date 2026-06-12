---
title: "[SOLVED] Errrr... where are the python libraries?"
date: 2007-07-04
forum: Programming Talk
---

### Post by sixfoottallrabbit on 2007-07-04
Yeah, sorry... you probably get annoyed with the amount of Python questions on here.

I was just wondering where the libraries are stored though? Like time.py

I want to have a look at them.

Thanks.

---

### Post by pmasiar on 2007-07-04
on Linux, try command 'locate filename'

---

### Post by sixfoottallrabbit on 2007-07-04
> **pmasiar said:**
> on Linux, try command 'locate filename'

Wow. I'm amazed the search works so quickly. Anyway, I found out it's actually called time.so

How do I read a .so file? Is it even possible?

Thanks.

---

### Post by ButteBlues on 2007-07-04
```
import 'time'
```

---

### Post by sixfoottallrabbit on 2007-07-04
You know I don't just want to import it, right?

I want to be able to read it.

Anyway:
```
>>> import "time"
  File "<stdin>", line 1
    import "time"
                ^
SyntaxError: invalid syntax
```

---

### Post by foo-bar on 2007-07-04
'time.so' is a compiled file.  In order to view the contents of the built in time module in Python, you would probably have to download the python source.

---

### Post by Smygis on 2007-07-04
[http://svn.python.org/view/python/trunk/Modules/timemodule.c?rev=54606&view=markup](http://svn.python.org/view/python/trunk/Modules/timemodule.c?rev=54606&view=markup)

---

### Post by sixfoottallrabbit on 2007-07-04
Ohhh it's compiled from C! Thanks a lot!

=D

Case closed...

---

