---
title: "Grub Problem"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by flipflop0112 on 2008-09-13
I have ubuntu 8.04 installed and windows OS but when trying to access windows from Grub I am getting the following error:

 Error 13: "Invalid or unsupported executable format"

```
 sudo fdisk -lu


  Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    38090114    19045026   83  Linux
/dev/sda2        38090115    41993909     1951897+  82  Linux swap / Solaris
/dev/sda3   *    41993911   147091139    52548614+   7  HPFS/NTFS
/dev/sda4       147091140   234436544    43672702+   7  HPFS/NTFS

```

boot.ini from windows:

```
[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

```

```

 sudo gedit /boot/grub/menu.lst


## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=e5cbf9c9-cefb-4b3b-b7b9-76b3676ce5c0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=e5cbf9c9-cefb-4b3b-b7b9-76b3676ce5c0 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e5cbf9c9-cefb-4b3b-b7b9-76b3676ce5c0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e5cbf9c9-cefb-4b3b-b7b9-76b3676ce5c0 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2

title	        Microsoft Windows XP Home Edition
root 		(hd0,02)
savedefault
makeactive
map 		(hd0) (hd2)
map 		(hd2) (hd0)
chainloader +1


# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


```

I am not sure how to alter the entry so I can boot to windows via grub.

---

### Post by Steve1961 on 2008-09-13
Try changing this:

title	        Microsoft Windows XP Home Edition
root 		(hd0,02)

to this:

title	        Microsoft Windows XP Home Edition
root 		(hd0,2)

just edit it by typing

sudo gedit /boot/grub/menu.lst

You may also need to change this:

map 		(hd0) (hd2)
map 		(hd2) (hd0)

to this:

map 		(hd0,0) (hd0,2)
map 		(hd0,2) (hd0,0)

---

### Post by flipflop0112 on 2008-09-13
thx mate. It works now :)

---

### Post by Steve1961 on 2008-09-13
> **flipflop0112 said:**
> thx mate. It works now :)

Your welcome :)

---

