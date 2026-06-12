---
title: "CHOWN fails to change ownership from root???"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by ijason on 2008-11-03
installing an additional drive into my computer, and running into a weird problem. 

the drive is detected right away after connecting it, and i formatted/partitioned it with Partition Editor. next i set the names i wanted with e2label, so now i get them listed as i like in the >Places >Computer window... 

problem is, when i mount them, they're owned by root.

i opened a terminal and SU'd to root and then "chown jason /dev/sdb" followed by doing the same for sdb1 and sdb2. no error messages. after un-mounting and re-mounting, the drives are STILL owned by root.

what am i missing?

---

### Post by taurus on 2008-11-03
What filesystem is that drive and where do you mount it to, mount point?

Applications -> Accessories -> Terminal
```
mount
```

---

### Post by ijason on 2008-11-03
here's the output :

```
jason@jason-desktop:/dev$ mount
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
gvfs-fuse-daemon on /home/jason/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jason)
/dev/sdc1 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdb2 on /media/everything_else type ext2 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1 on /media/media type ext2 (rw,nosuid,nodev,uhelper=hal)
jason@jason-desktop:/dev$ 
```

where /dev/sdb1 and /dev/sdb2 are the two partitions on the new drive.

thanks for your help!

---

### Post by taurus on 2008-11-03
Just change the ownership of those two mount points from root to your login name, jason, and you should be able to write to them anytime you want.

```
sudo chown -R jason:jason /media/everything_else
sudo chown -R jason:jason /media/media
ls -la /media
```

---

### Post by blackened on 2008-11-03
```
sudo chown jason:jason /media/media
sudo chown jason:jason /media/everything_else
```
It's the mountpoint that's giving you the permission problems, not the device itself.

EDIT:
Doh, day late, dollar short :)

---

### Post by ijason on 2008-11-03
ah... that worked, after un-mounting then mounting the drives they're now owned to me. 

so, i need to CHOWN the directory they're mounted *to*, instead of the actual device? interesting.

thanks again.

---

### Post by asmoore82 on 2008-11-04
> **ijason said:**
> ah... that worked, after un-mounting then mounting the drives they're now owned to me. 

so, i need to CHOWN the directory they're mounted *to*, instead of the actual device? interesting.

thanks again.

the missing link that has gone unsaid is that you should ``chown'' the mountpoint *while it is mounted*
so the ownership information will get saved back to the device that way.

changing ownership/permissions on the device itself would control who has "raw access" to the device,
such as the ability to re-partition or re-format it.

---

