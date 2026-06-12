---
title: "Python prgoarm put icon in System Tray(KDE4)?"
date: 2008-03-29
forum: Programming Talk
---

### Post by xelapond on 2008-03-29
Hello, 

Does anyone know how to put a tray icon in the system tray(KDE4) and have a menu pop up when you click on it?  I figure this would have some thing to do with PyQt, but I don't know.

Thanks, 

Alex

---

### Post by xelapond on 2008-03-29
I found something that looks really promising, I just have no idea how to use it:(

[http://doc.trolltech.com/4.3/qsystemtrayicon.html](http://doc.trolltech.com/4.3/qsystemtrayicon.html)

Would this be included it the PyQt module?  Can anyone give me some tips on how I would use this in Python?

Thanks a ton, 

Alex

---

### Post by nanotube on 2008-03-30
i think gtk's statusicon will work on both kde and gnome (and anything else with a standard tray icon)

see this site for example code:
[http://www.mail-archive.com/tracker-list@gnome.org/msg00669.html](http://www.mail-archive.com/tracker-list@gnome.org/msg00669.html)

so try it with pygtk (make sure it's gtk 2.10 or above)

---

