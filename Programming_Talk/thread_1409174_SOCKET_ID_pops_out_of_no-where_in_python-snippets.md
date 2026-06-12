---
title: "SOCKET ID pops out of no-where in python-snippets"
date: 2010-02-17
forum: Programming Talk
---

### Post by Flimm on 2010-02-17
I'm trying to add a Python snippet to PyGTK section of Python snippets. You can get the branch I'm using by running: ```
bzr branch lp:python-snippets
```

For some reason, whenever my script throws an exception, "SOCKET ID= #number#" is printed and a window is displayed. Only when I close that new window will the exception's stack trace be printed to the terminal as normal.

What I can't understand is why I don't get the same behaviour in any other directory, say my home directory. I only get the weird behaviour in python-snippets/pygtk. I wondered if perhaps a .py file was overriding a system default, but I only import gtk and sys in this test script, and neither gtk.py or sys.py exist in the directory.

Here's the test script:
[php]#!/usr/bin/env python

import gtk
import sys
win = gtk.Window()
win.connect("destroy", lambda a:sys.exit())
button = gtk.Button("exception")
def exp(widget): 1 / 0
button.connect("clicked", exp)
win.add(button)
win.show_all()
gtk.main()
[/php]
I run the script by typing "python mytest.py" in the terminal.
I get the weird behaviour when I click on the button, and this terminal output:
```
(mytest.py:4582): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(mytest.py:4582): atk-bridge-WARNING **: IOR not set.

(mytest.py:4582): atk-bridge-WARNING **: Could not locate registry
Socket ID= 171966548
Traceback (most recent call last):
  File "mytest.py", line 8, in exp
    def exp(widget): 1 / 0
ZeroDivisionError: integer division or modulo by zero
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
  File "/usr/lib/python2.6/urllib.py", line 844, in <module>
    class ftpwrapper:
  File "/usr/lib/python2.6/urllib.py", line 848, in ftpwrapper
    timeout=socket._GLOBAL_DEFAULT_TIMEOUT):
AttributeError: 'module' object has no attribute '_GLOBAL_DEFAULT_TIMEOUT'

Original exception was:
Traceback (most recent call last):
  File "mytest.py", line 8, in exp
    def exp(widget): 1 / 0
ZeroDivisionError: integer division or modulo by zero

```
It seems like Apport's excepthook has got something to do with it, but I can't understand why it's treating this directory differently from other directories.
This is the output I get if I run the exact same script moved to my home directory:
```
(mytest.py:4605): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(mytest.py:4605): atk-bridge-WARNING **: IOR not set.

(mytest.py:4605): atk-bridge-WARNING **: Could not locate registry
Traceback (most recent call last):
  File "mytest.py", line 8, in exp
    def exp(widget): 1 / 0
ZeroDivisionError: integer division or modulo by zero

```

(A few minutes later)
As I was typing this, I realised that socket.py existed in python-snippets/pygtk, and Apport was importing it. A rename of socket.py fixed the problem.

I guess the question now is: is this a bug in python-snippets or Apport?

---

