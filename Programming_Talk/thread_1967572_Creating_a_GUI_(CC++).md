---
title: "Creating a GUI (C\C++)"
date: 2012-04-28
forum: Programming Talk
---

### Post by Spirrwell on 2012-04-28
Alright, this should be simple enough. I'm looking for a way to create GUI on Linux. For a comparison, in Windows to make a GUI, you'd make a Win32 application with a window handle and whatnot. I'm looking for a way to do this that is compatible with most Linux operating systems. It'd be great if this could be done without the use of an external library.

If an external library is required such as GTK, QT, and etc., I'd prefer to have a plain C and\or C++ support, as in most cases, I'd rather program in plain C. Any recommendations as to what I should look into are appreciated.

---

### Post by Vaphell on 2012-04-28
gui is not a part of C/C++ standards so it's always provided by external, platform dependent libraries.

gtk - C
gtkmm - C++ bindings to gtk
QT - C++
wxWidgets - C++

look at some tutorials related to those toolkits and pick the one that suits you best.

---

### Post by Spirrwell on 2012-04-28
> **Vaphell said:**
> gui is not a part of C/C++ standards so it's always provided by external, platform dependent libraries.
I'm aware of that, but Windows has Win32, I would naturally assume Linux has something similar.

---

### Post by zombifier25 on 2012-04-28
Linux is only the kernel. Linux-based OSes may have whatever library they want. But no worries; most (if not all) major Linux distros has GTK and Qt already installed.
EDIT: Except from-the-scratch distros like Arch of course.

---

### Post by Vaphell on 2012-04-28
> major Linux distros has GTK and Qt already installed.

'already installed' may be an overstatement, but 'one mouseclick away' - sure :) KDE has not much use of GTK, gnome/xfce has not much use of Qt. Either way mixing things is not a problem (unless you are a fan of purity) and any respectable distro has these libs in repos even if it doesn't use them in its default configuration.

---

### Post by Spirrwell on 2012-04-28
Alright, I'll go with gtk, but I have this problem: gtk_main();.

How can I do things while the program is running like for instance, say I have a chat server\client, how can I process the events of a network library if everything has to be done before gtk_main?

Edit:
Never mind, stupid question. Thanks!

---

### Post by DaviesX on 2012-04-29
signal_connect :)

---

