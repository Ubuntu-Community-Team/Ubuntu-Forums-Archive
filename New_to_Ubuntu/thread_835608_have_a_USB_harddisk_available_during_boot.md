---
title: "have a USB harddisk available during boot"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by th00ht on 2008-06-20
Hi there, 
An external USB hard disk is connected to my system. Whenever I logon to the desktop it is recognized and mounted on /media/TREKSTOR and I can work with its files. Whenever I log of it is unmounted. 

As I will hardly ever login to the desktop but will use the hard disk as a shared drive I need it to be available as soon as it is rebooted. 

How do I change the behavior to have the usb hard disk mounted as soon as the machine is started?

---

### Post by Darkade on 2008-06-20
You need to edit your fstab file, since it tells your box where to mount your hard drives and other units.
Here are two useful links

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

First one is kindda technical but it's understandable.
Second one is a great how to.

Hope it helps

---

### Post by th00ht on 2008-06-29
> **Darkade said:**
> You need to edit your fstab file, 

Adding it to fstab helps so that I only have to type
sudo mount /usb0. But I do not whant to type anything. What when the external USB disk is available at /dev/sdb1? 

My fstab looks like
```
# /etc/fstab: static file system information.
#
# <file system>                                 <mount point>   <type>          <options>       <dump>          <pass>
proc                                            /proc           proc            defaults        0               0
# /dev/hdc1
UUID=90b1313b-c04e-4b8d-bc09-77f878b21f1f       /               ext3            defaults,errors=remount-ro 0    1
# /dev/hdc5
UUID=0cfca185-56ce-485d-a5c0-6b9b0549341c       none            swap            sw              0               0
/dev/sda1                                       /usb0           vfat            auto,async,rw,nosuid,nodev,umask=000,uid=1000   0     0
```

---

