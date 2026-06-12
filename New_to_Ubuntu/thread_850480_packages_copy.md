---
title: "packages copy"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by lio_013 on 2008-07-05
how can i copy the packages from a cd to the path 
/var/cache/apt/archives?
i tryed many times but i couldnot
:(:(:(

---

### Post by sisco311 on 2008-07-05
open your file browser as root:
```
gksu nautilus
```or use the cp command from a terminal:
```
sudo cp /media/cdrom/path/to/files/filename.deb /var/cache/apt/archives
```to copy all files from a folder:
```
sudo cp /media/cdrom/path/to/folder/* /var/cache/apt/archives
```

---

### Post by lio_013 on 2008-07-05
thanks i wasnot know how to browse folders as root
im copying them now

---

### Post by durand on 2008-07-06
> **sisco311 said:**
> open your file browser as root:
```
gksu nautilus
```or use the cp command from a terminal:
```
sudo cp /media/cdrom/path/to/files/filename.deb /var/cache/apt/archives
```to copy all files from a folder:
```
sudo cp /media/cdrom/path/to/folder/* /var/cache/apt/archives
```

I think you need to use -R for cp rather than an asterisk because there may be folders in there as well which won't be copied.

---

### Post by ChameleonDave on 2008-07-06
> **durand said:**
> I think you need to use -R for cp rather than an asterisk because there may be folders in there as well which won't be copied.

Probably best to do "*.deb" in this case.

---

### Post by durand on 2008-07-06
Oh yeah, I meant in general usage of cp.

---

### Post by sayakb on 2008-07-06
Copying the packages to /var/cache/apt/archives will **not** install them. Copy them to some other location and open that location at a terminal and do:
```
sudo dpkg -i *.deb
```
**Caution**: If the CD contains two different versions of the same package, dpkg may cause a broken dependency situation.

---

### Post by ChameleonDave on 2008-07-06
> **LinuxIsInnovation said:**
> Copying the packages to /var/cache/apt/archives will **not** install them. Copy them to some other location and open that location at a terminal and do:
```
sudo dpkg -i *.deb
```
**Caution**: If the CD contains two different versions of the same package, dpkg may cause a broken dependency situation.

I don't think anyone implied that that would install them!

It is not advisable to install large numbers of packages with the command you give.  What if there are problems, such as you mentioned?

Far better to dump those packages in /var/cache/apt/archives and then install them using Synaptic.  You then get the latest version of everything, with dependencies handled.

---

### Post by durand on 2008-07-06
> **ChameleonDave said:**
> I don't think anyone implied that that would install them!

It is not advisable to install large numbers of packages with the command you give.  What if there are problems, such as you mentioned?

Far better to dump those packages in /var/cache/apt/archives and then install them using Synaptic.  You then get the latest version of everything, with dependencies handled.

Yes, my thoughts exactly.

---

### Post by ChameleonDave on 2008-07-08
By the way, "*gksudo nautilus*" is only the appropriate command to open the graphical file manager as root on GNOME (standard Ubuntu).  For KDE (Kubuntu), use "*kdesudo konqueror*"; for Xfce (Xubuntu), use "*gksudo thunar*".

Make sure you close the file manager after you have finished the administrative task in question, as it is dangerous to use it for general purposes.  Any files you create whilst using a file manager as root will be owned by root, and will not be editable by you as a normal user.

> **lio_013 said:**
> thanks i wasnot know how to browse folders as root
im copying them now

Great.  It seems your problem is fixed.  Perhaps you could use the "Thread Tools" menu to mark this thread as solved.

---

