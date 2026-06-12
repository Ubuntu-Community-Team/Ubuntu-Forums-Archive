---
title: "Dual Boot: Ubuntu on PATA - XP on SATA"
date: 2006-06-27
forum: Outdated Tutorials &amp; Tips
---

### Post by jdvoracek on 2006-06-27
The hard part of this for a noobie was discovering the key tidbits and then figuring out the Grub map command.  

Motherboard: Asus A7N8X-E

Ubuntu on primary IDE controller:
   fstab = hda1
   grub = (hd0,0)

Windows XP on SATA channel 0:
   fstab = sda1
   grub = (hd1,0)

Key tidbits:  Windows XP will only boot from "first hard drive" but BIOS always counts IDE hard drives first, so the way to fool XP (NT loader) is to use Grub map command.  I don't remember where I came across this, but it was the key to make it all work.

/boot/grub/menu.lst:

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-25-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title Microsoft Windows XP Professional
map (hd0) (hd1)   # (hd0) is hda1 = ubuntu
map (hd1) (hd0)   # (hd1) is sda1 = windows xp
root (hd1,0)          # note - mapping does not affect grub's numbering
savedefault
makeactive
chainloader +1

/etc/fstab - mount sata xp drive at boot:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1 /media/WindowsXP/     ntfs    nls=utf8,umask=0222 0 0

---

