---
title: "[Pigment] Python error. Segmentation fault"
date: 2008-09-21
forum: Programming Talk
---

### Post by Intosia on 2008-09-21
Ok this is bugging me for like two weeks now...

I get a 'segmentation fault' when i try to run a pigment example.
```
root@intosia-desktop:/home/intosia/pigment-python-0.3.7/examples# python image.py 
Segmentation fault
```

What i do is:

- Fresh Ubuntu install (VFAT)
- Download Pigment source & Pigment-Python source from [Link]("https://code.fluendo.com/pigment/trac")
- Install the following packages with Apt-Get
[LIST]
[*]libglib2.0-dev
[*]libgtk2.0-dev
[*]gtk-doc-tools
[*]libgstreamer0.10-dev
[*]libgstreamer-plugins-base0.10-dev
[*]libc6-dev
[/LIST]
(those are in the README of Pigment)

- ./configure  (NO errors) [LOG]("http://intosia.com/uplaai/pigment_configure.txt")
- Make (Alot happens on screen no errors for far i can see)
- Make install (Seems fine) [LOG]("http://intosia.com/uplaai/pigment_makeinstall.txt")

Ok now i got Pigment installed, up to Python-Pigment
- Installed packages
[LIST]
[*]python2.5-dev
[*]python-gobject-dev
[*]python2.5-gst0.10
[/LIST]
(From README)
- ./configure (no problems) [LOG]("http://intosia.com/uplaai/python_configurelog.txt")
- make
- make install [LOG]("http://intosia.com/uplaai/python_makeinstalllog.txt")

So it should be all ok... 
But when i try to run a example script (python image.py). I get a segmentation fault... This is driving me nuts!

---

### Post by Zugzwang on 2008-09-21
Try using valgrind.
```
valgrind --tool=memcheck python image.py
```
Maybe that reveals some information about which components causes the segfault.

---

### Post by Intosia on 2008-09-21
Thanks.

The output of Valgrind shows a error in the Viewport routine of Pigment.
[LOG]("http://intosia.com/uplaai/output.txt")  (wayy below)

When i search for this error i get the bugtrack site of Pigment that shows a similar error:
[https://code.fluendo.com/pigment/trac/ticket/210](https://code.fluendo.com/pigment/trac/ticket/210)

Although that error is a year old should be fixed. The problem was with a GLX extention. That triggered me to run GLXINFO. Which shows i have the correct extention available (glXGetProcAddressARB)...

So im stuck now. Could it be my videocard (NV 8800GTX), im using the Restricted drivers that Ubuntu served me.

---

### Post by Intosia on 2008-09-23
Ok, i know its like cursing in church but i download the RPM's (which are way more up to date then Ubuntus debs), and used Alien. Works like a charm... :)

---

