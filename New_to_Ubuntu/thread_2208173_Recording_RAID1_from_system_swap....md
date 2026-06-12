---
title: "Recording RAID1 from system swap...?"
date: 2014-02-26
forum: New to Ubuntu
---

### Post by joshuc on 2014-02-26
UPDATE: oops, meant to put "RECOVERING" not recording...

I moved two disks (2TB each) configured with software raid1 from one system running Debian6 to an entirely different system running Ubuntu 13.10 Server.

mdadm picked them up automatically and says they are active at /dev/md127

I can type `sudo mount /dev/md127 /media/STORAGE` and I can browse all my data so I know I'm close to recovering this...
But I can't seem to get it to recognize my change in mdadm.conf when I put the ARRAY line in there.

Here is output of the commonly requested commands:
```

$ sudo cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : active raid1 sdc[1] sdb[0]
      1953513424 blocks super 1.2 [2/2] [UU]

unused devices: <none>

```

```

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/tree--nas--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=0b41edeb-daa6-4185-9fc4-e070ed42f1ee /boot           ext2    defaults        0       2
/dev/mapper/tree--nas--vg-swap_1 none            swap    sw              0       0

```

```

$ sudo mdadm --detail --scan
ARRAY /dev/md/tree-nas2:STORE metadata=1.2 name=tree-nas2:STORE UUID=40b712ad:e014e9fb:db87b836:e4b78943

```

I've tried different lines but it won't survive the reboot...
mdadm.conf
```

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
# ARRAY /dev/md/STORE metadata=1.2 UUID=40b712ad:e014e9fb:db87b836:e4b78943 name=tree-nas2:STORE
#ARRAY /dev/md/d0 metadata=1.2 name=tree-nas2:STORE UUID=40b712ad:e014e9fb:db87b836:e4b78943
ARRAY /dev/md/tree-nas2:STORE metadata=1.2 name=tree-nas2:STORE UUID=40b712ad:e014e9fb:db87b836:e4b78943
# This file was auto-generated on Wed, 26 Feb 2014 13:02:33 -0500
# by mkconf $Id$

```

---

### Post by joshuc on 2014-02-26
Well, I think I fixed this...
I used Webmin and went to System > Disk and Network File Systems
Clicked on the /media/STORAGE mount and then clicked Save and start on boot.

This preserved it.

WOOHOO!

---

