---
title: "Howto Ubuntu 6.06.1 on ASRock 775Dual-VSTA motherboard"
date: 2006-08-31
forum: Outdated Tutorials &amp; Tips
---

### Post by CapnCaffeine on 2006-08-31
Interested in getting DMA in the IDE channels and 3D Acceleration working by enabling AGPGART for this motherboard? :D 

Thought you would!

Here is the link:

[http://home.rochester.rr.com/msarnov/AsrockUbuntuHowTo.html](http://home.rochester.rr.com/msarnov/AsrockUbuntuHowTo.html)

BTW: How do I get this information to the Ubuntu development team?

Cappy

---

### Post by Cuppa-Chino on 2006-09-04
... double entry

---

### Post by Cuppa-Chino on 2006-09-04
cannot find:** gedit /usr/src/linux/include/linux/pci-ids.h**
to edit...

my gedit /usr/src/linux/include/linux/ directory only has:

```
:/usr/src/linux/include$ ls -l
total 28
lrwxrwxrwx   1 root root    42 2006-08-07 22:48 acpi -> ../../linux-headers-2.6. 15-26/include/acpi
lrwxrwxrwx   1 root root     8 2006-08-07 22:48 asm -> asm-i386
lrwxrwxrwx   1 root root    47 2006-08-07 22:48 asm-alpha -> ../../linux-headers -2.6.15-26/include/asm-alpha
lrwxrwxrwx   1 root root    45 2006-08-07 22:48 asm-arm -> ../../linux-headers-2 .6.15-26/include/asm-arm
lrwxrwxrwx   1 root root    47 2006-08-07 22:48 asm-arm26 -> ../../linux-headers -2.6.15-26/include/asm-arm26
lrwxrwxrwx   1 root root    46 2006-08-07 22:48 asm-cris -> ../../linux-headers- 2.6.15-26/include/asm-cris
lrwxrwxrwx   1 root root    45 2006-08-07 22:48 asm-frv -> ../../linux-headers-2 .6.15-26/include/asm-frv
lrwxrwxrwx   1 root root    49 2006-08-07 22:48 asm-generic -> ../../linux-heade rs-2.6.15-26/include/asm-generic
lrwxrwxrwx   1 root root    47 2006-08-07 22:48 asm-h8300 -> ../../linux-headers -2.6.15-26/include/asm-h8300
lrwxrwxrwx   1 root root    46 2006-08-07 22:48 asm-i386 -> ../../linux-headers- 2.6.15-26/include/asm-i386
lrwxrwxrwx   1 root root    46 2006-08-07 22:48 asm-ia64 -> ../../linux-headers- 2.6.15-26/include/asm-ia64
lrwxrwxrwx   1 root root    46 2006-08-07 22:48 asm-m32r -> ../../linux-headers- 2.6.15-26/include/asm-m32r
lrwxrwxrwx   1 root root    46 2006-08-07 22:48 asm-m68k -> ../../linux-headers- 2.6.15-26/include/asm-m68k
lrwxrwxrwx   1 root root    51 2006-08-07 22:48 asm-m68knommu -> ../../linux-hea ders-2.6.15-26/include/asm-m68knommu
lrwxrwxrwx   1 root root    46 2006-08-07 22:48 asm-mips -> ../../linux-headers- 2.6.15-26/include/asm-mips
lrwxrwxrwx   1 root root    48 2006-08-07 22:48 asm-parisc -> ../../linux-header s-2.6.15-26/include/asm-parisc
lrwxrwxrwx   1 root root    49 2006-08-07 22:48 asm-powerpc -> ../../linux-heade rs-2.6.15-26/include/asm-powerpc
lrwxrwxrwx   1 root root    45 2006-08-07 22:48 asm-ppc -> ../../linux-headers-2 .6.15-26/include/asm-ppc
lrwxrwxrwx   1 root root    46 2006-08-07 22:48 asm-s390 -> ../../linux-headers- 2.6.15-26/include/asm-s390
lrwxrwxrwx   1 root root    44 2006-08-07 22:48 asm-sh -> ../../linux-headers-2. 6.15-26/include/asm-sh
lrwxrwxrwx   1 root root    46 2006-08-07 22:48 asm-sh64 -> ../../linux-headers- 2.6.15-26/include/asm-sh64
lrwxrwxrwx   1 root root    47 2006-08-07 22:48 asm-sparc -> ../../linux-headers -2.6.15-26/include/asm-sparc
lrwxrwxrwx   1 root root    49 2006-08-07 22:48 asm-sparc64 -> ../../linux-heade rs-2.6.15-26/include/asm-sparc64
lrwxrwxrwx   1 root root    44 2006-08-07 22:48 asm-um -> ../../linux-headers-2. 6.15-26/include/asm-um
lrwxrwxrwx   1 root root    46 2006-08-07 22:48 asm-v850 -> ../../linux-headers- 2.6.15-26/include/asm-v850
lrwxrwxrwx   1 root root    48 2006-08-07 22:48 asm-x86_64 -> ../../linux-header s-2.6.15-26/include/asm-x86_64
lrwxrwxrwx   1 root root    48 2006-08-07 22:48 asm-xtensa -> ../../linux-header s-2.6.15-26/include/asm-xtensa
lrwxrwxrwx   1 root root    45 2006-08-07 22:48 cluster -> ../../linux-headers-2 .6.15-26/include/cluster
drwxr-xr-x 533 root root 12288 2006-08-07 22:48 config
lrwxrwxrwx   1 root root    42 2006-08-07 22:48 keys -> ../../linux-headers-2.6. 15-26/include/keys
drwxr-xr-x   2 root root 16384 2006-08-07 22:48 linux
lrwxrwxrwx   1 root root    46 2006-08-07 22:48 math-emu -> ../../linux-headers- 2.6.15-26/include/math-emu
lrwxrwxrwx   1 root root    43 2006-08-07 22:48 media -> ../../linux-headers-2.6 .15-26/include/media
lrwxrwxrwx   1 root root    41 2006-08-07 22:48 mtd -> ../../linux-headers-2.6.1 5-26/include/mtd
lrwxrwxrwx   1 root root    41 2006-08-07 22:48 net -> ../../linux-headers-2.6.1 5-26/include/net
lrwxrwxrwx   1 root root    44 2006-08-07 22:48 pcmcia -> ../../linux-headers-2. 6.15-26/include/pcmcia
lrwxrwxrwx   1 root root    44 2006-08-07 22:48 prism2 -> ../../linux-headers-2. 6.15-26/include/prism2
lrwxrwxrwx   1 root root    42 2006-08-07 22:48 rdma -> ../../linux-headers-2.6. 15-26/include/rdma
lrwxrwxrwx   1 root root    43 2006-08-07 22:48 rxrpc -> ../../linux-headers-2.6 .15-26/include/rxrpc
lrwxrwxrwx   1 root root    42 2006-08-07 22:48 scsi -> ../../linux-headers-2.6. 15-26/include/scsi
lrwxrwxrwx   1 root root    43 2006-08-07 22:48 sound -> ../../linux-headers-2.6 .15-26/include/sound
lrwxrwxrwx   1 root root    43 2006-08-07 22:48 video -> ../../linux-headers-2.6 .15-26/include/video
lrwxrwxrwx   1 root root    42 2006-08-07 22:48 wlan -> ../../linux-headers-2.6. 15-26/include/wlan

```

cannot find the next file either... nor via82cxxx.c

what am I doing wrong

---

### Post by CapnCaffeine on 2006-09-16
It appears that you have the /usr/src/linux/ directory pointed toward your headers directory and not the source directory. Make sure that you have symlinked (symbolically linked) /usr/src/linux to /usr/src/linux-source-2.6.15

with:

rm /usr/src/linux
ln -s /usr/src/linux-source-2.6.15 /usr/src/linux

then give it a whirl!

Cappy
:)

---

