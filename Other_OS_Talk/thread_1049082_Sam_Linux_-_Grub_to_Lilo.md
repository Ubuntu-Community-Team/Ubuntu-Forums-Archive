---
title: "Sam Linux - Grub to Lilo"
date: 2009-01-24
forum: Other OS Talk
---

### Post by rolnics on 2009-01-24
I was going through an old pile of cd's (all unmarked!) yesterday and came across SAM. I've installed it on my hd, but I can't get it to boot without using my Supergrub disk. The reason is SAM has installed LILO, and of course I'm using GRUB, how do I get GRUB to tell LILO to load up? I've done some searching on the SAM site and to be honest it doesn't say, it's a very small community there.

Any suggestions anyone? In the mean time I'll keep searching ......

---

### Post by Axelpalm on 2009-01-24
I would like to take at look a very interesting thread from an [other forum]("http://justlinux.com/forum/showthread.php?t=147959&highlight=boot")
you can get a idea how to multi-boot.

I would recommend to chainload from Ubuntu's grub to SAM's lilo:
```
title  SAM @ hdaX # alternatively sdaX 
root         (hd0,X-1)
chainloader  +1

``` 
That is SAM is on first (only) hd on partition X

Or alternatively boot directly from Ubuntus grub:
```
title SAM @ hdaX
root (hd0,X-1)  #where the SAM's /boot is, where kernel is
kernel /boot/vmlinuz(-<possibly_version_no_here) root=/dev/hdX ro
initrd=/boot/initrd(<look_what_the_exact_name_is> 
```

Check for exact vmlinuz and initrd names.
Alternatively can grub tell you. That is little more advanced ,but not so hard:
when in grub's menu hit "c" for grub's commandline. I show what I get, adapt to you situation !:
```
grub> 
grub> roo<TAB>
 Possible commands are: root rootnoverify
grub>root (h<TAB>
Possible disks are:  hd0 hd1 # I have two disks
grub> root (hd0,<TAB>
 Possible partitions are:
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 1,  Filesystem type unknown, partition type 0x82
   Partition num: 2,  Filesystem type is jfs, partition type 0x83
   Partition num: 3,  Filesystem type is jfs, partition type 0x83
#I have four partitions on disk 1
grub> root (hd0,3)  #Ubuntu on fourth partition
grub> kernel /bo<TAB>
grub> kernel /boot/
grub> kernel /boot/vm<TAB>
 Possible files are: vmlinuz vmlinuz-2.6.24-19-generic vmlinuz-2.6.24-22-generic
grub> kernel /boot/vmlinuz-2.6.24-22-generic root=/dev/sda4 ro # root - where / partition is .
grub>initrd /boot/init<TAB>
 Possible files are: initrd.img initrd.img-2.6.24-19-generic initrd.img-2.6.24-
19-generic.bak initrd.img-2.6.24-22-generic initrd.img-2.6.24-22-generic.bak
grub> initrd /boot/initrd.img-2.6.24-22-generic
grub> boot
```

Actually you can safely try it out in Ubuntu gnome-terminal (without tha boot command !).
```
sudo grub
```

---

### Post by rolnics on 2009-01-25
Thanks Axelpalm!

I've had a quick read of the other forum post, that looks very interesting!

---

