---
title: "[SOLVED] Installed Hardy over Feisty, do I have a home?"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by Udibuntu on 2008-10-21
Hi,

Just finished installing Hardy on my laptop (clean install overwriting Feisty).

I wanted to create a home partition (didn't on Feisty). Is this a home partition?:

> udi@udi-laptop:~$ mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-21-generic/volatile type tmpfs (rw)
/dev/sda4 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/udi/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=udi)
/dev/sda7 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
udi@udi-laptop:~$ 


More issues will surely follow (flash grey boxes etc.)

Thanks,

Udi

---

### Post by wolfen69 on 2008-10-21
it would appear /dev/sda4 is your home partition. so the answer would be yes.

---

### Post by philinux on 2008-10-21
/dev/sda4 on /home type ext3 (rw,relatime)

Yes.

---

