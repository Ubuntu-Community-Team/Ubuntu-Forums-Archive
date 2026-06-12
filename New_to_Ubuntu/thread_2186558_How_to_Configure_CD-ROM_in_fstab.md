---
title: "How to Configure CD-ROM in fstab"
date: 2013-11-07
forum: New to Ubuntu
---

### Post by altemir on 2013-11-07
I am a newbie who just installed Lubuntu 13.10 and am trying to run "sudo apt-get update".  When I do, I get error messages saying:[INDENT]
Please use apt-cdrom to make this CD-ROM recognized by APT.
[/INDENT]

In reading the apt-cdrom manual, a mountpoint is required, which must be "properly configured" in /etc/fstab.  Below is what I see in fstab:[INDENT]Lubuntu@Lubuntu:~$ cat /etc/fstab[/INDENT]
[INDENT]# /etc/fstab: static file system information.[/INDENT]
[INDENT]#[/INDENT]
[INDENT]# Use 'blkid' to print the universally unique identifier for a[/INDENT]
[INDENT]# device; this may be used with UUID= as a more robust way to name devices[/INDENT]
[INDENT]# that works even if disks are added and removed. See fstab(5).[/INDENT]
[INDENT]#[/INDENT]
[INDENT]# <file system> <mount point>   <type>  <options>       <dump>  <pass>[/INDENT]
[INDENT]# / was on /dev/sda1 during installation[/INDENT]
[INDENT]UUID=a883d2c8-4ee8-4dd1-87ce-0cae417dc367 /               ext4    errors=remount-ro 0       1[/INDENT]
[INDENT]# swap was on /dev/sda5 during installation[/INDENT]
[INDENT]UUID=4b16b113-7121-45aa-9c89-bde7e4fda9e4 none            swap    sw              0       0
[/INDENT]

I don't really know what this stuff means, but I don't see anything that looks like a "mount point" for a CD-ROM.  Of I don't know what a mount point is so maybe it's here :-)  

My question:  How do I get apt-get to recognize my CD-ROM?  As an aside, why can I browse files on my CD-ROM in file manager by apt-get doesn't know where it is?

Thanks in advance

---

### Post by fantab on 2013-11-07
Since you already installed Lubuntu, you don't need CDROM. Is the machine connected online?

Open 'Software center' from menu select 'EDIT'-> 'software sources' and uncheck/deselect CDRom

then run:
```
sudo apt-get update
```

---

### Post by deadflowr on 2013-11-07
Are you trying to install deb installation files from the cd?

Do you want to install deb installation files from a cd?

---

### Post by altemir on 2013-11-08
thanks, fantab.  That was easy :p

---

