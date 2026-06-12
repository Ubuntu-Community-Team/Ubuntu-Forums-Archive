---
title: "no partition automount other than in &quot;places&quot;??"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by pixelstuff on 2008-06-14
hello
I just did a fresh install of Ubuntustudio and found that all my partions are invisible to programs until I click on them in the Places menu. Bad thing: I don't want to click on every partion right after restart. They are not in the fstab either. What is going on? :confused: I already copied my old "home" over the fresh "home" if this has something to do with it..

---

### Post by ukripper on 2008-06-14
> **pixelstuff said:**
> hello
I just did a fresh install of Ubuntustudio and found that all my partions are invisible to programs until I click on them in the Places menu. Bad thing: I don't want to click on every partion right after restart. They are not in the fstab either. What is going on? :confused: I already copied my old "home" over the fresh "home" if this has something to do with it..

post your fstab here

and ```
sudo mount
```
and ```
sudo fdisk -l
```

---

### Post by pixelstuff on 2008-06-14
this is mount:
```
/dev/sda8 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-18-rt/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)

```
and fdisk -l
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf33df33d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12111    97281576    7  HPFS/NTFS
/dev/sda2           12112       30400   146906392+   f  W95 Ext'd (LBA)
/dev/sda5           18696       18759      514048+  82  Linux swap / Solaris
/dev/sda6           18760       19332     4602591    b  W95 FAT32
/dev/sda7           19333       30400    88903678+   7  HPFS/NTFS
/dev/sda8           12112       18695    52885917   83  Linux


```

---

### Post by rraj.be on 2008-06-14
Is the NTFS drives alone not auto mounting?

Just open

Applications-->System tools-->NTFS config tools.

Select all your NTFS drives and select mount points for them.

click apply.

check enable read write access to internal devices from pop up window.

Click apply.

From now your NTFS drives will be auto mounted.

---

### Post by pixelstuff on 2008-06-15
thanks, the ntfs are now always mounted and lines were added to the fstab.  I have a fat partion left, will find a line of code somewhere also for this one :)

---

### Post by drs305 on 2008-06-15
> **pixelstuff said:**
> thanks, the ntfs are now always mounted and lines were added to the fstab.  I have a fat partion left, will find a line of code somewhere also for this one :)

The vfat fstab entry normally looks something like this:
```
/dev/hdb1 /media/hb1 vfat auto,user,sync,exec,uid=1000,gid=1000,umask=007 0 0 
```

---

### Post by drs305 on 2008-06-15
> **pixelstuff said:**
> thanks, the ntfs are now always mounted and lines were added to the fstab.  I have a fat partion left, will find a line of code somewhere also for this one :)

vfat fstab entries typically look something like this:
```
/dev/hdb1 /media/hb1 vfat auto,user,sync,exec,uid=1000,gid=1000,umask=007 0 0 
```

---

### Post by pixelstuff on 2008-06-15
Thank you, that made it even easier!

---

