---
title: "Configure a second hard drive?"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Famicommander on 2008-05-16
I've got Xubuntu 8.04 installed on a 40 GB IDE drive. I just installed a second IDE hard drive, and set it to slave.

But Xubuntu does not detect it. What am I doing wrong?

---

### Post by Famicommander on 2008-05-16
:frown:Why does no one respond to my topics?:confused:

---

### Post by Mark_in_Hollywood on 2008-05-16
Stupid as this might seem, please check that the disk is found by the BIOS. Then get back to me.

Also, in a terminal (console) type:

sudo fdisk -l

and post the output here.

---

### Post by Famicommander on 2008-05-16
```
jason@ubuntu:~$ sudo fdisk -l
[sudo] password for jason: 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfb3b0b7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

```

.

---

### Post by Dylock on 2008-05-16
Did you make an entry in your fstab?

---

### Post by rlcomstock3 on 2008-05-16
It appears that the second disk is not functional.  Check to make sure your bios sees it as was said above.  

Once you see that your harddrive is loaded 

$ sudo gparted

You should be able to format and set mount points.

---

### Post by Raccoon1400 on 2008-05-16
Are there any partitions on the hard drive? Check with something like gparted, which is on  the live cd.

---

### Post by bullfrog2 on 2008-05-16
you need XP or whatever installed on slave drive first. then take slave off.then install ubuntu. do not restart ubuntu until you hook slave up. boot up and ubuntu will find slave drive and give you a choice of either one to boot . hope this helps. worked for me. bullfrog 2.

---

### Post by Mark_in_Hollywood on 2008-05-17
Re-reading your first post in this thread, I see you have 2 hard drives. One has ubuntu and another is ?

If your BIOS finds the two drives, then if you want Ubuntu as the OS, and the 2nd drive as storage, then you must modify some files and that is beyond my ability to help you, but there are plenty of people here who do know. There are plenty of posts about this, if I'm understanding what you are doing.

If not, correct me.

---

### Post by wubrgamer on 2008-05-17
This might prove useful...It's actually a really mature howto: IMHO

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

Best of luck!

---

### Post by Barriehie on 2008-05-17
What are you planning on doing with the 2nd drive?  I've got 2 on my machine and use the 2nd for archiving.  It greatly adds to peace of mind; being a noob and all! :)

There are many posts on editing the /etc/fstab file but I've found the most informative to be [COLOR=Black]**[here]("http://www.tuxfiles.org/linuxhelp/fstab.html")**[/COLOR].

Barrie

---

