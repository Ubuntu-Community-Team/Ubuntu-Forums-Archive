---
title: "PyGTK and freeze - dynamic module problem"
date: 2007-04-02
forum: Programming Talk
---

### Post by samjh on 2007-04-02
I'm having a go at learning Python.  After doing the basic tutorials, I've dived head-first into using PyGTK.

So far so good... as long as I stay in Python's interpreted environment.  My first PyGTK program runs perfectly!

But when I use the freeze utility to make my PyGTK program self-executable, it builds fine, but doesn't run.

Upon trying ./helloworld

I get...

```
Traceback (most recent call last):
  File "helloworld.py", line 7, in ?
    import gtk
  File "/var/lib/python-support/python2.4/gtk-2.0/gtk/__init__.py", line 38, in ?
    import gobject as _gobject
  File "/var/lib/python-support/python2.4/gtk-2.0/gobject/__init__.py", line 30, in ?
    from _gobject import *
SystemError: dynamic module not initialized properly
```

Previously I found that the _gobject.so file had to be copied to my executable's directory, since it is linked dynamically.  But what's this thing about "not initialized properly"?

---

