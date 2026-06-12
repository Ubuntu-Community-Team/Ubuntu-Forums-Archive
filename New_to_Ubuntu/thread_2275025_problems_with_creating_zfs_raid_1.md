---
title: "problems with creating zfs raid 1"
date: 2015-04-23
forum: New to Ubuntu
---

### Post by bundlic2 on 2015-04-23
Hi guys,     
my whs got damage, the os was old, got failures and didn't serve it's purpose any more.      
Because of that incident, I decided to install ubuntu server 14.04 Lts and use it as a samba file server.        
 
 ** First the hardware-config: **     
*server: *acer aspire h341     
*CPU: *Intel Atom D410     
*Chipset: *Intel 82801IR I/O Controller Hub (ICH 9R) (Southbridge)     
*RAM: *2 GB Storage: 3x 1 TB sata disk, 1x integrated USB disk 245MB     
*LAN: *1Gb Ethernet port  
  ...         
 
**Status quo:  **    
So far so good, I was successfully installing the OS on the (ext4 formated) sda1 partition and it is running.      
I was also successfully mounting the former data partition under the OS "Windows Home Server", now  (ntfs formated) sda2 partition and can successfully access my  personal data and so far the data seems to be unharmed ( totally relieved that at least the data is OK).      
Next to that I configured in the BIOS to create a RAID 1 with the two remaining 1TB disks. Also I was successfully creating a fakeRAID with the mirror mode (RAID1) and formated it with ext4. After that I copied the data from sda2 into the RAID1, but the do not fit in all.     
On the ntfs formated sda2, there is still 20GB left and on the RAID1 it is too few. It seems that ext4 had required 70GB space just for managing saving data.     
So I decided to try ZFS and so the problems are comming         
 
**Problem:  **   
Now I am stucking at creating a zfs RAID1.  I was following the HowTo of this website [http://serverascode.com/2014/07/01/zfs-ubuntu-trusty.html](http://serverascode.com/2014/07/01/zfs-ubuntu-trusty.html) and I am stucking at the step *"Configure zpool"*.    
 The error message is:     
 ...# zpool create -f data sdb sdd   
 [I]cannot open '/dev/sdb1': Device or resource busy     
cannot open '/dev/sdd1': Device or resource busy     
cannot create 'data': one or more vdevs refer to the same device, or one of the devices is part of an active md or lvm device   [/I]   
...    
Additionally to that I also read the post [https://ubuntuforums.org/showthread.php?t=2274803](https://ubuntuforums.org/showthread.php?t=2274803) and the links within.      
I am relatively new to linux and do not have much experience yet. Googling the issue hasn't found the right solution to that. Already spended about 4 hours on that issue.      
Now I am just totally confuse, and feeling like my mind is roller coasted and dizzy.     
Could you please show me a way out of this mess? What do I need to know to solve that problem?    
Thank you guys a lot in advance.          
 
Best Wishes,         
bundlic

---

### Post by TheFu on 2015-04-23
FakeRAID?  Ouch. I'm sure there are reasons to use it, but I cannot think of any. Use Linux SW RAID or buy a $360 HW-RAID card that is well supported in the kernel - something from LSI, perhaps?

ZFS on 2G of RAM and an Atom?  I wouldn't try it.  ZFS likes RAM.

Probably best if you run **sudo fdisk -l** and** mount** then post the output here to get help. Please, please, please, use *code tags* so things line up.

At this stage of your learning, google is NOT your friend.  How-tos will have commands that don't apply or have changed. You need stronger Linux-fu.

---

### Post by bundlic2 on 2015-04-24
Hi TheFu, 

thanks for you fast reply. You have asked about the outpout of **sudo fdisk -l ** and ** mount**. 

Here the output of ```
sudo fdisk -l : 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xeefc70ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *     7852032    41945087    17046528   83  Linux
/dev/sda2        41945715  1953503999   955779142+   7  HPFS/NTFS/exFAT
/dev/sda3           40958     7852031     3905537    5  Extended
/dev/sda5           40960     7852031     3905536   82  Linux swap / Solaris

Partition table entries are not in disk order

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  1953525167   976762583+  ee  GPT

Disk /dev/sdc: 256 MB, 256901120 bytes
32 heads, 63 sectors/track, 248 cylinders, total 501760 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2bd2c32a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63      497951      248944+   7  HPFS/NTFS/exFAT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1  1953525167   976762583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/mapper/isw_ebciefaeid_DataVolume'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/mapper/isw_ebciefaeid_DataVolume: 1000.2 GB, 1000202178560 bytes
256 heads, 63 sectors/track, 121125 cylinders, total 1953519880 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

                                Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_ebciefaeid_DataVolume1               1  1953525167   976762583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/mapper/35000cca373dd8cb6'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/mapper/35000cca373dd8cb6: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

                         Device Boot      Start         End      Blocks   Id  System
/dev/mapper/35000cca373dd8cb6p1               1  1953525167   976762583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/mapper/350014ee2acbc456b'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/mapper/350014ee2acbc456b: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

                        Device Boot      Start         End      Blocks   Id  System
/dev/mapper/350014ee2acbc456b1               1  1953525167   976762583+  ee  GPT

Disk /dev/mapper/35000cca373dd8cb6-part1: 1000.2 GB, 1000194703360 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953505280 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/35000cca373dd8cb6-part1 doesn't contain a valid partition table

Disk /dev/mapper/35000cca373dd8cb6-part9: 8 MB, 8388608 bytes
255 heads, 63 sectors/track, 1 cylinders, total 16384 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x955ed8d9

Disk /dev/mapper/35000cca373dd8cb6-part9 doesn't contain a valid partition table

Disk /dev/mapper/350014ee2acbc456b-part1: 1000.2 GB, 1000194703360 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953505280 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/350014ee2acbc456b-part1 doesn't contain a valid partition table

Disk /dev/mapper/350014ee2acbc456b-part9: 8 MB, 8388608 bytes
255 heads, 63 sectors/track, 1 cylinders, total 16384 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x955ed8d9

Disk /dev/mapper/350014ee2acbc456b-part9 doesn't contain a valid partition table [/I]

**And here the output of *mount*: ** 
[I]/dev/sda1 on / type ext4 (rw,errors=remount-ro) 
proc on /proc type proc (rw,noexec,nosuid,nodev) 
sysfs on /sys type sysfs (rw,noexec,nosuid,no dev) 
none on /sys/fs/cgroup type tmpfs (rw) 
none on /sys/fs/fuse/connections type fusectl (rw) 
none on /sys/kernel/debug type debugfs (rw) 
none on /sys/kernel/security type securityfs (rw) 
udev on /dev type devtmpfs (rw,mode=0755) 
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620) 
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755) 
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880) 
none on /run/shm type tmpfs (rw,nosuid,nodev) 
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755) 
none on /sys/fs/pstore type pstore (rw) 
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd) 
/dev/sda2 on /home/tql/data-ntfs type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096) 
 
``` 
What did do wrongly? 

Thanks in advance. 

bundlic

What do you mean with linux-fu? what's that?

---

### Post by bundlic2 on 2015-05-02
no help, great ....

---

