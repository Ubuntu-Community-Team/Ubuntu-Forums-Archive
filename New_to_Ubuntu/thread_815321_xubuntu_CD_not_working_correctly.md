---
title: "xubuntu CD not working correctly"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by xecure on 2008-06-01
I just downloaded and burned Xubuntu on a CD for my desktop, and after I entered it into my CD drive so i can boot to it. But when ever I hit Intslall Xubuntu the linux kernel loads (sometimes it freezes half way and I have to hit the power button to restart) and after wards the screen just goes black. The same happens when I hit check CD for defects. I own a Dell dimension 2400. Any idea why it is giving me this problem? Would it be easier just to burn another disc and try it?

---

### Post by bobnutfield on 2008-06-01
Initial indication is that either it is a bad cd burn (a burn with errors, did you check the md5 sum?), or there is a piece of hardware that Ubuntu is having difficulty with.  Have you tried a live cd to see how your hardware runs with Ubuntu?

---

### Post by xecure on 2008-06-01
how do i check md5 sum?
and I have tried to runn Xubuntu without installing, but I get the same error

---

### Post by bobnutfield on 2008-06-01
OK, did you download and burn your cd with Windows?  If so, here is a link to instructions on checking the MD5 sum from Windows.

[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows]("http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows")

But, it is also possible that your graphics card may be the issue.  Have you tried to load the live cd in safe mode?

---

### Post by xecure on 2008-06-01
I actually went ahead and burned a new disc. I tried to load that without installing and it loaded up fine, and i tried, but couldn't delete my earlier Ubuntu partition with GParted. So I decided to reboot my computer again and just go ahead and install Xubuntu on a separate partition. Then I started getting the same problem again. After a few more reboots I got this error message: "[42.741606] Kernal Panic - not syncing: VFS: Unable to mount root fs on unknown block (104,1)"
Any other ideas?

---

### Post by bobnutfield on 2008-06-01
The message you are getting is telling that the partition where you have the kernel isn't being found so the boot process is halting.  If you can, load up the live cd again, boot to the desktop, open a terminal, and type:

> fdisk -l

and post the results back.

---

### Post by xecure on 2008-06-01
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16673   133925841    7  HPFS/NTFS
/dev/sda2           16674       19452    22322317+   5  Extended
/dev/sda5           16674       19331    21350353+  83  Linux
/dev/sda6           19332       19452      971901   82  Linux swap / Solaris
```

---

### Post by bobnutfield on 2008-06-01
> **xecure said:**
> ```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16673   133925841    7  HPFS/NTFS
/dev/sda2           16674       19452    22322317+   5  Extended
/dev/sda5           16674       19331    21350353+  83  Linux
/dev/sda6           19332       19452      971901   82  Linux swap / Solaris
```

OK, you have your Linux partition on sda5.  You can install from the live cd (just choose to install from the icon.)  When the partioning question comes up, choose MANUAL PARTIONING.  Be very careful here because Ubuntu will take over your whole hard drive if you choose auto partitioning.  Stay away from sda1, as you obviously have windows installed there.  Ubuntu will automatically find your Windows installtion and include it in your grub configuration.  Just follow all the prompts and take your time to read everything and it should install for you just fine.

Remember, when it asked where to put the root partition (/), choose sda5.   You don't need to delete or reformat (the installer will do that for you) the partition.

Good Luck.

Bob

---

### Post by psyntience on 2008-06-01
xecure,

Have you tried burning another copy of the CD?  I went through three burns with the same error on the same CD sector before I managed to get a disc that would install without errors.  It wasn't really a Ubuntu or Windows issue...it was just my choice in cheap CD-Rs.

---

