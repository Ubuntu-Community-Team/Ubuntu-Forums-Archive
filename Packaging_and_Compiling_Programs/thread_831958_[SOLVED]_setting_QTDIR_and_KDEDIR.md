---
title: "[SOLVED] setting QTDIR and KDEDIR"
date: 2008-06-17
forum: Packaging and Compiling Programs
---

### Post by Pollywoggy on 2008-06-17
The Qt and KDE packages put the includes and libs all over the place, so I have a problem in setting QTDIR and KDEDIR.  I am trying to learn about KDE but when I try to compile programs, the includes and libs can't be found. 

I know of one way to fix this, by installing the same version of Qt and kdelibs that are on my system as deb packages in /usr/local or in my home directory and then setting KDEDIR and QTDIR to point there, but that is a huge waste of disk space.  Is there another way?

---

### Post by Pollywoggy on 2008-06-22
> **Pollywoggy said:**
> The Qt and KDE packages put the includes and libs all over the place, so I have a problem in setting QTDIR and KDEDIR.  I am trying to learn about KDE but when I try to compile programs, the includes and libs can't be found. 

I know of one way to fix this, by installing the same version of Qt and kdelibs that are on my system as deb packages in /usr/local or in my home directory and then setting KDEDIR and QTDIR to point there, but that is a huge waste of disk space.  Is there another way?

I found how to set QTDIR and KDEDIR but also discovered these variables are obsolete with Qt 4.

---

