---
title: "Python bytecode questions"
date: 2010-12-08
forum: Programming Talk
---

### Post by nolag on 2010-12-08
I know python generates intermediate bytecode to speed up execution after the 1st time.  I can't remember where these files are.  I am wondering if I can give those instead of (or with) the source so it can run faster.  Also does anyone know how python byte code compare in speed to Java bytecode?  I know Java is faster, but they say that mostly because of the lexing and parsing times, if it is already bytecode how does it compare?

---

### Post by skirkpatrick on 2010-12-08
They (.pyc files) are stored in the same directory as the .py files.  It is my understanding that Python compares the date of the .py file to the .pyc file and does a recompile if the .py is newer.  I believe it will run the .pyc if that is all that is available.  If so, it will also make it more difficult for someone to modify the code.  Not for somebody determined but the casual user.

---

### Post by Quikee on 2010-12-08
Distributing intermediate python bytecode makes only sense if you don't want to reveal the source. Otherwise it makes no sense to distribute the bytecode as it will only shave of a fraction of a second for the user when he starts the program for the first time. 

Comparing Python bytecode with Java bytecode also does not mean much as the execution speed of both is not dependent much on the bytecode itself but on the interpreting (mind also that python is a dynamically typed language and the interpreter must do additional runtime checks which are not needed for a statically typed language like Java as they can be done at compilation) or "just in time" compilation of the code and how good the interpretation and/or the generated code is. Java has one of the most optimized virtual machines currently available (todays problem with Java is mostly memory consumption). The "official" CPython does not have "just in time" compilation and just interprets the code.
 
On the other hand, Python is easier to integrate with C which makes it possible to write parts of code that need to be fast in C. In facts some libraries in python standard library are written in C (or have a C implmementation alternative) to be faster.

---

### Post by nolag on 2010-12-09
Thank you both for your replies, you have answered my questions :).

---

### Post by juancarlospaco on 2010-12-09
```

#!/usr/bin/env python
# -*- coding: utf-8 -*-
#
try:
    import psyco  # Speed Up if avaliable
    psyco.full()
except ImportError:
    print(" ")
    print(" No PYTHON-PSYCO avaliable, this application will run slower... ")
    print(" ")
    pass
```

:)

---

