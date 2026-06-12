---
title: "Problem with compiling a pyqt program"
date: 2008-05-20
forum: Programming Talk
---

### Post by thotmos on 2008-05-20
I'm starting to learn python, but I'm familiar with qt over c++
and after reading this tutorial [http://wiki.python.org/moin/JonathanGardnerPyQtTutorial]("http://wiki.python.org/moin/JonathanGardnerPyQtTutorial") I find the calls very similar to
those in c++, so I decided to give it a try. when running the program though the following error came up.
```

sameh@desktop:~/dev/pyqt$ python at.py
Traceback (most recent call last):
  File "at.py", line 3, in <module>
    from at_auto import at_auto
  File "/home/sameh/dev/pyqt/at_auto.py", line 10, in <module>
    from PyQt4 import QtCore, QtGui
RuntimeError: the PyQt4.QtCore and qt modules both wrap the QObject class
```
is the program outdated or something is missing

---

### Post by thotmos on 2008-05-20
well its outdated, but I've put my version
I like python, it's really easy and bonds with Qt beautifully
making great for prototyping

---

### Post by goterror on 2008-09-16
Yes. It works now. Thx. :guitar:

I think the problem caused by non-compatible between qt3 and qt4. 

And don't forget using pyuic4 instead of using pyuic

---

