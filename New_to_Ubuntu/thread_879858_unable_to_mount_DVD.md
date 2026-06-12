---
title: "unable to mount DVD"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by DrScum on 2008-08-04
Installed Xubuntu 8.04 from CD inserted into the DVD drive (see below). However, the following problem so far I was unable to solve:

When inserting a DVD into the DVD drive the icon appears on the desktop  but an error message occurs:
Failed to mount "DVD Title".
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: /dev/scd0 already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/scd0 is already mounted on /media/cdrom0.

When I close the error message with the ok button and click on the DVD icon again, the files on the dvd become available but VLC doesn't play the movie. When starting VCL and selecting "open disc" the movie doesn't play.
I came to the conclusion that there is something wrong with the configuration of the drives.
How can I approach this?

fstab readout:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9875abb7-de71-4446-9fe5-ad8f37085e3c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b5ba9dfb-d6f5-4dc8-ad18-42d445f352cd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

mtab readout:
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-19-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
/dev/scd0 /media/cdrom0 udf ro,nosuid,nodev,utf8,user=username 0 0

the following hardware is installed:
hdd primary master
DVD drive secondary master
CD-RW drive secondary slave


Thanks for your help.

---

### Post by overdrank on 2008-08-04
Closed duplicate thread [[COLOR="DarkRed"]Here[/COLOR]](http://ubuntuforums.org/showthread.php?t=879862)
Please do not make multiple threads on the same issue, I do know that accidents happen.
:)

---

