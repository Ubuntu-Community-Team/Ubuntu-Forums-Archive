---
title: "Embedding Python in a Pidgin plugin - linking issues"
date: 2008-10-17
forum: Programming Talk
---

### Post by klange on 2008-10-17
Alright, in order to write a protocol plugin for libpurple I'm trying to use Python's C API to embedded quite a bit of Python into a plugin for Pidgin, but I'm having some issues when I go to run it. Specifically, the issue described [here](http://docs.python.org/extending/embedding.html#linking-requirements) (when I try to import anything in the embedded Python, I get a Python stack trace saying some Python C function symbol was undefined). The real problem is I have no idea where I need to make these changes to the build. I've pretty much added the arguments everywhere in building just the plugin, do I have to go all the way and recompile libpurple and Pidgin like this? I'm quite confused at what's happening here. The same code when not made into a Pidgin plugin runs fine.

Can someone help me out?

```
**$ pidgin**
Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "/usr/lib/python2.5/asyncore.py", line 49, in <module>
    import select
ImportError: /usr/lib/python2.5/lib-dynload/select.so: undefined symbol: PyExc_ValueError
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 38, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.5/site-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.5/site-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
  File "/usr/lib/python2.5/subprocess.py", line 401, in <module>
    import select
ImportError: /usr/lib/python2.5/lib-dynload/select.so: undefined symbol: PyExc_ValueError

Original exception was:
Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "/usr/lib/python2.5/asyncore.py", line 49, in <module>
    import select
ImportError: /usr/lib/python2.5/lib-dynload/select.so: undefined symbol: PyExc_ValueError

```
(Pidgin then continues to load without my plugin)

---

### Post by klange on 2008-10-18
Been a day, I'm a few pages back... ***bump***

I'd really like to get this working so I can finally port my protocol to something useful.

---

### Post by iPAS on 2010-11-16
Yep. I got this problem on plugin development too. While running, it shown that ... 

> Error: undefined symbol: Py_GetPath
Check the plugin website for an update.

---

