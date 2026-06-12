---
title: "Help with IDE"
date: 2010-06-29
forum: Programming Talk
---

### Post by WiiTard on 2010-06-29
Hello. Coming from Windows, my favorite C++ IDE has always been MinGW Developer Studio.

I found the Linux .DEB package of MinGWStudio and installed this IDE, and everything seems to work fine.

But there is this issue where every other time I press Build and Execute, the IDE will start to build the project, then MinGWStudio will unexpectedly close. I don't understand why. It doesn't happen every time I compile, it seems like every second or third time.


I am using Lucid Lynx amd64, if that makes a difference. Any help is greatly appreciated. I really do not want to have to switch IDEs.

---

### Post by Yes on 2010-06-29
Try running it from the command line, so you can see what errors it exits with.

---

### Post by WiiTard on 2010-06-29
> **Yes said:**
> Try running it from the command line, so you can see what errors it exits with.

OK. Here is the terminal output:

```

Gtk-CRITICAL **: gtk_container_remove: assertion `GTK_IS_TOOLBAR (container) || widget->parent == GTK_WIDGET (container)' failed

(MinGWStudio:2047): Gtk-CRITICAL **: gtk_container_remove: assertion `GTK_IS_TOOLBAR (container) || widget->parent == GTK_WIDGET (container)' failed

(MinGWStudio:2047): Gtk-CRITICAL **: gtk_container_remove: assertion `GTK_IS_TOOLBAR (container) || widget->parent == GTK_WIDGET (container)' failed

(MinGWStudio:2047): Gtk-CRITICAL **: gtk_container_remove: assertion `GTK_IS_TOOLBAR (container) || widget->parent == GTK_WIDGET (container)' failed
Segmentation fault

```

When MinGWStudio crashed it said Segmentation Fault

---

### Post by mmix on 2010-06-30
version 2.0.6?

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=946669](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=946669)

it seems to be abandonware.

---

### Post by WiiTard on 2010-06-30
> **mmix said:**
> version 2.0.6?

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=946669](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=946669)

it seems to be abandonware.


Yep, I have 2.0.6. Yes its abandonware but nevertheless it is still a great IDE in my humble opinion.

What could be causing the "segmentation fault" error?

---

### Post by mmix on 2010-07-02
> **WiiTard said:**
> 
What could be causing the "segmentation fault" error?

I had never tried to use it, but,
Latest gtk version in ubuntu 10.04 could be the problem.

Gtk code base getting change rapidly, however, generally, 
abandonware use it's old GUI code base.

---

