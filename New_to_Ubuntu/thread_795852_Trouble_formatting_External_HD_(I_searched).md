---
title: "Trouble formatting External HD (I searched)"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by Firefighter503 on 2008-05-15
Ok, I recently installed Ubuntu on an HD that my buddy dropped into his external HD case (Windows OS) and formatted for me. I want to format a couple of other HDs that currently have various Windows crap on them. For instance: 2 HDs that were set up in Raid0 for my previous computer. I have one in an external HD case now, and have it plugged into my computer (USB), but my computer can not seem to recognize that anything is even plugged in. 

Any ideas based on the following terminal output:

> justin@Justin:~$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda5      [COLOR="Red"][this is my root HD, is that normal partitioning?][/COLOR]

and:

> justin@Justin:~$ sudo fdisk -l

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xab16d928

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17495   140528556   83  Linux
/dev/sda2           17496       18241     5992245    5  Extended
/dev/sda5           17496       18241     5992213+  82  Linux swap / Solaris

I am trying to format a HD, so that I may load Windows on it for when it is needed. 

Help please!

---

### Post by uclalinux on 2008-05-15
yes that is normal partitioning, if you are going to still windows on HD other then the main one you will need to use a chainloader from grub. Windows will not install on secondary drive in the bios, it must be installed on the first drive. -it sucks, i know. Google how to doit there are lots of howTo's on the topic.

here is one i found [http://gentoo-wiki.com/HOWTO_Dual_boot](http://gentoo-wiki.com/HOWTO_Dual_boot)

---

### Post by stairwayoflight on 2008-05-15
what is the output of
```
dmesg |tail -n 15
```

---

