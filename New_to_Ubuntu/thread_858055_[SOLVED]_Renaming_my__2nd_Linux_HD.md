---
title: "[SOLVED] Renaming my  2nd Linux HD"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by djsjbh on 2008-07-13
Hi folks,

I want to rename my 2nd Linux HD (formatted ext3). It decided to name itself "320.1 GB Media" and I'd  like to change it to "Linux Storage" (since I have NTFS HDs within the same rig). This disk is all storage, the operating system is on a totally different disk.

When I   right-click > rename   it says:

The item could not be renamed.

Sorry, couldn't rename "320.1 GB Media" to "Linux Storage": Operation not supported by backend.

Any ideas on how to change the name?

Thank you

---

### Post by hyper_ch on 2008-07-13
unmount it first

---

### Post by djsjbh on 2008-07-13
Yep, did that. Sorry I didn't mention it in the original post  but it was unmounted...still not working.

---

### Post by ChameleonDave on 2008-07-13
> **djsjbh said:**
> 

Any ideas on how to change the name?

Make absolutely sure that the device is unmounted.

Then, determine the correct device identifier for the drive.  You can do this with a program like GParted, or you can get info on the command line with commands such as "*sudo fdisk -l*" or "*sudo blkid*".  The identifier will start with "*/dev/*".

Once you know that, do the following command:

```

sudo tune2fs -L Linux_Storage /dev/**sdb2**

```I have used "sdb2" as a guess.  Replace that with the correct identifier for your drive.

---

### Post by djsjbh on 2008-07-13
That worked...thank you.

---

### Post by ChameleonDave on 2008-07-13
> **djsjbh said:**
> That worked...thank you.

You can also use this (and similar commands for ReiserFS, NTFS...) to label other drives, such as your root partition.  You can then use labels instead of /dev/ names or UUIDs to refer to your partitions in /etc/fstab.

Here is the start of my /etc/fstab file, for example:

```

*# <file system> <mount point>   <type>  <options>       <dump>  <pass>*
**proc           /proc           proc    defaults        0       0         **

*# /dev/sdb7*
*# UUID=6223d2bf-822b-4a42-a15e-05b17b7f3aef could also be used.*
**LABEL=Kubuntu  /               reiserfs notail,relatime 0       1**

*# /dev/sdb5*
*# UUID=b1d5011b-f544-4c19-b895-e8ba52f4aa54 could also be used.*
**LABEL=Files    /home/david/Files      ext3    relatime        0       2**

*# /dev/sda2*
*# UUID=9ACC9F03CC9ED8B9 could also be used.*
**LABEL=Windows  /mnt/Windows    ntfs-3g    defaults,umask=007,gid=46,noauto,user 0       1**

```
Just an idea. ;-)

Now, since your main issue has been dealt with, perhaps you could be so kind as to use the "Thread Tools" menu to mark this as solved.  Thanks.

---

### Post by BLTicklemonster on 2008-07-13
Didn't for me. Or does it not work on partitions?

I unmounted my partition in gparted, then got this:

bill@bill-desktop:~$ sudo tune2fs -L Movies /dev/sdc5
[sudo] password for bill: 
tune2fs 1.40.8 (13-Mar-2008)
tune2fs: Bad magic number in super-block while trying to open /dev/sdc5
Couldn't find valid filesystem superblock.
bill@bill-desktop:~$

---

### Post by ChameleonDave on 2008-07-13
> **BLTicklemonster said:**
> Didn't for me. Or does it not work on partitions?

I unmounted my partition in gparted, then got this:

bill@bill-desktop:~$ sudo tune2fs -L Movies /dev/sdc5
[sudo] password for bill: 
tune2fs 1.40.8 (13-Mar-2008)
tune2fs: Bad magic number in super-block while trying to open /dev/sdc5
Couldn't find valid filesystem superblock.
bill@bill-desktop:~$
Either it's not an Ext filesystem, or there is a corruption.

Assuming it is indeed Ext3, try:
```

sudo fsck.ext3 -vc /dev/sdc5

```It might be good to grab some info by doing this:

```

sudo blkid

```

---

### Post by BLTicklemonster on 2008-07-14
It's vfat. fat32 if I'm not mistaken.

---

### Post by ChameleonDave on 2008-07-14
> **BLTicklemonster said:**
> It's vfat. fat32 if I'm not mistaken.
Well, there you go.  The original poster was asking about ext3, so that's that command I gave.

This is what you need:

```

sudo apt-get install mtools
sudo mlabel -i /dev/sdc5 ::Movies

```

Here's a whole guide to labelling drives: [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by BLTicklemonster on 2008-07-14
lmao I thanked you before I tried it. 

Didn't work. No error messages or anything. Just didn't work.

Well, it may after a reboot, I'll find out later, but for now, I mounted the drive from gparted after I'd done it.

Thanks for the link, I'll check it out!

Anyway, you earned the thanks.

*edit: lmao even more:

ill@bill-desktop:~$ sudo mlabel -i /dev/sdc5 -s ::Movies
 Volume label is Movies (abbr=MOVIES     )


and it still shows up as 94.1 GB Media instead of Movies.

woohoo.


*another edit:

I see this from the linked page:

Now for the easiest part: unplug the drive, wait a second, then plug it back in. It should appear on your desktop with the new label and have its new mount point. 

so yeah, it will probably come up right on reboot.

Thanks!!!

---

### Post by Canis familiaris on 2008-07-14
> **ChameleonDave said:**
> Well, there you go.  The original poster was asking about ext3, so that's that command I gave.

This is what you need:

```

sudo apt-get install mtools
sudo mlabel -i /dev/sdc5 ::Movies

```

Here's a whole guide to labelling drives: [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

And how do I set label on an NTFS partition and a ReiserFS partition?

---

### Post by BLTicklemonster on 2008-07-14
This explains it very well

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by BLTicklemonster on 2008-07-14
Confirming that the name took after a reboot.

Thanks again, ChameleonDave!!!

---

