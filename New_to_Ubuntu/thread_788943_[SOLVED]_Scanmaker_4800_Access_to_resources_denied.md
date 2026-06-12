---
title: "[SOLVED] Scanmaker 4800 Access to resources denied."
date: 2008-05-10
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-05-10
I have a scanmaker 4800 scanner and I keep coming up with an error saying access to resources is denied.  I am a member of the scanner group.  What else do I need to do to get this scanner working?

---

### Post by alienexplorers on 2008-05-10
Have tried adding the scanner to fstab.  Now it is listed in /proc/bus/usb/devices.  I still am unable to get it to run.  Still gives the error:
> Access to resources denied.
Any help would be appreciated.  I am desperate to get this running.

---

### Post by alienexplorers on 2008-05-10
bump

---

### Post by alienexplorers on 2008-05-11
Come on people.  I need help here. BUMP

---

### Post by alienexplorers on 2008-05-11
Problem fixed.  Had to delete from /usr/lib/sane:
> libsane-sm3840.so.1.0.19
libsane-sm3840.so
libsane-sm3840.so.1
next I got a copy of the 1.0.15 version of the libsane-sm3840 file and copied it to the /usr/lib/sane directory.
I then created a symbolic link as shown:
> cd /usr/lib/sane
ln -s libsane-sm3840.so.1.0.15 libsane-sm3840.so
ln -s libsane-sm3840.so.1.0.15 libsane-sm3840.so.1
Closed terminal and clicked xsane and scanner ran perfectly.

---

### Post by alienexplorers on 2008-05-11
I have submitted a error report to the sane project about this error.

---

