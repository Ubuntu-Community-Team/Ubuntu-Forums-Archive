---
title: "Permissions problems after installation"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by pstjmack on 2008-10-29
I installed Ubuntu eee on my eee 900, but I’ve ended up with most of the machine’s memory inaccessible due to permissions problems on the partitions. I can access my /dev/sda partitions fine, but all the /dev/sdb partitions, including most of the 16GB drive, are closed off. Any ideas how I can fix this? For everyone's information, Ubuntu eee is a remix for netbooks, though it has no unique aspects regarding disk partitions, and the Asus eee 900 has two physical drives, one 4GB, one 16GB.

---

### Post by macogw on 2008-10-29
Er, are they mounted?  Type the command "mount" in a terminal and see if they're listed as being mounted anywhere.

---

### Post by pstjmack on 2008-10-29
Yes, they do mount when I type the command in the terminal. Here's the output:

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb6 on /media/disk-1 type ext2 (rw,nosuid,nodev,uhelper=hal)

/dev/sda is the accessible directory, /dev/sdb is the one I've been unable to use.

---

