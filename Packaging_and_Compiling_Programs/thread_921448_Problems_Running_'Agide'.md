---
title: "Problems Running 'Agide'"
date: 2008-09-16
forum: Packaging and Compiling Programs
---

### Post by nikki93 on 2008-09-16
I'm not sure whether this is on the right forum.:confused:

Anyway, I installed AAP (from the .zip), and then Agide (from CVS), from [here]("http://www.a-a-p.org/"). Both of them install fine, but when I run Agide, I get the following error(s):-

```
/usr/local/lib/aap/Agide-0.124/agide.py:96: DeprecationWarning: The wxPython compatibility package is no longer automatically generated or actively maintained.  Please switch to the wx package as soon as possible.
  from wxPython.wx import wxNewId
Traceback (most recent call last):
  File "/usr/local/bin/agide", line 12, in <module>
    agide.main()
  File "/usr/local/lib/aap/Agide-0.124/agide.py", line 273, in main
    agideMain()
  File "/usr/local/lib/aap/Agide-0.124/agide.py", line 96, in agideMain
    from wxPython.wx import wxNewId
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wxPython/__init__.py", line 15, in <module>
    import _wx
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wxPython/_wx.py", line 8, in <module>
    from _misc import *
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wxPython/_misc.py", line 456, in <module>
    wxDateTime_GetNumberOfDaysinYear = wx._misc.DateTime_GetNumberOfDaysinYear
AttributeError: 'module' object has no attribute 'DateTime_GetNumberOfDaysinYear'

```

I'm guessing its due to it being really old, and thus using a really old wxPython.

On a side note: I was actually looking for a simple IDE that I could plug Vim into. I CAN use Vim by itself, but IDEs are fun. :)

---

### Post by Partyboi2 on 2008-09-17
What version of  python-wxgtk do you have installed? Try installing 
 python-wxgtk2.8 if you don't already have it installed.

---

### Post by nikki93 on 2008-09-17
I already have that installed...

---

