---
title: "Thotkeeper installation."
date: 2008-05-19
forum: New to Ubuntu
---

### Post by cserpentis on 2008-05-19
Has anyone successfully installed this program on ubuntu system? I've installed most of Python and wxWidgets I could find to get it running, as it was told in the manual, but to no effect. When I try to run the damn thing it gives me the following in console:
```
Traceback (most recent call last):
  File "./thotkeeper", line 17, in <module>
    import tk_main
  File "./lib/tk_main.py", line 19, in <module>
    from wxPython.wx import *
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wxPython/__init__.py", line 15, in <module>
    import _wx
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wxPython/_wx.py", line 8, in <module>
    from _misc import *
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wxPython/_misc.py", line 456, in <module>
    wxDateTime_GetNumberOfDaysinYear = wx._misc.DateTime_GetNumberOfDaysinYear
AttributeError: 'module' object has no attribute 'DateTime_GetNumberOfDaysinYear'
```

Any help would be welcome. If you have this program running on your system, I would be exceptionally gratefull if you would write what you did to get it up and running. Thanks in advance.

---

### Post by cmpilato on 2008-05-20
I was/am able to use ThotKeeper 0.2.0 on both Ubuntu 7.10 and 8.04.  I don't have a 7.10 box on hand any more, but on the 8.04 box, I've got python-wxgtk2.8 (2.8.7.1-0ubunt) and Python 2.5.2.  As far as I know, these are the stock versions of these tools from the distribution at this point.

We (I'm one of the ThotKeeper devs) know that version 0.1.0 doesn't work with Ubuntu 8.04, though.  Are you using 0.2.0?

---

### Post by cserpentis on 2008-05-21
Yes, as I see the best solution is to use the latest buit, that could be pulled from the svn. (svn checkout [http://thotkeeper.googlecode.com/svn/trunk/](http://thotkeeper.googlecode.com/svn/trunk/) thotkeeper-read-only)

Thanks for quick bug-fixes.

---

