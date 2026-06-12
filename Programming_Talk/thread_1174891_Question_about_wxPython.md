---
title: "Question about wxPython"
date: 2009-05-31
forum: Programming Talk
---

### Post by Volt9000 on 2009-05-31
I've just started learning wxPython, and ran into something which has be a bit confused.

In code, I'm writing things like wx.Frame, wx.App, wx.Menu, etc. But when I go to the online docs and check out the class reference, I see wxFrame, wxApp, wxMenu, etc.

I'm assuming that wx.Frame = wxFrame, but why are the class names different? I know that the wx. prefix is referring to the namespace called "wx" and the class itself is called "Frame", so why then do the docs refer to the class name as "wxFrame"?

---

### Post by crdlb on 2009-05-31
You've probably looking at the documentation for the C++ api, which uses C-style namespace prefixes.

---

### Post by Volt9000 on 2009-05-31
Ach, nevermind-- crdlb is right.

The wxPython docs site ([http://www.wxpython.org/onlinedocs.php](http://www.wxpython.org/onlinedocs.php)) just links directly to the wxWidgets website ([http://docs.wxwidgets.org/stable/wx_classref.html](http://docs.wxwidgets.org/stable/wx_classref.html)).

---

