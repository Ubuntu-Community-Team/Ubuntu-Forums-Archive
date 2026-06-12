---
title: "python i/o errno2"
date: 2010-03-09
forum: Programming Talk
---

### Post by pmiln099 on 2010-03-09
```
>>> f = open("~/myPy/test.txt", "r")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IOError: [Errno 2] No such file or directory: '~/myPy/test.txt'

```

Why am I getting this error message? I have been running Python scripts successfully for several weeks, no problems. This is the first script I am beginning to write to open a file and do some work on it.

I have searched for an answer without success. I have tried
```
peter@pubuntu:~$ export PYTHONPATH=$PYTHONPATH:~/myPy
```
and this is my PYTHONPATH:
```

>>> import sys
>>> from pprint import pprint as pp
>>> pp(sys.path)
['',
 '/home/peter',
 '/home/peter/myPy',
 '/usr/lib/python25.zip',
 '/usr/lib/python2.5',
 '/usr/lib/python2.5/plat-linux2',
 '/usr/lib/python2.5/lib-tk',
 '/usr/lib/python2.5/lib-dynload',
 '/usr/local/lib/python2.5/site-packages',
 '/usr/lib/python2.5/site-packages',
 '/usr/lib/python2.5/site-packages/Numeric',
 '/usr/lib/python2.5/site-packages/PIL',
 '/usr/lib/python2.5/site-packages/gst-0.10',
 '/var/lib/python-support/python2.5',
 '/usr/lib/python2.5/site-packages/gtk-2.0',
 '/var/lib/python-support/python2.5/gtk-2.0']
```

---

### Post by __init__ on 2010-03-09
> **pmiln099 said:**
> ```
>>> f = open("~/myPy/test.txt", "r")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IOError: [Errno 2] No such file or directory: '~/myPy/test.txt'

```

Why am I getting this error message?

Obviously, because there is no such file or directory :)
Tilda expansion is a *shell* feature and there is no surprise that library functions interpret '~' as a direcory name. You need the os.path.expanduser function. So your code should look like
```

import os
f = open(os.path.expanduser("~/myPy/test.txt"), "r")

```

---

