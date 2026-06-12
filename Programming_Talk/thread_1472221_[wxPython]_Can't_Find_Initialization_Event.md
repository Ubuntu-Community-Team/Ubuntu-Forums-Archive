---
title: "[wxPython] Can't Find Initialization Event"
date: 2010-05-04
forum: Programming Talk
---

### Post by dodle on 2010-05-04
I thought that wx/wxPython had an event that could be caught on construction/initialization of an object, but I haven't been able to find it in neither the [wxPython]("http://www.wxpython.org/docs/api/wx-module.html") docs, [wx]("http://docs.wxwidgets.org/stable/wx_classref.html#classref") docs, nor googling.  I thought that someone had told me how to catch it here, but I can't find the thread.

Does anyone know what I am referring to?

---

### Post by dodle on 2010-05-04
It was the wx.CreateWindowEvent.  I couldn't get it to do what I wanted before, but now it seems to be working.

---

