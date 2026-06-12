---
title: "PyGtk vs. wxPython for my project"
date: 2010-03-26
forum: Programming Talk
---

### Post by dodle on 2010-03-26
I have an open source project that I haven't worked on in a while, but would like to get back in to.  The project is written in Python using wx for the Gnome version and Qt for Kde.  

My question is in regard to the wx version.  As I understand it, wx wraps around Gtk.  Would there be any reason to switch and re-write it in pure Gtk?  I've never programmed using Gtk, but if it would make my program more preferable for other programmers then I would like to learn it.

---

### Post by akudewan on 2010-03-26
Hi,

Your question is quite subjective. If I were you, I would have just made a wx version and not bothered even with the Qt version. This is because pyqt, pygtk and wxpython all need to be installed separately. If the user has to install a library, might as well just stick to wxpython. The native look-and-feel issue is not worth it (as long as it doesn't look too ugly). That's my opinion anyway.

> 
I've never programmed using Gtk, but if it would make my program more preferable for other programmers then I would like to learn it.

No point, unless you just want to learn pyGtk. wxPython is simple enough for most programmers.

---

### Post by dodle on 2010-03-29
Thanks, I am going to stick with wxPython.

---

### Post by cdekter on 2010-03-31
> **dodle said:**
> My question is in regard to the wx version.  As I understand it, wx wraps around Gtk.  Would there be any reason to switch and re-write it in pure Gtk?  I've never programmed using Gtk, but if it would make my program more preferable for other programmers then I would like to learn it.

The main reason a project would switch from wx to pygtk would be to use features of GTK not available in wx. This is because wx is cross-platform and must cater for the lowest common denominator - features available on all platforms. Otherwise it must re-implement featuers missing from a particular platform... anyway, for a basic app there is no logical reason to re-do a UI already built with wx.

---

