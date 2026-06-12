---
title: "Trash as superuser nautilus"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by Rokurosv on 2008-11-16
Ok so I made a backup of some configuration files when I didn't need them anymore I deleted them, the folder was mine but the files were root's, so basically I can't empty my trash bin cause I don't have permision to delete those files. How can I access an user's trash bin from root, via console or nautilus?

---

### Post by MrWES on 2008-11-16
/home/{USERNAME}/.trash

---

### Post by philinux on 2008-11-16
/home/username/.local/share/Trash
but use

gksudo nautilus

---

### Post by Rokurosv on 2008-11-16
> **philinux said:**
> /home/username/.local/share/Trash
but use

gksudo nautilus

Thanks that worked for me.

---

### Post by drs305 on 2008-11-16
Here's a link to a tutorial I wrote about finding and deleting system trash:
[Disk Full? - Check Your Trash Bin(s)]("http://ubuntuforums.org/showthread.php?t=898573")

It covers how to find the deleted files on your system, how to delete them, and how to free up more space on your partitions.

---

