---
title: "Python-&gt;help-&gt;modules= Seg fault"
date: 2012-07-24
forum: Programming Talk
---

### Post by kindledwind on 2012-07-24
Here it is, Ubuntu 12.04 64bit :

```

todd@laptop:~$ python
Python 2.7.3 (default, Apr 20 2012, 22:39:59) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> help()

Welcome to Python 2.7!  This is the online help utility....

# 3 more paragraphs of the standard response go here.

help> modules

Please wait a moment while I gather a list of all available modules...

/usr/lib/python2.7/dist-packages/gobject/constants.py:24: Warning: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
  import gobject._gobject
/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:40: Warning: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
  from gtk import _gtk

** (python:5005): CRITICAL **: pyg_register_boxed: assertion `boxed_type != 0' failed
/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:40: Warning: cannot register existing type `GdkDevice'
  from gtk import _gtk
/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:40: Warning: g_type_get_qdata: assertion `node != NULL' failed
  from gtk import _gtk
Segmentation fault (core dumped)

```

Any ideas?

Thanks in advance
Todd

---

### Post by Bachstelze on 2012-07-24
A segfault is almost always due to a bug in the program, so here it's a bug in Python, and there's nothing you can do besides reporting it if it hasn't been reported already.

---

### Post by kindledwind on 2012-07-24
Hmmph...bummer.

For anyone landing here due to a search result:
```
apt-get install --force-reinstall true python
```
doesn't fix it either.

---

### Post by Bachstelze on 2012-07-24
Of course it doesn't fix it, it reinstalls the same package with the same bug. ;) Why not use Python 3?

---

### Post by kindledwind on 2012-07-24
Because Python3 doesn't come with pyusb in the packages. Manually installing pyusb from sourceforge seems to work though..

I was hoping I'd screwed 2.7 up in my random examinations of how things work & the reinstall would sort it out... :D Guess not.

todd

---

