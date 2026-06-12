---
title: "Pylab in IDLE 2.7"
date: 2012-05-09
forum: Programming Talk
---

### Post by layolayo on 2012-05-09
Hi,

Just wondering if anyone knows why I cannot import pylab modules from a *.py file, but can direct from IDLE interface or from terminal?

TERM:-
```
>>> from pylab import *
>>> plot([1,2,3,4])
[<matplotlib.lines.Line2D object at 0x3f2f610>]
>>> show()
```

Running same code in IDLE from pylab.py
```
Traceback (most recent call last):
  File "/home/layolayo/Documents/Python Projects/pylab.py", line 1, in <module>
    from pylab import *
  File "/home/layolayo/Documents/Python Projects/pylab.py", line 2, in <module>
    plot([1,2,3,4])
NameError: name 'plot' is not defined
```

Thanks

Layolayo

---

### Post by cgroza on 2012-05-09
The name of your file is identical to the one of the module. When you try to import, python chooses the one in the current directory. Try renaming your file to a different name.

---

### Post by layolayo on 2012-05-10
You're a star! Thank you

---

