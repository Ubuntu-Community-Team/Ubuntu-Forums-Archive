---
title: "wxPython and wxGlade problem!"
date: 2008-03-31
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2008-03-31
Hi

I've just installed wxPython 1.8 and wxGlade.

when i build a gui using wxGlade and generated the code I got the following erro!
```

 File "./kdsd.py", line 5, in <module>
    from wxPython.wx import *
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wxPython/__init__.py", line 15, in <module>
    import _wx
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wxPython/_wx.py", line 8, in <module>
    from _misc import *
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wxPython/_misc.py", line 456, in <module>
    wxDateTime_GetNumberOfDaysinYear = wx._misc.DateTime_GetNumberOfDaysinYear
AttributeError: 'module' object has no attribute 'DateTime_GetNumberOfDaysinYear'


```

Anyone know why? and what to do about it? it cant be my fault as I havent even edited the generated code yet! :lolflag:

Mike

---

