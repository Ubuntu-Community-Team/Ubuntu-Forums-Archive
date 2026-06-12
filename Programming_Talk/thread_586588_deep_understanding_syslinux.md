---
title: "deep understanding syslinux"
date: 2007-10-22
forum: Programming Talk
---

### Post by linyongting on 2007-10-22
As we know, syslinux is a usful tool for creating a boot setor which is similar with lilo.

You can create a bootable usb trick like that:
syslinux /dev/sdb (assuming /dev/sdb is the path of Usb trick)

than create a file named as syslinux.cfg, its content is something like that:
 DISPLAY title.txt
LABEL linux
      kernel vmlinuz
    append initrd=initrd.gz ramdisk_size=10240 

syslinux combined with syslinux.cfg qualified USB trick as bootable.

But I don't what it do when run syslinux /deb/sdb

why?

---

### Post by Raphaff on 2008-07-12
> **linyongting said:**
> As we know, syslinux is a usful tool for creating a boot setor which is similar with lilo.

You can create a bootable usb trick like that:
syslinux /dev/sdb (assuming /dev/sdb is the path of Usb trick)

than create a file named as syslinux.cfg, its content is something like that:
 DISPLAY title.txt
LABEL linux
      kernel vmlinuz
    append initrd=initrd.gz ramdisk_size=10240 

syslinux combined with syslinux.cfg qualified USB trick as bootable.

But I don't what it do when run syslinux /deb/sdb

why?

Hi ! 
I have been running around trying to understand all this things syslinux.cfg , vmlinux , inirtd.gz , isolinux.cfg. For what i see a lot of types on how to boot from differnt types of media.. 

What i need, if possible is: can you say where why can find the right initrd.gz , the right vmlinuz , the right sys linux or can u do a little guide ! 


If you want to give a brief explanation on how does various unix dists, .iso, or pendrives boot would be great.

Thanks much appreciated.

:(:popcorn::)

---

