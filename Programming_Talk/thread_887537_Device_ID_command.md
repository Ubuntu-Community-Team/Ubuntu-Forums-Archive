---
title: "Device ID command"
date: 2008-08-12
forum: Programming Talk
---

### Post by KB1LQC on 2008-08-12
Does anyone know how to acquire and set a certain device such as a USB drive to always be the same drive letter.  I.E.  have a certain reader always be /dev/sdb.  I want to use this in a program I have been working on.  Thanks!




Bryce
KB1LQC

---

### Post by finer recliner on 2008-08-12
every mountable device has a unique ID called a UUID. you can use this ID to mount a specific device to a specific path in your fstab.

this sounds similar to your problem:
[http://www.linuxforums.org/forum/misc/20903-uuid.html](http://www.linuxforums.org/forum/misc/20903-uuid.html)

---

