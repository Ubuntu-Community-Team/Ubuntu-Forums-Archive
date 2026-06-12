---
title: "which graphics system used in ubuntu 6.10"
date: 2008-01-08
forum: Programming Talk
---

### Post by asif.kalim on 2008-01-08
hi,
plz tell me which graphics used by ubuntu 6.10, either its Framebuffer (fb) or QT, and also where can i find it on a ubutu system.

thanks in advance,
asif

---

### Post by scruff on 2008-01-09
QT is a graphics library/toolkit. 

Framebuffer (from wikipedia): The Linux framebuffer (fbdev) is a graphic hardware-independent abstraction layer to show graphics on a console without relying on system-specific libraries such as SVGALib or the heavy overhead of the X Window System.

If you are asking about the library, Ubuntu uses mainly GTK as Gnome is the default environment. If you use KDE, then QT is the predominant graphics library.

---

### Post by luisito on 2008-01-09
Framebuffer would be an alternative to an X server.

QT would be an alternative to GTK+ or wxWindows.

Ubuntu uses Gnome, which uses GTK+ and runs on top of an X server.

KUbuntu uses KDE, which uses QT and also runs on top of an X server.

I believe the ubuntu logo during the boot stage uses framebuffer.

GTK+ actually uses a graphics library called cairo.

---

