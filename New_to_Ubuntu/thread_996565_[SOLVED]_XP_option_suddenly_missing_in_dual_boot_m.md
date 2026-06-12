---
title: "[SOLVED] XP option suddenly missing in dual boot menu"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by gkaucher on 2008-11-29
I've been running XP and Hardy Heron fine for many months as a dual boot (Grub) on my Toshiba Satellite. For some reason the option to boot with XP has recently disappeared from the menu. Any help appreciated.

Gary

---

### Post by ratmandall on 2008-11-29
Post the output of.
```
fdisk -l
```

---

### Post by nhasian on 2008-11-29
super grub disk to the rescue!

[http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_without_problems](http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_without_problems)

---

### Post by ratmandall on 2008-11-29
> **ratmandall said:**
> Post the output of.
```
fdisk -l
```
Never mind this I just realized that it would just show you if the NTFS partition was on your hard drive or not which if the NTFS partition wasn't there, the GRUB option for Windows still should be there. 0-O

---

### Post by gkaucher on 2008-11-29
Disk /dev/sda: 79.8 GB, 79826342400 bytes
255 heads, 63 sectors/track, 9705 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2787912c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612        6527    31455270   83  Linux
/dev/sda3            6528        6788     2096482+  82  Linux swap / Solaris
/dev/sda4            6789        9729    23623582+   b  W95 FAT32

---

### Post by MasterSander on 2008-11-29
Add this to /boot/grub/menu.lst

```
sudo gedit /boot/grub/menu.lst
```

```

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

hd0,0 means the first hard drive's first partition.

---

### Post by gkaucher on 2008-11-29
Thank you MasterSander. Problem solved!

Two questions:

1) What might have caused the XP option to disappear in the first place?
2) Here is what my menu.1st file looked like before I added the "XP entry" you suggested right after the Ubuntu memtest. At the very end of this file there is the exact same "XP entry". Why didn't it work? 


Thanks,
Gary


title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=d1229f2f-f0d6-420a-9290-731c6568bc94 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=d1229f2f-f0d6-420a-9290-731c6568bc94 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=d1229f2f-f0d6-420a-9290-731c6568bc94 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=d1229f2f-f0d6-420a-9290-731c6568bc94 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d1229f2f-f0d6-420a-9290-731c6568bc94 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d1229f2f-f0d6-420a-9290-731c6568bc94 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.22-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=d1229f2f-f0d6-420a-9290-731c6568bc94 ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=d1229f2f-f0d6-420a-9290-731c6568bc94 ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d1229f2f-f0d6-420a-9290-731c6568bc94 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d1229f2f-f0d6-420a-9290-731c6568bc94 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1





title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=d1229f2f-f0d6-420a-9290-731c6568bc94 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=d1229f2f-f0d6-420a-9290-731c6568bc94 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=d1229f2f-f0d6-420a-9290-731c6568bc94 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=d1229f2f-f0d6-420a-9290-731c6568bc94 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d1229f2f-f0d6-420a-9290-731c6568bc94 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d1229f2f-f0d6-420a-9290-731c6568bc94 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.22-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=d1229f2f-f0d6-420a-9290-731c6568bc94 ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=d1229f2f-f0d6-420a-9290-731c6568bc94 ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d1229f2f-f0d6-420a-9290-731c6568bc94 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d1229f2f-f0d6-420a-9290-731c6568bc94 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by gkaucher on 2008-11-29
I figured out what happened. A recent update was added to the top of the "grub menu", causing the Windows XP option at the bottom of the menu to "scroll off". So, the option was always there, but I didn't see it, or realize that I needed to scroll it up!

Thanks

---

