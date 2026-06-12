---
title: "Python, Tkinter, and AttributeErrors"
date: 2011-09-30
forum: Programming Talk
---

### Post by Jack Ryan on 2011-09-30
I'm running Ubuntu 10.10, and python 2.6 and ran into the following issue when working with Tkinter.

I import the module, create a window, but when I try and create a button, label, or entrybox, I get the following error:

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.6/lib-tk/Tkinter.py", line 2005, in __init__
    Widget.__init__(self, master, 'button', cnf, kw)
  File "/usr/lib/python2.6/lib-tk/Tkinter.py", line 1926, in __init__
    BaseWidget._setup(self, master, cnf)
  File "/usr/lib/python2.6/lib-tk/Tkinter.py", line 1906, in _setup
    if cnf.has_key('name'):
AttributeError: 'str' object has no attribute 'has_key'
 

Is there something wrong with my particular version of Tkinter or what? I followed the same tutorial with 10.04 with no problems. Any ideas would be greatly appreciated.

---

### Post by Smart Viking on 2011-09-30
Include your code in CODE tags, then we can test the code and try to fix it.
Always include code.

---

### Post by Jack Ryan on 2011-09-30
I just realized that the tutorial I was following contained an error. Thanks, anyway.

---

