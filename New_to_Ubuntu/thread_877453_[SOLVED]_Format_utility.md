---
title: "[SOLVED] Format utility?"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by esotericguy on 2008-08-01
I need to format an external HD to ntfs but add/remove... doesn't seem to have a program for formatting. Can someone point me in the right direction?

---

### Post by jolx on 2008-08-01
gparted.

---

### Post by tamoneya on 2008-08-01
as jolx said gparted.  Hit alt-F2 and type:```
gksudo gparted
```

---

### Post by zvacet on 2008-08-01
[Gparted]("http://gparted.sourceforge.net/")

---

### Post by esotericguy on 2008-08-01
> **jolx said:**
> gparted.

edit:nevermind

---

### Post by tamoneya on 2008-08-01
> **esotericguy said:**
> it's an EXTERNAL hard drive and the download for that is an ISO. I need a program that i can install in Ubuntu and format it.

Yes we know it is external.  gparted will work on externals and it is already installed on hardy so there is no need to install.

---

### Post by kansasnoob on 2008-08-01
Yes, gparted should be able to format the drive. It's available in synaptic.

But since you're going to ntfs, please install ntfsprogs while you're there.

That will give you excellent read/write support for NTFS.

[http://www.linux-ntfs.org/doku.php](http://www.linux-ntfs.org/doku.php)

---

### Post by jo.cisco on 2008-08-02
ok so i have a similar probelm....gparted wont format my extrenal hard disk into anything but ext2/3. fat16/32, and linux swap. I want NTFS.

---

### Post by ingeva on 2008-08-02
> **tamoneya said:**
> Yes we know it is external.  gparted will work on externals and it is already installed on hardy so there is no need to install.

I needed to install it, but it was on the list ... :)

However, if you need NTFS that means you must have a Windows system, which has the capability to create NTFS partitions as well as formatting them.

---

### Post by drs305 on 2008-08-02
mkfs.ntfs can also create/format an ntfs partition via terminal. Read about it at "man mkfs.ntfs"

---

### Post by zvacet on 2008-08-02
@ **jo.cisco**

> .gparted wont format my extrenal hard disk into anything but ext2/3. fat16/32, and linux swap. I want NTFS.

That is why I suggested [Gparted live CD.]("http://gparted.sourceforge.net/")

---

