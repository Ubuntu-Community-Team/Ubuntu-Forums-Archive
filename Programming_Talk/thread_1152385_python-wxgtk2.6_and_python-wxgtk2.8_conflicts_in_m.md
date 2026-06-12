---
title: "python-wxgtk2.6 and python-wxgtk2.8 conflicts in my program"
date: 2009-05-07
forum: Programming Talk
---

### Post by dodle on 2009-05-07
I have built a program that makes use of the wx.HyperLinkCtrl class of wxpython2.8.  This causes a problem if wxpython2.6 is installed and my program cannot launch.  Apperently upon importing, my program sees 2.6 is installed and imports it before it sees 2.8.  Is there a way to tell it to specifically look for 2.8?  This would be better than adding 2.6 to my program's conflicts list.

```
import wx, os, wx.lib.dialogs
```

---

### Post by dodle on 2009-05-08
I figured it out thanks to [http://wiki.wxpython.org/MultiVersionInstalls](http://wiki.wxpython.org/MultiVersionInstalls)
```
import wxversion
wxversion.select("2.8")
import wx, os, wx.lib.dialogs

```

---

