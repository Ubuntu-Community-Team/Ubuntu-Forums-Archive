---
title: "Umount"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by Jensss on 2008-06-16
I want to Umount my HP Webcam, so I can mount him in VirtualBox under XP in MSN.

But what do I have to type behind 'umount'?

Thanks!

---

### Post by wolfen69 on 2008-06-16
which version of virtualbox are you running? the ose or puel? there should be no need to unmount it for it to work in xp.

---

### Post by Keith Hedger on 2008-06-16
```
man umount
```
but basically the command is ```
umount /dev/DEVICE
or
umount /THE/MOUTNT/POINT
```

the DEVICE and /THE/MOUNT/POINT can be found from the output of mount, u may need to use sudo umount

---

### Post by Joeb454 on 2008-06-16
True - I can't see any reason why it would need "umount-ing"

You may find it easier to get USB devices to work in the VM if you're running the Non-OSE edition :)

---

### Post by Jensss on 2008-06-16
I'm running the PUEL version and I can only mount my webcam in VB if he is umounted in Ubuntu.
I don't know what my webcam is in te following list.

```
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-18-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jens/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jens)
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

```

---

### Post by Jensss on 2008-06-16
Does someone know which device it is?

---

