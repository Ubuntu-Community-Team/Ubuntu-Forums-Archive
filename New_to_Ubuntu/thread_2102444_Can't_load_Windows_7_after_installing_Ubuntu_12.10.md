---
title: "Can't load Windows 7 after installing Ubuntu 12.10"
date: 2013-01-07
forum: New to Ubuntu
---

### Post by chee siong on 2013-01-07
Hi there, I just installed Ubuntu 12.10. When I want to boot up Windows 7, it automatically boot to Ubuntu. When I install Ubuntu, I clicked install Ubuntu INSIDE Windows 7 and this problem came up. Can I ask why is it like this and how do I fix this problem? All your help are much appreciated. Thanks =):D

---

### Post by Frogs Hair on 2013-01-07
Hello and Welcome

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

The problem has been addressed on this thread but it may take some reading.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by Mark Phelps on 2013-01-07
When Wubi installs fail, it is usually the OPPOSITE problem -- booting into Win7 by default and not into Ubuntu.

Are you SURE you installed inside Windows?

---

### Post by chee siong on 2013-01-08
Yes, I am sure i install Ubuntu inside Windows 7.

---

### Post by 3rdalbum on 2013-01-08
> **chee siong said:**
> Yes, I am sure i install Ubuntu inside Windows 7.

In Ubuntu, open a terminal by pressing Control-Alt-T and type in the following:

```
sudo fdisk -l
```

(that's a lowercase L, not a number one)

It'll ask for your password; type it and press Enter.

Copy and paste what it tells you into a post here, so we can see exactly how you installed your system.

Normally the install should go all okay and you'd never need to do this, but something strange has happened and we need to know what it is.

---

### Post by 3rdalbum on 2013-01-08
(note to people reading this thread later to help: I don't think the poster used Wubi. When the poster tells us the output from fdisk we'll know for sure. Please read their fdisk output before trying to help)

---

### Post by chee siong on 2013-01-08
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00006bb5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    97656831    48827392   83  Linux
/dev/sda2        97658878   195313663    48827393    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5        97658880   195313663    48827392   83  Linux

that's what it wrote on the terminal after i copy and paste it.

---

### Post by mlentink on 2013-01-08
I really hope you made backups....
Because I am also sorry to tell you that you did NOT install ubuntu within Windows, but rather installed Ubuntu in place of Windows. So your Windows 7 partition has gone.

@3rdalbum: good call

---

### Post by chee siong on 2013-01-08
Oh.. Thanks for the info. Can I ask a question? Can i re-install Windows 7 back? :D

---

### Post by Cheesemill on 2013-01-08
If you have the recovery discs that came with the computer then yes, it should be easy to reinstall Windows.

If you want to have Ubuntu and Windows on your computer then you should read up on how to dual boot.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by sandyd on 2013-01-08
> **chee siong said:**
> Oh.. Thanks for the info. Can I ask a question? Can i re-install Windows 7 back? :D

Yes, just use a Windows 7 Recovery DVD / Install DVD to recover. When installing, delete all the linux partitions during the reinstallation.

---

### Post by Mark Phelps on 2013-01-08
> **chee siong said:**
> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00006bb5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    97656831    48827392   83  Linux
/dev/sda2        97658878   195313663    48827393    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5        97658880   195313663    48827392   83  Linux

that's what it wrote on the terminal after i copy and paste it.

THIS is why I asked the question in post #3 -- this NOT a Wubi install.

---

### Post by Mark Phelps on 2013-01-08
> **chee siong said:**
> Oh.. Thanks for the info. Can I ask a question? Can i re-install Windows 7 back? :D

IF your PC came preinstalled witn Win7, it's most likely that any disk that came with it, is at most, a Restore CD, meaning, it will attempt to boot into WinPE and launch an app that will attempt to formate the drive and reinstall Win7 -- from a compressed image saved inside a Recovery partition on the drive.

Since your fdisk results show NO SUCH partition on the drive, unless you have Full Install Media (not a Restore CD), there is no way to get WIN7 back.

---

### Post by chee siong on 2013-01-09
I have my Recovery disc. So now i must buy a Windows 7 disc to re-install back?

---

### Post by Cheesemill on 2013-01-09
That depends on the type of recovery disc you have.

Some recovery discs are used in combination with the recovery partition on your hard drive to restore Windows, this wont work in your case as you have deleted the recovery partition.

Other recovery discs are a set of DVDs that restore your system without using a recovery partition, if this is what you have then you are OK with just the discs.

I would say just try what you have and you'll soon know whether or not it will work.

---

### Post by rkfb on 2013-01-09
> **chee siong said:**
> Oh.. Thanks for the info. Can I ask a question? Can i re-install Windows 7 back? :D

Or maybe just run with your Ubuntu installation as is for a couple of weeks and see what you think...you may not want it back.

regards,
-- 
Robert

---

