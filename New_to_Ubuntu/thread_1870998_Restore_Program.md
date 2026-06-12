---
title: "Restore Program"
date: 2011-10-28
forum: New to Ubuntu
---

### Post by bokgeneraal on 2011-10-28
Is there a restore program for ubuntu. One that goes back to a previous state of the system, even installing and uninstalling programs if need be , and goes back to all settings at that particular restore point. That would be useful. :o

---

### Post by MG&amp;TL on 2011-10-28
I suggest that you make a system image with a tool like clonezilla:

[http://clonezilla.org/]("http://clonezilla.org/")

Then store the image(s) (external device or cloud) until such a time as your computer breaks, updating about once a week to once a day, depending on your level of paranoia. I suggest keeping around three of the system images around, in case one is faulty in some way.

---

### Post by mikechant on 2011-10-28
If you want something a bit more like Apple's time machine or similar, you could look into this:
[http://backintime.le-web.org/](http://backintime.le-web.org/)
The documentation page on this website also mentions two other programs, filevault and flyback

The setup for backing out system updates (program installs/updates etc.) might be a bit complicated since these changes typically affect a number of different folders.
Personally for this sort of use I'd probably start by setting backintime (or equivalent) to back up the whole of the root filesystem but excluding certain parts like /var, /tmp /dev /proc etc.

---

### Post by Mark Phelps on 2011-10-28
> **bokgeneraal said:**
> Is there a restore program for ubuntu.

If you mean something like MS Windows System Restore, which is installed automatically, then basically -- NO.

You have to do your own image or file backups.

Unless you want to spend a lot of time learning scripting, or tweaking various for different directories and files, a relatively simple solution is the one already mentioned -- Clonezilla.

This functions much the same as Norton Ghost, Acronis True Image, or Macrium Reflect in MS Windows.

---

### Post by HermanAB on 2011-10-28
Well, on Linux, you don't really need that kind of thing.  The package manager does most of that and Linux is very easy to install and very stable.  Just backup your data.

---

### Post by bokgeneraal on 2011-11-01
Thanks for all the suggestions.:D

---

