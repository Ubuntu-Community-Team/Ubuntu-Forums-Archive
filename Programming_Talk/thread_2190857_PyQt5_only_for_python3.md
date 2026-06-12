---
title: "PyQt5 only for python3?"
date: 2013-11-29
forum: Programming Talk
---

### Post by Erik1984 on 2013-11-29
I'm looking for the PyQt5 packages on Ubuntu and I can't find a package for python 2.x For Qt4 there is python-qt4 but there is no package named python-qt5. There is a package called python**3**-qt5. Is this Ubuntu's way to tell me to move on to Python3 :) ? Or should I just stick with Qt4? I haven't really 'invested' in Qt yet so at this point I think it's better to get familiar with the latest version of Qt.

---

### Post by Erik1984 on 2013-12-03
*bump*

---

### Post by schmidtbag on 2013-12-04
Canonical is trying to ditch python2.x, and it's about time.  There are very few libraries worth using that don't work with python3 at this point.  I developed a python2 program around 2000 lines long, more or less, using qt5.  I initially decided to write it in python2 because for some reason, the python3 version didn't have a way to convert UI files to python3 (at least in Arch it doesn't).  I decided I needed to switch to python3 because distros like ubuntu don't support pyqt5 on python3.  Amazingly, I only needed to modify about 5 lines of code to make it work, and only 1 or 2 of those lines were Qt specific.

So in short, just switch to python3.

---

### Post by Erik1984 on 2013-12-08
Thanks. I'll go with python3.

---

### Post by bootch2 on 2014-03-26
I think that the PyQt5 binding is compatible with Python 2.6+.

The problem you are experiencing is that Ubuntu still includes and segregates Python 2.7 from Python3, and installs package python3-pyqt5 with Python 3 packages.  But if you just type 'python' on a command line, you get Python2.7 and it can't find the PyQt5 module since it is installed with the Python3 modules.

(It seems inconsistent that Ubuntu makes Python2.7 the default python version (when you just enter 'python')  but doesn't package PyQt5 that installs with Python2.7?)

I don't think it is hard to download PyQt5 source from the vendor, build, and install it yourself.  (In my experience, it is bullet proof.) Except that you must download and install both SIP and PyQt, and you must be sure that you are using the python version you want (Python 2.7) when you finally install it (when you invoke >python setup.py install.)

But the other poster is correct, you might as well switch to Python 3, and the more people who fight inertia and do so, the sooner this mess will be history.

---

