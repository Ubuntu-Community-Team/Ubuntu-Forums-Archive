---
title: "sda3 swap partition shows up as external drive in /var/media/external"
date: 2016-10-11
forum: New to Ubuntu
---

### Post by laoche on 2016-10-11
my sda3 swap partition is showing up as an external drive in /var/media/external and I am not sure how to get rid of it.  It wouldn't be a big deal but I have a program running that looks in var/media/external for free storage space.  How can I get rid of it?

Thank you!

---

### Post by papibe on 2016-10-11
Hi laoche. Welcome to the forum ):P

Could you open a terminal run these commands, and post back the results (you can copy/paste the text of the terminal using the mouse)?
```
cat /etc/fstab

cat /proc/swaps

swapon -s

sudo fdisk -l

lsblk 

df -h

mount -l
```
Please use CODE tags to wrap the output text.

Regards.

---

### Post by laoche on 2016-10-11
Thanks for the quick reply.  results are below.

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=1b915db3-07ee-4626-a8a3-0d8a57e7a38e /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=BC6E-3187  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda3 during installation
UUID=d2a36309-1b0b-4d0c-a5ae-9dd272115f03 none            swap    sw              0       0

```

```
s@Server55:/var/media/external$ cat /proc/swaps
Filename                                Type            Size    Used    Priority
/dev/sda3                               partition       16722940        0       -1
```

```
s@Server55:/var/media/external$ swapon -s
Filename                                Type            Size    Used    Priority
/dev/sda3                               partition       16722940        0       -1
```

```
s@Server55:/var/media/external$ sudo fdisk -l
[sudo] password for s:
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/sda: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 6EBB74F7-885F-465D-9149-FF8EA951C0D8

Device         Start       End   Sectors  Size Type
/dev/sda1       2048   1050623   1048576  512M EFI System
/dev/sda2    1050624 200994815 199944192 95.3G Linux filesystem
/dev/sda3  200994816 234440703  33445888   16G Linux swap

Disk /dev/sdb: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 25FA4ABF-EFE1-46C2-BB4E-E039011FD152

Device     Start     End Sectors  Size Type
/dev/sdb1   2048 5861375 5859328  2.8G Linux filesystem
```

s@Server55:/var/media/external$ lsblk
```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 111.8G  0 disk
&#9500;&#9472;sda1   8:1    0   512M  0 part /boot/efi
&#9500;&#9472;sda2   8:2    0  95.3G  0 part /
&#9492;&#9472;sda3   8:3    0    16G  0 part [SWAP]
sdb      8:16   0   2.7T  0 disk
&#9492;&#9472;sdb1   8:17   0   2.8G  0 part
sr0     11:0    1  1024M  0 rom
```

```
s@Server55:/var/media/external$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  9.8M  1.6G   1% /run
/dev/sda2        94G   12G   78G  13% /
tmpfs           7.9G  192K  7.9G   1% /dev/shm
tmpfs           5.0M  8.0K  5.0M   1% /run/lock
tmpfs           7.9G     0  7.9G   0% /sys/fs/cgroup
/dev/sda1       511M  3.6M  508M   1% /boot/efi
tmpfs           1.6G   20K  1.6G   1% /run/user/112
tmpfs           1.6G     0  1.6G   0% /run/user/1000
```

```
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=8137924k,nr_inodes=2034481,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1638008k,mode=755)
/dev/sda2 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=31,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sda1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,relatime)
lxcfs on /var/lib/lxcfs type fuse.lxcfs (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other)
tmpfs on /run/user/112 type tmpfs (rw,nosuid,nodev,relatime,size=1638008k,mode=700,uid=112,gid=121)
gvfsd-fuse on /run/user/112/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=112,group_id=121)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=1638008k,mode=700,uid=1000,gid=1000)
```

---

### Post by papibe on 2016-10-11
Thanks.

I see nothing mounted or special on /var/media/external. 

Your swap is in /dev/sda3. It is correctly being used as swap, and it doesn't seem to be mounted anywhere else.

How did you come to the conclusion that it was on /var/media/external?

Regards.

---

### Post by laoche on 2016-10-12
The application I am running (SageTV) sees it and when I execute an ls command on the directory I see it as well:

```
s@Server55:/var/media/external$ ls
sda3
```

---

### Post by oldfred on 2016-10-12
Post 
ls -l /var/media/external

Your sda3 looks more like a file or folder that just happens to use a partition name?

---

### Post by laoche on 2016-10-12
Thanks!  That was it.  I am not sure why it created that folder but I just removed it and that took care of it.  Thanks.

---

