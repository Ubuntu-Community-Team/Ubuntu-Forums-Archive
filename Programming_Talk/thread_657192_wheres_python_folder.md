---
title: "wheres python folder"
date: 2008-01-03
forum: Programming Talk
---

### Post by Mr.popo on 2008-01-03
Please can you tell me where the python folder is please. I looked in /bin but its not there.



thanks

---

### Post by LaRoza on 2008-01-03
/usr/bin/python is the location of the interpreter

For future reference, the command "whereis" can help find the location of some things. It is a bit picky at times, as it only looks in a few areas.

```

whereis python

```

---

### Post by Martin Witte on 2008-01-03
to see where python looks for its libraries you can inspect sys.path, see [http://docs.python.org/inst/search-path.html#SECTION000410000000000000000](http://docs.python.org/inst/search-path.html#SECTION000410000000000000000) for more on this
[PHP]martin@toshibap200:~$ python
Python 2.5.1 (r251:54863, Oct  5 2007, 13:36:32) 
[GCC 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import sys
>>> print sys.path
['', '/usr/lib/python25.zip', '/usr/lib/python2.5', '/usr/lib/python2.5/plat-linux2', '/usr/lib/python2.5/lib-tk', '/usr/lib/python2.5/lib-dynload', '/usr/local/lib/python2.5/site-packages', '/usr/lib/python2.5/site-packages', '/usr/lib/python2.5/site-packages/Numeric', '/usr/lib/python2.5/site-packages/gst-0.10', '/var/lib/python-support/python2.5', '/usr/lib/python2.5/site-packages/gtk-2.0', '/var/lib/python-support/python2.5/gtk-2.0']
>>> [/PHP]

---

### Post by Mr.popo on 2008-01-03
cool thanks for the tips :)

---

### Post by dwblas on 2008-01-04
/usr/lib/python is where most of the stuff is.  You should also have a PYTHONPATH.  If so, keying $PYTHONPATH in the terminal will display it.

---

