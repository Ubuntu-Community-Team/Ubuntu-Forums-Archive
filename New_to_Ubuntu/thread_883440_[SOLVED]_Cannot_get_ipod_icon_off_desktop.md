---
title: "[SOLVED] Cannot get ipod icon off desktop"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by richie42 on 2008-08-07
Hi, I connected my iPod, and i disconnected it, by pulling out the cable, and now there is this iPod icon that i cannot get rid of. I like my desktop nice and clean. Help!

---

### Post by hitlist diary on 2008-08-08
> **richie42 said:**
> Hi, I connected my iPod, and i disconnected it, by pulling out the cable, and now there is this iPod icon that i cannot get rid of. I like my desktop nice and clean. Help!

did you try right clicking the icon and ejcting the ipod?

---

### Post by richie42 on 2008-08-08
> **hitlist diary said:**
> did you try right clicking the icon and ejcting the ipod?

I pulled the iPod out of the usb port manually. I didn't eject it with the computer.

---

### Post by OutOfReach on 2008-08-08
The safest way to remove an iPod is to eject it from the desktop, pulling the cord can cause damage to the files or even file loss.

---

### Post by richie42 on 2008-08-08
> **OutOfReach said:**
> The safest way to remove an iPod is to eject it from the desktop, pulling the cord can cause damage to the files or even file loss.

That doesn't help with getting this icon off though...

---

### Post by richie42 on 2008-08-08
When I tried moving it into the trash can, it said :Error while deleating and his:

The specified location is not supported

---

### Post by eightmillion on 2008-08-08
It's probably still mounted. Start up a terminal and run the command **mount** and post the output here please.

---

### Post by richie42 on 2008-08-08
> **eightmillion said:**
> It's probably still mounted. Start up a terminal and run the command **mount** and post the output here please.

It is still there.

```
richard@theSelbys:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/richard/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=richard)
/dev/sdb1 on /media/RICHARD SEL type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
richard@theSelbys:~$ 

```

---

### Post by eightmillion on 2008-08-08
Try **sudo umount /dev/sdb1** and see if it goes away.

---

### Post by richie42 on 2008-08-08
> **eightmillion said:**
> Try **sudo umount /dev/sdb1** and see if it goes away.

Thank you soooo much.


How do I mark this thread as solved. You deserve thanks, man.

---

### Post by eightmillion on 2008-08-08
No problem. :)

> How do I mark this thread as solved. 

It's under thread tools at the top right.

---

