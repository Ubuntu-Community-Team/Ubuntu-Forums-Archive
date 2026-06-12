---
title: "[SOLVED] changing fstab question"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by fontenot_1031 on 2008-05-28
When I manually set up my laptop with hardy heron I accidentally had my seperate data partition mount in the directory /media/datadisk instead of /mnt/datadisk.  If I sudo nano /etc/fstab and change the mount point *would that cause any other problems with the ubuntu installation?*  (Besides application problems I know I'll have to change my music directory and so on)

---

### Post by Fire_Chief on 2008-05-28
As long as no part of the Ubuntu installation itself is on that partition, then you can change it at will with no ill effects on the OS.

Cheers!

---

### Post by drs305 on 2008-05-28
> **fontenot_1031 said:**
> When I manually set up my laptop with hardy heron I accidentally had my seperate data partition mount in the directory /media/datadisk instead of /mnt/datadisk.  If I sudo nano /etc/fstab and change the mount point *would that cause any other problems with the ubuntu installation?*  (Besides application problems I know I'll have to change my music directory and so on)

No, it shouldn't. Your ubuntu home partition isn't on it, is it?

---

### Post by fontenot_1031 on 2008-05-28
> **drs305 said:**
> No, it shouldn't. Your ubuntu home partition isn't on it, is it?

Yes I do have ubuntu installed on /
thanks for all of the help

---

