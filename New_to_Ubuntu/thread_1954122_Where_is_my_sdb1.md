---
title: "Where is my sdb1?"
date: 2012-04-07
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-04-07
Using sudo fdisk -l  I see the other drives plus sdb1  

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    15633407     7816688    b  W95 FAT32

However using mount, it is not listed.


ubuntu@ubuntu:~$ mount
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda2 on /media/OS type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd1 on /media/STU EXT HD type fuseblk (rw,nosuid,nodev,allow_other,blksize=512,default_permissions)

I am using 11.10 running on a cd as I type.

I cannot Install onto sdb1 because it does not see a boot area.

Can someone please help me untangle this mess?

(The drive is 8 GB)

---

### Post by Mark Phelps on 2012-04-07
You can't install to a FAT32 partition.  Linux distros must install to Linux filesystems.  You will have to make some unallocated space to use.

---

### Post by Boyntonstu on 2012-04-07
> **Mark Phelps said:**
> You can't install to a FAT32 partition.  Linux distros must install to Linux filesystems.  You will have to make some unallocated space to use.

Why didn't 'mount' see the FAT32?  It saw NTFS.

What Linux file system should I use?


(I understand that the root partition should be 750 MB.)

---

### Post by Cheesemill on 2012-04-07
> **Boyntonstu said:**
> Why didn't 'mount' see the FAT32?  It saw NTFS.

Because it wasn't mounted :)

---

### Post by Boyntonstu on 2012-04-07
> **Cheesemill said:**
> Because it wasn't mounted :)

I checked automatic mount.???

---

### Post by Cheesemill on 2012-04-07
Instead of using the mount command, what is the result of:
```
df -
```h

If it's being automounted then it will be taken care of by fuse which may not show up properly with the mount command.

---

