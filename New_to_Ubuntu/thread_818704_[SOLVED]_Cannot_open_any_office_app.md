---
title: "[SOLVED] Cannot open any office app"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Michaelg14 on 2008-06-04
For the last couple days I have been unable to start any open office application.  I can open an existing document but not a blank one.

When I enter ooffice in the terminal I get:

greybeard@greybeard-desktop:~$ ooffice
greybeard@greybeard-desktop:~$ Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f00ec68997c]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x15) [0x7f00ec689a15]
#2 /usr/lib/libX11.so.6 [0x7f00f0353323]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x44) [0x7f00f034ad54]
#4 /usr/lib/libgdk-x11-2.0.so.0(gdk_window_new+0x395) [0x7f00ec233c05]
#5 /usr/lib/libgtk-x11-2.0.so.0 [0x7f00e78c24c8]
#6 /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x10f) [0x7f00eb6c7bcf]
#7 /usr/lib/libgobject-2.0.so.0 [0x7f00eb6db386]
#8 /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x875) [0x7f00eb6dd0d5]
#9 /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83) [0x7f00eb6dd483]
#10 /usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0x77) [0x7f00e78b3957]
#11 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f00e7c6b76d]
#12 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f00e7c6c16a]
#13 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f00e7c6c82b]
#14 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f00e7c44f64]
#15 /usr/lib/openoffice/program/libvcl680lx.so [0x7f00f3bf04ed]
#16 /usr/lib/openoffice/program/libvcl680lx.so [0x7f00f3b85322]
#17 /usr/lib/openoffice/program/libvcl680lx.so(_ZN9TabDialogC2EP6WindowRK5ResId+0x5f) [0x7f00f3bc21cf]
#18 /usr/lib/openoffice/program/libsvx680lx.so [0x7f00e0949084]
#19 /usr/lib/openoffice/program/libsvx680lx.so [0x7f00e0b1ddb4]

Any help would be appreciated.

Mike

---

### Post by JoshuaRL on 2008-06-04
Try this:
```

sudo apt-get remove --purge ooffice
sudo apt-get install ooffice

```
See if that fixes it.

---

### Post by Michaelg14 on 2008-06-04
I don't think this is right...

greybeard@greybeard-desktop:~$ sudo apt-get remove --purge ooffice
[sudo] password for greybeard: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ooffice
greybeard@greybeard-desktop:~$ sudo apt-get install ooffice
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ooffice

---

### Post by JoshuaRL on 2008-06-04
Alright, are you sure that's the right package name?

---

### Post by forestpixie on 2008-06-04
I thought it was soffice - did you by chance run an update a few days ago for openoffice - I had to delete all teh openoffice and reinstall.

---

### Post by Michaelg14 on 2008-06-04
I get the same results with soffice, and yes I did just do an update.  I will try using package manager to reload everything

---

### Post by JoshuaRL on 2008-06-04
Make sure you mark it for complete removal.  And then after that reinstall it.

---

### Post by Michaelg14 on 2008-06-04
It Works, Thanks guys.  I had to use synaptics to get it all the way out.  Add/Remove applications didn't want to remove writer.

:lolflag:



How do I mark this as solved?   (never mind)

---

