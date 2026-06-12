---
title: "What is the correspondent of Jar in python"
date: 2009-10-26
forum: Programming Talk
---

### Post by hoboy on 2009-10-26
In java when I need an api I will put the jar file that contains the api in my classpath.
I do I do the same in python ?
For example if i am using python shell of python 3.1
and I want to use a module that python 3.1 does not contains how to I ipmor the module in to it ?

---

### Post by snova on 2009-10-26
> **hoboy said:**
> In java when I need an api I will put the jar file that contains the api in my classpath.
I do I do the same in python ?
For example if i am using python shell of python 3.1
and I want to use a module that python 3.1 does not contains how to I ipmor the module in to it ?

Add the directory containing the module/package to the $PYTHONPATH environment variable.

---

### Post by iblis on 2009-10-26
The PYTHONPATH environment variable works, however often I try to avoid messing with a shell, so I do something like this:

```
import sys

other_dirs = (
    '/usr/local/codebase/somedir',
    '/usr/local/codebase/someotherdir',
    '/path/to/yet/more/code',
)

for dir in other_dirs:
    if dir not in sys.path:
        sys.path.insert(0,dir)

```

It seems to work fine for bootstrapping the environment from within a python application.

---

### Post by diesch on 2009-10-26
Python has [eggs](http://peak.telecommunity.com/DevCenter/PythonEggs).

---

