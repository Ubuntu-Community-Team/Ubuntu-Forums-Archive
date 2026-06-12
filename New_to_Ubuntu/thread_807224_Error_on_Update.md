---
title: "Error on Update?"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by kattman on 2008-05-25
Any suggestions on how to fix this error?

"Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs"   

Help Im still in the newbie mode

---

### Post by bwhite82 on 2008-05-25
With the CD in the drive, open a terminal, and enter:

> sudo apt-cd add

then

> sudo apt-get update

---

