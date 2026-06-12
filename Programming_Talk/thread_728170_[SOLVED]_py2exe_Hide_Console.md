---
title: "[SOLVED] py2exe Hide Console"
date: 2008-03-18
forum: Programming Talk
---

### Post by themusicwave on 2008-03-18
I'm using Py2Exe to turn a python program into a Windows exe.  I know this is probably not a popular idea, but I have to do it since I cannot be sure the computer will have python on it.

Rest assured that the first thing that this exe does is install python 2.5 and setup the python path environment variable.  This way in the future I can assume python will be there!

Anyways, the problem is that even though it's a GUI App built on TK, it still shows the console when compiled with Py2Exe.  I even tried changing the extensions to .pyw

Any ideas?  I know most of us don't like Windows XP, but sadly my employer does not share that feeling...

---

### Post by Quikee on 2008-03-18
I had the same problem today (however I was using pygtk). I changed app.py to app.pyw and modify the "setup.py" py2exe script from:

[PHP]from distutils.core import setup
import py2exe
setup(console=['app.py'])[/PHP]

to:

[PHP]from distutils.core import setup
import py2exe
setup(windows=['app.py'])[/PHP]

I hope it helps.

---

### Post by themusicwave on 2008-03-19
That worked, thanks!

---

