---
title: "Help with Python imports"
date: 2009-11-25
forum: Programming Talk
---

### Post by bostonaholic on 2009-11-25
I've been searching around the web and I can't find a solution.

I have a Python project and in one module I need to import a module that is "side-by-side" with the current module.  How do I import it?  Here's my directory structure.

```
bin
  py
    A\
     __init__.py
     a.py
    B\
     __init__.py
     b.py
    C\
     __init__.py
     c.py
```

So, from within a.py, how would I import b.py?  Thanks.

---

### Post by 0cton on 2009-11-25
[http://www.python.org/dev/peps/pep-0328/#guido-s-decision](http://www.python.org/dev/peps/pep-0328/#guido-s-decision)

It should be 
from ..B import b (I think)

---

### Post by bostonaholic on 2009-11-25
> **0cton said:**
> [http://www.python.org/dev/peps/pep-0328/#guido-s-decision](http://www.python.org/dev/peps/pep-0328/#guido-s-decision)

It should be 
from ..B import b (I think)

That didn't seem to work, here's my error
```
Traceback (most recent call last):
  File "a.py", line 10, in <module>
    from ..B import b
ValueError: Attempted relative import in non-package
```

---

### Post by falconindy on 2009-11-25
Append the "root" to the path using:
```
import sys
sys.path.append('/bin/py')
```
Then you can use syntax similar to java to import libraries:
```
import B.b
```

Source: [http://docs.python.org/tutorial/modules.html#packages](http://docs.python.org/tutorial/modules.html#packages)

---

### Post by bostonaholic on 2009-11-25
> **falconindy said:**
> Append the "root" to the path using:
```
import os
os.path.append('/bin/py')
```
Then you can use syntax similar to java to import libraries:
```
import B.b
```

Source: [http://docs.python.org/tutorial/modules.html#packages](http://docs.python.org/tutorial/modules.html#packages)

os.path.append doesn't exist.  I'm using Python 3.1.1 btw.

```
Traceback (most recent call last):
  File "a.py", line 11, in <module>
    os.path.append('/bin/py')
AttributeError: 'module' object has no attribute 'append'
```

---

### Post by raffaele181188 on 2009-11-25
Last solution didn't work for me neither... Maybe sys.path
> 
Note that both explicit and implicit relative imports are based on the name of the current module. Since the name of the main module is always "__main__", modules intended for use as the main module of a Python application should always use absolute imports.

so if you run a.py directly you can't use relative imports. You can set the env PYTHONPATH or work with absolute imports (append to sys.path)
[A similar problem on StackOverflow]("http://stackoverflow.com/questions/72852/how-to-do-relative-imports-in-python"), but it also tells about a 2.6 change...

---

### Post by falconindy on 2009-11-25
Oops, it is sys.path.append.

---

### Post by bostonaholic on 2009-11-25
> **falconindy said:**
> Oops, it is sys.path.append.

That didn't work either but I got it figured out...kinda.

So, again here's my structure
```
bin
  py
    __init__.py
    control.py
    A\
     __init__.py
     a.py
    B\
     __init__.py
     b.py
    C\
     __init__.py
     c.py
```

It turns out that running a.py will not import B.b successfully when using import B.b.  But when I use bin/py/control.py and import A.a, the B.b import within A.a will work.  Confusing enough?

**Example**

A.a
```
import B.b
```
bin/py/control.py
```
import A.a
```
This successfully imports A.a as well as inherently importing B.b (from A.a code).

Luckily, in my code I will only be using a.py from within control.py and will never be calling a.py alone (other than testing).

---

