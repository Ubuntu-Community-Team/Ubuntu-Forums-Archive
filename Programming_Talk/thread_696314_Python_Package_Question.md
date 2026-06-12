---
title: "Python Package Question"
date: 2008-02-13
forum: Programming Talk
---

### Post by euler_fan on 2008-02-13
I'm trying to write a python package and have been reading the python tutorial, etc about doing so.

I have a directory, wavepack/ with one module and an _init_.py file, and two folders (filters, measures) each with their own _init_.py file.

If the _init_.py files contain anything, they contain a statement
```
_all_ = ["module1","module2"]
```

After running
```
import sys
sys.path.append('/path/to/one/up/from/wavepack')
```

I run

```
import wavepack
```

and get this error:

```
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named wavepack

```

Any help would be great. I can import the individual modules one by one, but this will get progressively less practical as I add more modules.

Thanks in advance,

EF

---

### Post by cyberbuff on 2008-02-14
> I have a directory, wavepack/ with one module
is wavapack a .py file?

---

### Post by euler_fan on 2008-02-14
> **cyberbuff said:**
> is wavapack a .py file?

wavepack is a folder. It has an _init_.py file and a module called generic.py in it along with two other folders each with their own _init_.py files and other modules therein.

EF

---

