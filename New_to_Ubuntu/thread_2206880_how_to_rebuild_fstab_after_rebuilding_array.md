---
title: "how to rebuild fstab after rebuilding array"
date: 2014-02-21
forum: New to Ubuntu
---

### Post by andrew-stewart on 2014-02-21
1 of 4 drives failed (ubuntu only, raid5) replacement installed and logical drive rebuilt successfully.

On boot, 1 logical drive found, but following messages appear and system halts... chroot: cannot execute /etc/apparmor/initramfs: No such file or directory run-init: /sbin/init: No such file or directory [ 20.252079] Kernel panic - not syncing: Attempted to kill init!

On booting to livecd...

- - - - -[INDENT]/target # mount
rootfs on / type rootfs (rw)
none on /proc type proc (rw,relatime)
none on /sys type sysfs (rw,relatime)
tmpfs on /dev type tmpfs (rw,relatime)
devpts on /dev/pts type devpts (rw,relatime,mode=600,ptmxmode=000)
/dev/2/root on /target type ext4 (rw,relatime,barrier=1,data=ordered)
tmpfs on /target/dev type tmpfs (rw,relatime)
none on /target/proc type proc (rw,relatime)
none on /target/sys type sysfs (rw,relatime)

/target # fdisk -l

Disk /dev/cciss/c0d0: 750.1 GB, 750077009920 bytes
255 heads, 63 sectors/track, 91191 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b8bd9

Device Boot Start End Blocks Id System 
/dev/cciss/c0d0p1 1 91161 732242668+ 8e Linux LVM
/dev/cciss/c0d0p2 91161 91191 249007+ 5 Extended
/dev/cciss/c0d0p5 91161 91191 248976 83 Linux

/target # blkid
/dev/cciss/c0d0p1: UUID="a5ik2Y-..." TYPE="LVM2_memer"
/dev/cciss/c0d0p5: UUID="6c187489-..." TYPE="ext2"
/dev/mapper/z-root: UUID="611de0fz-..." TYPE="ext4"
/dev/mapper/Z-swap_1: UUID="c87060b4-..." TYPE="swap"


/target # cat /etc/fstab
none /dev/pts devpts defaults 0 0
none /proc proc defaults 0 0
none /sys sysfs noauto 0 0
[/INDENT]
- - - - - 

[B]Questions:
[/B]How do I rebuild fstab?
Will rebuilding fstab solve the /sbin/init and /etc/apparmor/initramfs "no such file" errors?

All help to get this webserver back up and running very much appreciated!

---

