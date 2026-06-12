---
title: "Grub and WIndows XP"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by cschill on 2008-06-01
Hi,

Just bought a SATA HD and installed Ubuntu.  Everything works fine!

Now, I have an old IDE drive with windows XP installed on it.  I would like to get grub to include an option to boot windows.   I have read through some other posts, but I am stuck, so I thought I would try a new post.

Here is the output of fdsik -l:
[INDENT]
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0c980c98

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a560a55

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60049   482343561   83  Linux
/dev/sdb2           60050       60801     6040440    5  Extended
/dev/sdb5           60050       60801     6040408+  82  Linux swap / Solaris
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0c980c98

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a560a55

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60049   482343561   83  Linux
/dev/sdb2           60050       60801     6040440    5  Extended
/dev/sdb5           60050       60801     6040408+  82  Linux swap / Solaris
[/INDENT]

One thing that is strange is that it calls the ntfs drive /dev/sda1.  I would have expected it to be hda1 or something like that since it is an IDE.  
/dev/sdb is obviously the SATA drive with Ubuntu.

Now, here is the /boot/grup/device.map:
[INDENT]
(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
[/INDENT]

This is strange to, because all the Ubuntus in menu.lst are root (hd0,0). Here is the relevant part of menu.lst:
[INDENT]
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=841a6451-8927-43dd-9445-854afa63fd1f ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=841a6451-8927-43dd-9445-854afa63fd1f ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=841a6451-8927-43dd-9445-854afa63fd1f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=841a6451-8927-43dd-9445-854afa63fd1f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title Windows Loader
rootnoverify (hd0,0)
makeactive
chainloader +1
map (hd0) (hd1)
map (hd1) (hd0)

### END DEBIAN AUTOMAGIC KERNELS LIST

[/INDENT]

Any help would be greatly appreciated.
Thanks
Chris

---

### Post by Xiong Chiamiov on 2008-06-01
After much mucking about with the GRUB file, I found that it's much easier to use [SuperGrubDisk]("http://supergrubdisk.org").  However, we can help you do it manually if you prefer.

---

### Post by louieb on 2008-06-01
```

title Windows Loader[COLOR=DarkGreen]
rootnoverify (hd1,0)[/COLOR]
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


```Assuming your Ubuntu entries work the above should work for XP. Let us know.   I just changed the root statement and moved the chainloader statment.

---

### Post by alzie on 2008-06-01
I believe louieb is right.

A bit of housekeeping.  You might want to move > ### END DEBIAN AUTOMAGIC KERNELS LISTso that it seperates your windows from your ubuntu.  This will prevent the next kernal update from messing your windows up.

Been there done that  LOL

---

