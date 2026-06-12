---
title: "wx python error!"
date: 2009-05-05
forum: Programming Talk
---

### Post by bg11 on 2009-05-05
I can't get wx to work, I keep getting an import error:

> 
> python ColorPanel.py
Traceback (most recent call last):
  File "ColorPanel.py", line 6, in <module>
    import wx
  File "/usr/lib/python2.5/site-packages/wx-2.6-gtk2-unicode/wx/__init__.py", line 42, in <module>
    from wx._core import *
  File "/usr/lib/python2.5/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 4, in <module>
    import _core_
ImportError: /usr/lib/libwx_gtk2u_core-2.6.so.0: undefined symbol: wxEVT_COMMANDCHOICEBOOK_PAGE_CHANGED, version WXU_2.6


---

### Post by bg11 on 2009-05-05
Hmm, very strange, everything is back to normal after a re-boot!

:-?

---

### Post by salvachn on 2009-05-06
It might be that your instance of the terminal didn't properly get the locale of wxpython or does it have to do with wxwindows?

---

