---
title: "undefined symbol: XtManageChild"
date: 2010-10-20
forum: Programming Talk
---

### Post by ladasky on 2010-10-20
Hi folks,

I've just downloaded a package for Python called pymacs.  This is NOT the application which establishes a link between Python and the EMACS editor.  There's another application with the same name (unfortunately).  The pymacs that I mean is an application which links Python to the molecular dynamics package GROMACS.  It is found [here]("http://wwwuser.gwdg.de/~dseelig/pymacs.html").
 
Anyway, pymacs is installed with a *sudo python setup.py install*.  The first time I tried to do this, I got an error message from ld, which said I was missing a file called lfftw3f.  I found this puzzling at first, since I had already installed libfftw3.  I did some searching and determined that the missing file was in fact in libfftw3-dev.  So I installed that, and the build completed.
 
When I started my Python interpreter, I got a surprise:
 
```
IDLE 2.6.4      ==== No Subprocess ====
>>> from pymacs import *
Traceback (most recent call last):
  File "<pyshell#0>", line 1, in <module>
    from pymacs import *
  File "/usr/local/lib/python2.6/dist-packages/pymacs/__init__.py", line 23, in <module>
    from molecule import *
  File "/usr/local/lib/python2.6/dist-packages/pymacs/molecule.py", line 37, in <module>
    from atomselection import *
  File "/usr/local/lib/python2.6/dist-packages/pymacs/atomselection.py", line 24, in <module>
    import _pymacs
ImportError: /usr/local/lib/python2.6/dist-packages/pymacs/_pymacs.so: undefined symbol: XtManageChild
```
 
I've never received a build-style error message from inside a Python import call before.
 
I went searching for information on XtManageChild, and it appears to be a function from X windows or Motif.  Well, I already have a few X- and Motif-related packages installed, but there are MANY more of them, and I haven't discovered which one contains XtManageChild.
 
Any guidance would be appreciated!  I've had luck in the past looking at my build error logs and finding missing packages, but this time I can't find the right one.

I'm running Python 2.6 on Ubuntu 9.10, not that it should matter.

---

