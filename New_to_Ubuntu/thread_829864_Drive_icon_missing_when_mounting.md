---
title: "Drive icon missing when mounting"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by wariskampar on 2008-06-15
Hello, when i enter mount command in terminal, the drive icon missing and therefore unaccessible. I'm pretty sure it is connected because it is accessible in mount point and confirm with Gparted. Actually i just re-format my system due to total config mess up that newbie like me can not solve(my mistake) and i mount my boot file (Ubuntu partition) at /. Could this be the problem. Now, during start up i can not see all mounted partitions (that means icon disappear when mounted and even when I issue umount the icon still not appear). Please assist me..

---

### Post by drs305 on 2008-06-15
Just to be clear, when you run the following command do you see the drive/partition you are concerned about. It might help to post the results:
```
mount
```

If you don't see it, please post the results of:
```

cat /etc/fstab
sudo fdisk -l

```

---

### Post by wariskampar on 2008-06-15
aznan@aznan-laptop:~$ mount
/dev/sda7 on / type ext3 (rw,noatime,errors=remount-ro,data=writeback)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-18-generic/volatile type tmpfs (rw)
/dev/sda5 on /mnt/sda5 type ext3 (rw)
/dev/sda6 on /mnt/sda6 type ext3 (rw)
/dev/sda1 on /mnt/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/aznan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=aznan)

---

### Post by wariskampar on 2008-06-15
ok..solve. i change mount point to media (initially mnt). Thanks. Now! i'm going to post another problem related to XP unable to boot. Thanks

---

