---
title: "automounting 2nd and 3rd hard drive"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by alwiap on 2008-06-05
Hi,

I've browsed through some threads of how to do this, and I just want to make sure I do the right thing.  I see that I have to edit /etc/stab, and here is what I currently have:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=c44f4a27-c688-4596-8439-f7962d5cc931 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=3d7e26b3-f32a-4751-aa46-5f1529c753ee none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```

From this data, I also can't tell which drives are which, so I know which 2 to enable to automount (sorry, I'm n00b).

Thanks so much!

---

### Post by hopelessone on 2008-06-05
Check the community docs for a step by step guide...


[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

Hope this helps...

---

### Post by alwiap on 2008-06-05
> **hopelessone said:**
> Check the community docs for a step by step guide...


[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

Hope this helps...

thanks for the link! i will investigate.

---

### Post by bumanie on 2008-06-05
Essentially you have to make a directory as a mount point for the drives that are not automounting and then add them to fstab. For example to add sdb1 partition called bob, one would 
> sudo mkdir /media/bob then > sudo gedit /etc/fstab and add
/dev/sdb1 /media/bob ext3 defaults, 0 1
Hope that helps.

---

