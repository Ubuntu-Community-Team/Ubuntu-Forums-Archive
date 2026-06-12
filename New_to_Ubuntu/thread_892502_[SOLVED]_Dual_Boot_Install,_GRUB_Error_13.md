---
title: "[SOLVED] Dual Boot Install, GRUB Error 13"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by EcthelionGenesis on 2008-08-17
Bit of a problem here, hope you can help:

I am trying to dual boot Ubuntu 32 bit with Windows XP Pro x64 Edition, on a single disk partitioned into 4 (with partitions for Windows, /home, Ubuntu and Swap). I wanted 64 bit so I could use all my RAM.

Install of XP went smoothly, then I reinstalled GRUB to the MBR from the live CD using 

```

sudo grub

> find boot/grub/stage1
> root (hd0,2)
> setup (hd0)
```

Now I can boot into Ubuntu, but trying to boot into Windows XP 64bit leaves me with the following GRUB error message:

```
Error 13: Invalid or unsupported executable format
```

Is this to do with something like a 32 bit version of GRUB not being able to run the XP x64 boot files?

Would it help if I posted the content of my menu.lst file?

(Oh, and in case you were wondering, I also plan to go 64 bit on Ubuntu as soon as I get the CD posted to me... Darn slow connection :( )

Anyway, help (in any form) would be greatly appreciated!

---

### Post by caljohnsmith on 2008-08-17
Yes, definitely post your menu.lst, and just for completeness, please post:
```
sudo fdisk -l
```

---

### Post by EcthelionGenesis on 2008-08-17
Okay, menu.lst:

```
default 0
fallback 1
timeout 4
color black/light-gray light-gray/black

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=e2a12012-1ce8-4559-bce7-6c1d3f02a255 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Microsoft Windows XP Professional x64 Edition
root (hd0,2)
chainloader +1
savedefault
makeactive

title Recovery / Diagnostic Modes:
root (hd0,2)

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=e2a12012-1ce8-4559-bce7-6c1d3f02a255 ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, memtest86+
root (hd0,2)
kernel /boot/memtest86+.bin
quiet
```

And sudo fdisk -l:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a2e63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3133    25165791    7  HPFS/NTFS
/dev/sda2            3134       35768   262140637+   b  W95 FAT32
/dev/sda3           35769       37608    14779800   83  Linux
/dev/sda4           37609       38913    10482412+  82  Linux swap / Solaris

```

Thanks.

---

### Post by caljohnsmith on 2008-08-17
I think your problem might be as simple as fixing the Win XP entry in your menu.lst:
```
title Microsoft Windows XP Professional x64 Edition
root [COLOR="Blue"](hd0,0)[/COLOR]
chainloader +1
savedefault
makeactive
```
Your Win XP partition is on (hd0,0), not (hd0,2) like you had it. :)

---

### Post by EcthelionGenesis on 2008-08-17
Ah, yes, that would be it... ](*,)

Strange, though, I didn't change it to (0,2). Must have done something...

Anyway, that seems to have sorted it. Thanks a lot.

---

