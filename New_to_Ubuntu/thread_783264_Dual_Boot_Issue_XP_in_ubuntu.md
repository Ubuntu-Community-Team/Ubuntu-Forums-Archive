---
title: "Dual Boot Issue/ XP in ubuntu"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by BlackSwordD2 on 2008-05-05
ok so not even a week ago i decided to upgrade from Windows XP to Ubuntu but i didn't want to wipe so i did the dual boot option.

ubuntu runs great and i love it, but I'm still working on the transfer from Xp to Ubuntu (such as games and other misc. programs that I've been using for years) so for the last few days i've been all about Ubuntu and have the whole eye candy things running and just started tinkering with Wine.

And now i decided to try to boot into windows for a bit and it would not load.

it would give me the "Starting" line but would not continue to the "Loading" line as it does for Ubuntu when i reboot

so i have two possible scenarios:

1) Fix the Error.
          I've been looking around this forum and I've found some useful things such as a program called ntfsfix, however I'm still new to the Terminal and I don't know how to use the program well enough so if someone could offer guidance for that I would be grateful and I'm also open to other options, but i really do need an idots guide to its use

or more preferably

2) Open XP in a separate window in Ubuntu
          I want to be able to have XP as a separate window and I've looked around and heard of VirtualBox and VMware as well as Wine (which I'm tinkering with). But what i need is to be able to open Windows WITHOUT having to re-install it. So if there is a way to do this I would be eternally grateful.

Thank you

---

### Post by zaussome on 2008-05-05
z

---

### Post by kwacka on 2008-05-05
Could you also post the contents of your '/boot/grub/menu.lst' file (just open with 'text editor' and cut/paste from '## ## End Default Options ##' onwards into your reply).

Also what is the output of ```
 sudo fdisk -l
```

---

### Post by BlackSwordD2 on 2008-05-05
> **kwacka said:**
> Could you also post the contents of your '/boot/grub/menu.lst' file (just open with 'text editor' and cut/paste from '## ## End Default Options ##' onwards into your reply).

Also what is the output of ```
 sudo fdisk -l
```

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=05472d09-51b7-481c-98a5-fb7993108516 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=05472d09-51b7-481c-98a5-fb7993108516 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=05472d09-51b7-481c-98a5-fb7993108516 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=05472d09-51b7-481c-98a5-fb7993108516 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=05472d09-51b7-481c-98a5-fb7993108516 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=05472d09-51b7-481c-98a5-fb7993108516 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1





Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf806f806

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17545   140930181    7  HPFS/NTFS
/dev/sda2           17546       19371    14667345   83  Linux
/dev/sda3           19372       19457      690795    5  Extended
/dev/sda5           19372       19457      690763+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072932864 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x207a4a15

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS


Also there are no error messages, it just stops after the line "Starting" i even left it for a while to see if it was just taking a while but it didn't seem to matter

---

