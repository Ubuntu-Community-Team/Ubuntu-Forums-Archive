---
title: "[SOLVED] Automount ext3 partition"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by byroncheng on 2008-07-27
I currently have my hard drive split into three partitions:
10 gb ubuntu
10 gb vista (to be installed)
80 gb ext3 storage

I see lots of guides on here how to automount an ntfs partition but they all use a program, and therefore aren't really analogous.

sudo mount:
```
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/byron/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=byron)
/dev/sda4 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)

```

sudo fdisk -l:
```
Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         973     7815591   83  Linux
/dev/sda2             974        1216     1951897+  82  Linux swap / Solaris
/dev/sda3            1217        2432     9767520   83  Linux
/dev/sda4            2433       11978    76678245   83  Linux

```

Hopefullly someone can give me some suggestions as to how to do it?  It's quite annoying when i open rhythmbox and i just see my music library shrink because it can't find files.

---

### Post by bjschuma on 2008-07-27
To do this you have to edit your /etc/fstab file.  Add the line "/dev/sda4    [put the location that you want it mounted here]    ext3    defaults,auto    0    0"

The "auto" option tells your computer to mount the partition on startup.  For more information on how fstab works, see this page:  [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by drs305 on 2008-07-27
I just wrote a tutorial today about using a gui fstab editor. You can be my first test case if you want to give it a try... (I know what you're thinking - oh yeah, I'll jump on THAT ;-))

[Storage Device Manager - A GUI Way to Manage Fstab and Other Mounting Options]("http://ubuntuforums.org/showthread.php?t=872197")

If you are familiar with what StartUp-Manager does for grub menu.lst, this is an fstab equivalent.

---

### Post by meka4996 on 2009-10-25
Try this
[http://ubuntuforums.org/showthread.php?p=8165772](http://ubuntuforums.org/showthread.php?p=8165772)

---

