---
title: "Wrong Python module paths for opencv and others in Lucid"
date: 2010-06-03
forum: Programming Talk
---

### Post by scotty64 on 2010-06-03
I notice some python odds in Lucid when trying to use python-opencv:

>>> import cv

Traceback (most recent call last):
  File "<pyshell#0>", line 1, in <module>
    import cv
ImportError: No module named cv

This should normally import the opencv python module (at least all tutorials for the library do it this way and even the module wiki states:
Starting with release 2.0, OpenCV has a new Python interface. (The previous Python interface is described in SwigPythonInterface.) Some highlights of the new bindings:
    * single import of all of OpenCV using "import cv" 

But....
>>> import opencv
this one at least imports something called opencv.

Anybody had the same problem and solved it ?
How can I fix wrong python module paths in Lucid (there are other modules e.g. SPE that sit in the wrong path)? 

thanks for any help.

---

### Post by scotty64 on 2010-06-05
I think this explains the problem - the python-opencv package just does not work and/or uses the old python bindings that are no longer used:
[http://opencv.willowgarage.com/wiki/InstallGuide%20%3A%20Debian](http://opencv.willowgarage.com/wiki/InstallGuide%20%3A%20Debian)

---

