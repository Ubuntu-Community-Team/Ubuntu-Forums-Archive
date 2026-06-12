---
title: "Can't find Python.h already installed python-dev"
date: 2013-01-27
forum: Programming Talk
---

### Post by zuhl on 2013-01-27
Hi,

I'm a newbie programmer trying to call C functions from Python and when I #include <Python.h> and "gcc spam.c" I get the compiler message, "fatal error: Python.h: No such file or directory compilation terminated"

Of course I Googled the problem and everyone says "sudo apt-get install python-dev" I did this though and I still get the same error message.

Also I tried "find Python.h" and no such file or directory. I even manually looked in /usr/lib/Python2.7 and its not there.

I'm running Ubuntu12.04 and Python2.7.3.  64-bit if it matters.  

Thanks!

---

### Post by MadCow108 on 2013-01-27
python headers in subfolders, normally /usr/include/python2.7 and /usr/include/x86_64-linux-gnu/python2.7
use e.g. python-config to get them:
```
gcc $(python-config --includes) file.c
```

from within python you can get the path with distutils:
```
from distutils.sysconfig import get_python_inc
incdirs = [get_python_inc(), get_python_inc(plat_specific=True)]
```

---

### Post by zuhl on 2013-01-27
You're right.  Python.h is in /usr/include/python2.7 on my machine.

```
incdirs = [get_python_inc(), get_python_inc(plat_specific=True)])
```

gave me a syntax error.

---

### Post by zuhl on 2013-01-27
Adding the correct path, as Mad Cow pointed out, solved the problem.

```
$ C_INCLUDE_PATH=/usr/include/python2.7
$ export C_INCLUDE_PATH
```

Thanks!

---

