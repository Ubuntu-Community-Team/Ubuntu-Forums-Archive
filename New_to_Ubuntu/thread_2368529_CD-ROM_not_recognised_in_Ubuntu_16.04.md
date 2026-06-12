---
title: "CD-ROM not recognised in Ubuntu 16.04"
date: 2017-08-12
forum: New to Ubuntu
---

### Post by badhri on 2017-08-12
I have Ubuntu 16.04 installed in my laptop. But my CD ROM is not getting recognised even if i have one disk already present in that. The disk is getting read but the CD ROm icon is not getting displayed in Files to browse it. Please help.

Thanks in advance.

---

### Post by Autodave on 2017-08-12
How did you install Ubuntu: by DVD?  Are you sure that the disc drive worked before?  What happens if you boot the laptop with a disc already in the drive: does it see it then?

Is this drive a DVD or just a CD?

---

### Post by Frogs Hair on 2017-08-12
> [COLOR=#000000]The disk is getting read but the CD ROm icon is not getting displayed in Files to browse it. Please help.[/COLOR] Does it show up in the Unity launcher ?

---

### Post by badhri on 2017-08-13
I installed Ubuntu with flash drive. When i was using windows, the same DVD disk worked.Even if the disc is in the drive, icon does not show up.

---

### Post by badhri on 2017-08-13
On Examining, i found the contents of the DVD in Disks application and i am able to open the files as well. But what should i do to auto mount/ show CD-ROM icon on the launcher.

---

### Post by Andreyshel on 2017-08-14
I think that can be useful to know where dvd is mounted.
Can you show us contents of files /etc/fstab and /etc/mtab when dvd is inside?

---

### Post by badhri on 2017-08-15
Content for etc/mtab file


sysfs /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
proc /proc proc rw,nosuid,nodev,noexec,relatime 0 0
udev /dev devtmpfs rw,nosuid,relatime,size=1944732k,nr_inodes=486183,mode=755 0 0
devpts /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
tmpfs /run tmpfs rw,nosuid,noexec,relatime,size=393400k,mode=755 0 0
/dev/sda2 / ext4 rw,relatime,errors=remount-ro,data=ordered 0 0
securityfs /sys/kernel/security securityfs rw,nosuid,nodev,noexec,relatime 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
tmpfs /run/lock tmpfs rw,nosuid,nodev,noexec,relatime,size=5120k 0 0
tmpfs /sys/fs/cgroup tmpfs ro,nosuid,nodev,noexec,mode=755 0 0
cgroup /sys/fs/cgroup/systemd cgroup rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd 0 0
pstore /sys/fs/pstore pstore rw,nosuid,nodev,noexec,relatime 0 0
efivarfs /sys/firmware/efi/efivars efivarfs rw,nosuid,nodev,noexec,relatime 0 0
cgroup /sys/fs/cgroup/net_cls,net_prio cgroup rw,nosuid,nodev,noexec,relatime,net_cls,net_prio 0 0
cgroup /sys/fs/cgroup/pids cgroup rw,nosuid,nodev,noexec,relatime,pids 0 0
cgroup /sys/fs/cgroup/cpuset cgroup rw,nosuid,nodev,noexec,relatime,cpuset 0 0
cgroup /sys/fs/cgroup/perf_event cgroup rw,nosuid,nodev,noexec,relatime,perf_event 0 0
cgroup /sys/fs/cgroup/cpu,cpuacct cgroup rw,nosuid,nodev,noexec,relatime,cpu,cpuacct 0 0
cgroup /sys/fs/cgroup/hugetlb cgroup rw,nosuid,nodev,noexec,relatime,hugetlb 0 0
cgroup /sys/fs/cgroup/memory cgroup rw,nosuid,nodev,noexec,relatime,memory 0 0
cgroup /sys/fs/cgroup/devices cgroup rw,nosuid,nodev,noexec,relatime,devices 0 0
cgroup /sys/fs/cgroup/freezer cgroup rw,nosuid,nodev,noexec,relatime,freezer 0 0
cgroup /sys/fs/cgroup/blkio cgroup rw,nosuid,nodev,noexec,relatime,blkio 0 0
systemd-1 /proc/sys/fs/binfmt_misc autofs rw,relatime,fd=24,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=819 0 0
mqueue /dev/mqueue mqueue rw,relatime 0 0
debugfs /sys/kernel/debug debugfs rw,relatime 0 0
hugetlbfs /dev/hugepages hugetlbfs rw,relatime 0 0
fusectl /sys/fs/fuse/connections fusectl rw,relatime 0 0
/dev/sda1 /boot/efi vfat rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,relatime 0 0
tmpfs /run/user/1000 tmpfs rw,nosuid,nodev,relatime,size=393400k,mode=700,uid=1000,gid=1000 0 0
gvfsd-fuse /run/user/1000/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,relatime,user_id=1000,group_id=1000 0 0
/dev/sr0 /media/badhri/.NET udf ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8 0 0

---

### Post by Andreyshel on 2017-08-15
[COLOR=#000000]What happens, if you eject the cd and then remove /media/badhri/.NET directory?[/COLOR]
[COLOR=#000000]Sounds strange, but worked for me in a similar   situation[/COLOR]

---

