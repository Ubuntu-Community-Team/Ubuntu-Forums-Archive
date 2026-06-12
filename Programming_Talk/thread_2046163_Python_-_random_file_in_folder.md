---
title: "Python - random file in folder"
date: 2012-08-22
forum: Programming Talk
---

### Post by SelbyRowleyCannon on 2012-08-22
I have a function that moves into a directory, but it needs to pick a random file within that folder. Does anyone know how to do that?

EXTRAS WHICH WOULD BE PREFERABLE:
~Cross Platform
~Picks file, not folders

---

### Post by MadCow108 on 2012-08-22
```
import os
import random

random.choice([x for x in os.listdir("path") if os.path.isfile(x)])
```

---

### Post by SelbyRowleyCannon on 2012-08-22
> **MadCow108 said:**
> ```
import os
import random

random.choice([x for x in os.listdir("path") if os.path.isfile(x)])
```
Thanks, but could you explain exactly how this works?

---

### Post by MadCow108 on 2012-08-22
you could just look in the documentation.
[http://docs.python.org/library/random.html](http://docs.python.org/library/random.html)
[http://docs.python.org/library/os.html](http://docs.python.org/library/os.html)

the only thing "special" is the "list comprehension":

```
res = [x for x in sequence if condition(x)]
```
is shorthand for
```
res = []
for x in sequence:
  if condition(x):
    res.append(x)
```

note that you'll get an IndexError from random.choice if the directory does not contain any files

---

### Post by SelbyRowleyCannon on 2012-08-22
> **MadCow108 said:**
> you could just look in the documentation.
[http://docs.python.org/library/random.html](http://docs.python.org/library/random.html)
[http://docs.python.org/library/os.html](http://docs.python.org/library/os.html)

the only thing "special" is the "list comprehension":

```
res = [x for x in sequence if condition(x)]
```is shorthand for
```
res = []
for x in sequence:
  if condition(x):
    res.append(x)
```note that you'll get an IndexError from random.choice if the directory does not contain any files

So try / except IndexError is the only other thing, right?

---

### Post by MadCow108 on 2012-08-22
you can also get OSError and IOError as you are dealing with the operating system and the disk.
MemoryError is also possible if you are starved for memory.

---

### Post by SelbyRowleyCannon on 2012-08-22
> **MadCow108 said:**
> you can also get OSError and IOError as you are dealing with the operating system and the disk.
MemoryError is also possible if you are starved for memory.

OK I'll deal with those as well
Thanks

---

