---
title: "After Windows Installation, updated GRUB: now Windows is gone"
date: 2014-04-20
forum: New to Ubuntu
---

### Post by stefan_03 on 2014-04-20
Hello,

I'm using elementaryOS, which is based on Ubuntu. I've installed Win7 on another partition - after which I couldn't start eOS any more. I've updated GRUB with an Ubuntu live DVD and now I've got the problem, that I cannot boot into Windows any more.

My linux partition os on /dev/sdb1 and my Win7 on /dev/sdb3

```
$ fdisk -l

Disk /dev/sdb: 128.0 GB, 128035676160 bytes255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000063f4


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   192522239    96260096   83  Linux
/dev/sdb2       192522240   192727039      102400    7  HPFS/NTFS/exFAT
/dev/sdb3   *   192727040   233482239    20377600    7  HPFS/NTFS/exFAT
/dev/sdb4       233484286   250068991     8292353    5  Extended
/dev/sdb5       233484288   250068991     8292352   82  Linux swap / Solaris
```

What I did: I've added the following code to **/etc/grub.d/40_custom** and **/boot/grub/grub.cfg** and updated grub. (I've found this in another thread)
```
menuentry "Windows 7" {
    set root=(hd1,msdos3)
    chainloader +1
}
```


Now 2 problems:

1) GRUB doesn't show up on normal boot (only when I press the OFF button on my PC instead of normal shutting down)
2) When GRUB shows up, I see Windows 7, but it says **No partition found.**

Does anyone have an explanation / solution for these 2 problems?


Thanks!

---

### Post by nothingspecial on 2014-04-20
First thing to try in this situation is boot repair

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Mark Phelps on 2014-04-20
My guess -- is that the Window boot loader files might be on sdb2, not sdb3.  You can confirm that by booting into eOS and seeing which partition contains the "boot" folder and "bootmgr" file.  Those are some of the Windows loader files.  The partition that contains "winload.exe" is the Windows OS partition.

---

### Post by stefan_03 on 2014-04-20
[FONT=arial]Thanks @nothingspecial, this worked out for me. I think sdb2 was really the right one.

If somebody is searching on Google the following error message, let me help you
**```
W: Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found
```**[/FONT]

[FONT=arial]This is because the current boot-repair isn't available yet for Ubuntu 14.04.
When you enter **[COLOR=#333333]sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update[/COLOR]**[COLOR=#333333] into terminal, go to **System Settings -> Software -> Other Software** click on the added repository and change the type to Binary and the OS distribution version from Trusty to Saucy. and check the checkbox.[/COLOR][/FONT]

---

