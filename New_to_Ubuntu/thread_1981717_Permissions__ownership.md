---
title: "Permissions / ownership"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by Lanz78 on 2012-05-17
Hi,

First of all i am an absolute beginner to linux :)

I installed a linux server Ubuntu 11.04. With that i installed 3 disk's in total 6tb. First after some playing around i was able to format and mount the disks but sometimes after a restart they would not mount and give the error Unable to mount, not authorized. Suddenly it worked again. Now i moved the server downstairs and have a rdp connection through win7. Now i cant mount the disks again.. I've tried all tips and tricks i can find so i guess its now best to ask the people that actually know what they're doing ;)

Any help would be appreciated.

---

### Post by Lanz78 on 2012-05-17
```
Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00026a51

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63  3907024064  1953512001   83  Linux

Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e64e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048      499711      248832   83  Linux
/dev/sdc2          501758   234440703   116969473    5  Extended
/dev/sdc5          501760   234440703   116969472   8e  Linux LVM

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x196b0a1f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1           16065  1943784674   971884305    7  HPFS/NTFS/exFAT
/dev/sdd2      1943784675  1944057779      136552+  82  Linux swap / Solaris
/dev/sdd3      1944057780  1945118069      530145   83  Linux

Disk /dev/mapper/ubuntu-root: 115.5 GB, 115477577728 bytes
255 heads, 63 sectors/track, 14039 cylinders, total 225542144 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu-swap_1: 4294 MB, 4294967296 bytes
255 heads, 63 sectors/track, 522 cylinders, total 8388608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-swap_1 doesn't contain a valid partition table

```

```
/dev/sda1: LABEL="2TB" UUID="8b1e41c5-b2b1-4da9-a113-a6e10b184b65" TYPE="ext4" 
/dev/sdb: LABEL="3TB" UUID="8b36e68b-354a-4f2b-bf07-ed9e40d186ba" TYPE="ext4" 
/dev/sdc1: UUID="125c5110-bbaa-4679-9437-3fb23fcae82a" TYPE="ext2" 
/dev/sdc5: UUID="yBUrOp-YhAl-Zj1O-C3j3-OPX3-Bb6g-zpk2Of" TYPE="LVM2_member" 
/dev/sdd1: LABEL="1TB" UUID="f6d069fb-6263-4b5a-8b36-23b944641a0f" TYPE="ext4" 
/dev/sdd2: TYPE="swap" 
/dev/sdd3: UUID="236eda66-d82f-488d-9cfb-d4bb139a5505" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/ubuntu-root: UUID="4f7d1d6a-1494-44b8-bfab-003626cfc445" TYPE="ext4" 
/dev/mapper/ubuntu-swap_1: UUID="567a47b2-eae4-409c-b9a6-fba6ae9c870d" TYPE="swap" 

```

```
/dev/mapper/ubuntu-root on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdc1 on /boot type ext2 (rw)
rpc_pipefs on /run/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
gvfs-fuse-daemon on /home/sylvain/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sylvain)

```
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/ubuntu-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=125c5110-bbaa-4679-9437-3fb23fcae82a /boot           ext2    defaults        0       2
/dev/mapper/ubuntu-swap_1 none            swap    sw              0       0
/dev/sdb none            ext4    sw              0       0

```

---

### Post by choppyfireballs on 2012-05-17
Is there a reason that you are using 3 differnt disks and not using raid 0. Raid 0 might solve some of your issues and make your life a ton easier.

---

### Post by Lanz78 on 2012-05-18
They are seperate for movies, music and backup of my win pc. I dont know much about raid but if read up on it now it would mean that if one falls out all my data is gone and it would take the smallest one and multiply that by 3 so i would only have 3TB instead of 6? No, this is not gonna work. I need safe data storage, especially for my backup. It will be less frequently used then the other 2 so it will also be safer.

---

### Post by Lanz78 on 2012-05-18
Solved, i fount the correct settings for in fstab.

---

### Post by choppyfireballs on 2012-05-18
> **Lanz78 said:**
> Solved, i fount the correct settings for in fstab.

just in case anyone else has the issue you should share your solution in here

---

### Post by Morbius1 on 2012-05-18
And while you're at it you might want to explain this:
> /dev/sdb: LABEL="3TB" UUID="8b36e68b-354a-4f2b-bf07-ed9e40d186ba" TYPE="ext4" That's impossible. "sdb" would refer to an actual physical hard drive and as such would not have a UUID, label, or type. sdb1, sdb2, .. sdbx would have those things because they would be partitions on that device.

Very odd output from blkid.

---

### Post by choppyfireballs on 2012-05-18
> **Morbius1 said:**
> And while you're at it you might want to explain this:
That's impossible. "sdb" would refer to an actual physical hard drive and as such would not have a UUID, label, or type. sdb1, sdb2, .. sdbx would have those things because they would be partitions on that device.

Very odd output from blkid.

^^

---

