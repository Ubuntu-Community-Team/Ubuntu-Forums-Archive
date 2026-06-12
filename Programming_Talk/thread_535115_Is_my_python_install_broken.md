---
title: "Is my python install broken?"
date: 2007-08-26
forum: Programming Talk
---

### Post by triptoe on 2007-08-26
I have a pretty simple program
```
import random

for i in range(10):
  x = random.random()
  print x 
```

here is the output:

```
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 30, in apport_excepthook
    import apport.report, apport.fileutils
  File "/var/lib/python-support/python2.5/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/var/lib/python-support/python2.5/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
  File "/usr/lib/python2.5/tempfile.py", line 33, in <module>
    from random import Random as _Random
  File "/home/notig/random.py", line 7, in <module>
    x = random.random()
TypeError: 'module' object is not callable

Original exception was:
Traceback (most recent call last):
  File "random.py", line 1, in <module>
    import random
  File "/home/notig/random.py", line 7, in <module>
    x = random.random()
TypeError: 'module' object is not callable

```

---

### Post by ghostdog74 on 2007-08-26
check to make sure you don't have a random.py (that you made) in the folder you are currently in.

---

### Post by Smygis on 2007-08-26
**/home/notig/random.py**


NEVER name your apps the same as official python modules.

---

### Post by triptoe on 2007-08-26
:oops:

---

### Post by jfinkels on 2007-08-26
> **triptoe said:**
> :oops:

Best response post ever.

---

### Post by Note360 on 2007-08-26
that was good. DOnt worry happens to every one. You can just prepend it if you want (eg I would do cwrandom (my initials)) or I would come up wiht a wise *** name (like how Why names his ruby modules). For example for somethign like this I might call it... tossup, tosser, russianroulette, or some other very random, annoying and hard to figure out name.

---

