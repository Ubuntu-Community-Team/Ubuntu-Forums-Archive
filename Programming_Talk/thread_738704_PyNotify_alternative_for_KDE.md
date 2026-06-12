---
title: "PyNotify alternative for KDE?"
date: 2008-03-28
forum: Programming Talk
---

### Post by xelapond on 2008-03-28
Hello, 

I am writing a program in PyQt, and I am using the PyNotify notification library.  Is there an alternative to this for KDE4?  It looks weird having Gtk notifications pop up in KDE4.

Thanks, 

Alex

---

### Post by Whiffle on 2008-03-28
In KDE3 you can use the DCOP interface to popup notifications, I don't know why it wouldn't work in kde4.

[http://www.fruitsalad.org/people/phil/kde/userguide-tng/kde-diy.html](http://www.fruitsalad.org/people/phil/kde/userguide-tng/kde-diy.html)

---

### Post by happysmileman on 2008-03-28
> **xelapond said:**
> Hello, 

I am writing a program in PyQt, and I am using the PyNotify notification library.  Is there an alternative to this for KDE4?  It looks weird having Gtk notifications pop up in KDE4.

Thanks, 

Alex


There's KNotify, not sure if it's still called that in KDE4 but it's a place to start looking.

---

