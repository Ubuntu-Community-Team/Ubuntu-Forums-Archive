---
title: "Transfer disks from NAS to Ubuntu Server"
date: 2021-06-28
forum: New to Ubuntu
---

### Post by sed_faster on 2021-06-28
The output of the command "sudo fdisk -l" it is:

```

$ sudo fdisk -l
Disk /dev/sda: 5.5 TiB, 6001175126016 bytes, 11721045168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 

Device           Start         End     Sectors   Size Type
/dev/sda1           40     1060289     1060250 517.7M Microsoft basic data
/dev/sda2      1060296     2120579     1060284 517.7M Microsoft basic data
/dev/sda3      2120584 11703256109 11701135526   5.5T Microsoft basic data
/dev/sda4  11703256112 11704316399     1060288 517.7M Microsoft basic data
/dev/sda5  11704316408 11721023999    16707592     8G Microsoft basic data


Disk /dev/sdb: 5.5 TiB, 6001175126016 bytes, 11721045168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 

Device           Start         End     Sectors   Size Type
/dev/sdb1           40     1060289     1060250 517.7M Microsoft basic data
/dev/sdb2      1060296     2120579     1060284 517.7M Microsoft basic data
/dev/sdb3      2120584 11703256109 11701135526   5.5T Microsoft basic data
/dev/sdb4  11703256112 11704316399     1060288 517.7M Microsoft basic data
/dev/sdb5  11704316408 11721023999    16707592     8G Microsoft basic data


Disk /dev/sdc: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdc1  *         2048 232441855 232439808 110.9G 83 Linux
/dev/sdc2       232443902 234440703   1996802   975M  5 Extended
/dev/sdc5       232443904 234440703   1996800   975M 82 Linux swap / Solaris


Disk /dev/md127: 5.5 TiB, 5990981238784 bytes, 11701135232 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/md126: 448.1 MiB, 469893120 bytes, 917760 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/md125: 517.7 MiB, 542834688 bytes, 1060224 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/md124: 517.6 MiB, 542769152 bytes, 1060096 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/md123: 6.9 GiB, 7408779264 bytes, 14470272 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/mapper/vg288-lv544: 55.9 GiB, 60028878848 bytes, 117243904 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/mapper/vg288-lv1: 5.4 TiB, 5930947182592 bytes, 11583881216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

```

If I try mount any of the drives I can't, the result it is this:

```

$ sudo mount -av /dev/sda (press tab tab...)
sda   sda1  sda2  sda3  sda4  sda5

$ sudo mount -av /dev/sda1 /home/user/teste/
/                        : ignored
none                     : ignored

The same result unti /dev/sda5.

```

It is possible mount this disk on my Ubuntu Server?

---

### Post by TheFu on 2021-06-28
Maybe. Probably. The model of NAS would be the most helpful, assuming the NAS formats the drives.
I don't know what "Microsoft basic data" means.  Sometimes it is just NTFS, but other times it is a way to have a volume manager created by Microsoft that merges storage from different partitions. Those are harder to deal with.
[https://askubuntu.com/questions/996683/how-to-mount-a-microsoft-basic-data-partition](https://askubuntu.com/questions/996683/how-to-mount-a-microsoft-basic-data-partition)  Did you try mounting it?

The mount command needs to 
a) have an empty directory
b1) sudo mount UUID=.....   /path/to_target_directory   # which I cannot see while typing this now.
or
b2)  sudo mount LABEL=.....   /path/to_target_directory
To see the UUID and LABEL, use **lsblk -e 7 -o name,size,type,fstype,mountpoint,uuid,label**

---

### Post by sed_faster on 2021-06-28
Sorry, my fault, because I should share model and more information about device. The NAS it is: [https://www.qnap.com/en/product/ts-231p](https://www.qnap.com/en/product/ts-231p)
On this device I had two hard drives, each with 6TB (WD) on in mirror (Raid 0, I think).

I try your suggest and the result it was:

```

$ sudo mount LABEL=9 /home/usernas/teste/
mount: unknown filesystem type 'linux_raid_member'

$ sudo mount UUID=5455234234-5124-874271-df8b-cbsdfsfsdf7634f /home/usernas/teste/
mount: unknown filesystem type 'linux_raid_member'

```

I saw the link which you shared but I didn't run this command because I have fear to do something wrong
```

sudo nfts-3g -o force,rw /dev/sdax /path/to/folder

or 

mount -t vfat /dev/sdax /path/to/folder

```

Thanks for all advice's and helps do you shared until now.

---

### Post by TheFu on 2021-06-28
Well, I'm betting that the drives are NOT ntfs or any MS-format.  Qnap has used a funky setup previously - a mix of LVM and btrfs, if my memory is right.  You'll find more help than I can give on the QNAP forums. Sorry.  I suspect the best hope would be to leave the storage connected, get all the data off, then pull the HDDs and completely wipe them for use by normal, standard, Linux techniques.

Here's part of the reason why I think they do some funky things: [https://forum.qnap.com/viewtopic.php?f=25&t=159692](https://forum.qnap.com/viewtopic.php?f=25&t=159692)
That is a different model than yours and RAID5 requires at least 3, preferably 5 HDDs to work, so the setup is probably different - definitely a different RAID level.

[https://www.qnap.com/en-us/product/ts-231p](https://www.qnap.com/en-us/product/ts-231p) says it uses encryption, so it could be that there won't be any method to access the data without the hardware.  Or they may be using normal Linux encryption tools and all will work.  IDK.

---

### Post by scorp123 on 2021-06-29
> **TheFu said:**
>  Qnap has used a funky setup previously - a mix of LVM and btrfs 

Qnap uses Ext3 / Ext4 and "mdraid", unless there's a hardware RAID controller inside (e.g. on some high-end models) or it's one of the new fancy expensive "Pro" models that use ZFS. Transferring disks from a Qnap NAS to a normal Linux system should be straightforward, provided you use **"mdadm"** and re-create the RAID setup that the disks were configured with.

Output from my own Qnap TS-453B (same generation as OP's, except it has 4 x bays) :

```

[~] # uname -r
4.14.24-qnap

[~] # mount | grep ext

/dev/mmcblk1p5 on /mnt/boot_config type ext2 (rw)
/dev/md9 on /mnt/HDA_ROOT type ext3 (rw,data=ordered)
/dev/mapper/cachedev1 on /share/CACHEDEV1_DATA type ext4 (rw,usrjquota=aquota.user,jqfmt=vfsv0,user_xattr,data=ordered,data_err=abort,delalloc,nopriv,nodiscard,noacl)
/dev/mapper/cachedev2 on /share/CACHEDEV2_DATA type ext4 (rw,usrjquota=aquota.user,jqfmt=vfsv0,user_xattr,data=ordered,data_err=abort,delalloc,nopriv,nodiscard,noacl)
/dev/sdg1 on /share/external/DEV3302_1 type ext4 (rw,usrjquota=aquota.user,jqfmt=vfsv0,user_xattr,data=ordered,data_err=abort,delalloc,nopriv,nodiscard,noacl)
/dev/sdf1 on /share/external/DEV3304_1 type ext4 (rw,usrjquota=aquota.user,jqfmt=vfsv0,user_xattr,data=ordered,data_err=abort,delalloc,nopriv,nodiscard,noacl)
/dev/md13 on /mnt/ext type ext4 (rw,data=ordered,barrier=1,nodelalloc)
tmpfs on /share/external/.cm type tmpfs (rw,size=1m)
tmpfs on /mnt/ext/opt/samba/private/msg.sock type tmpfs (rw,size=16M)
tmpfs on /share/external/.nd type tmpfs (rw,size=1m)

[~] # mdadm --examine --brief --scan --config=partitions
ARRAY /dev/md/9  metadata=1.0 UUID=0435645a:03409b6b:5cabe7ac:ea4b5498 name=9
ARRAY /dev/md/256  metadata=1.0 UUID=3526d19a:8afc7ad9:2cbb0f5d:21eb955a name=256
   spares=2
ARRAY /dev/md/1  metadata=1.0 UUID=a8ac6ca6:b139cbee:44563f2f:9ecc0c50 name=1
ARRAY /dev/md/13  metadata=1.0 UUID=df7dce35:88bcd0f7:1d3e6d28:495232a7 name=13
ARRAY /dev/md/322  metadata=1.0 UUID=530c3afe:cdb181d2:ad33803e:3f209d92 name=322
   spares=2
ARRAY /dev/md/2  metadata=1.0 UUID=5dd420ac:c914d50f:58723839:3e8609d1 name=2

```

---

### Post by sed_faster on 2021-07-11
Hy,

I followed this topic: [https://forum.qnap.com/viewtopic.php?f=25&t=159692](https://forum.qnap.com/viewtopic.php?f=25&t=159692) and I achieved only mount one disk (only disk). On down I attach my output:

```

[B]$ sudo cat /proc/mdstat  
[/B]Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md123 : active (auto-read-only) raid1 sdb2[1] sda2[0]
      530112 blocks super 1.0 [2/2] [UU]
      bitmap: 0/1 pages [0KB], 65536KB chunk

md124 : active (auto-read-only) raid1 sdb4[1] sda4[0]
      458880 blocks super 1.0 [32/2] [UU    ]
      bitmap: 1/1 pages [4KB], 65536KB chunk

md125 : active (auto-read-only) raid1 sdb5[1] sda5[0]
      7235136 blocks super 1.0 [2/2] [UU]
      bitmap: 0/1 pages [0KB], 65536KB chunk

md126 : active (auto-read-only) raid1 sdb1[1] sda1[0]
      530048 blocks super 1.0 [32/2] [UU      ]
      bitmap: 1/1 pages [4KB], 65536KB chunk

md127 : active (auto-read-only) raid1 sdb3[1] sda3[0]
      5850567616 blocks super 1.0 [2/2] [UU]
      
unused devices: <none>

**$ sudo fdisk -l /dev/md127**
**Disk /dev/md127: 5.5 TiB, 5990981238784 bytes, 11701135232 sectors**
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

**$ sudo mount /dev/md127 /home/usernas/teste/**
mount: unknown filesystem type 'LVM2_member'

**$ sudo vgscan**
  Reading all physical volumes.  This may take a while...
  Found volume group "vg288" using metadata type lvm2

**$ sudo lvscan**
  ACTIVE            '/dev/vg288/lv544' [55.91 GiB] inherit
  ACTIVE            '/dev/vg288/lv1' [5.39 TiB] inherit

**$ sudo mount /dev/vg288/lv1 /home/usernas/teste/**

**$ sudo fdisk -l**
**Disk /dev/sda: 5.5 TiB, 6001175126016 bytes, 11721045168 sectors**
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 

**Device**     **      Start** **        End** **    Sectors** **  Size** **Type**
/dev/sda1           40     1060289     1060250 517.7M Microsoft basic data
/dev/sda2      1060296     2120579     1060284 517.7M Microsoft basic data
/dev/sda3      2120584 11703256109 11701135526   5.5T Microsoft basic data
/dev/sda4  11703256112 11704316399     1060288 517.7M Microsoft basic data
/dev/sda5  11704316408 11721023999    16707592     8G Microsoft basic data


**Disk /dev/sdb: 5.5 TiB, 6001175126016 bytes, 11721045168 sectors**
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 

**Device**     **      Start** **        End** **    Sectors** **  Size** **Type**
/dev/sdb1           40     1060289     1060250 517.7M Microsoft basic data
/dev/sdb2      1060296     2120579     1060284 517.7M Microsoft basic data
/dev/sdb3      2120584 11703256109 11701135526   5.5T Microsoft basic data
/dev/sdb4  11703256112 11704316399     1060288 517.7M Microsoft basic data
/dev/sdb5  11704316408 11721023999    16707592     8G Microsoft basic data


**Disk /dev/sdc: 111.8 GiB, 120034123776 bytes, 234441648 sectors**
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 

**Device**     **Boot** **    Start** **      End** **  Sectors** **  Size** **Id** **Type**
/dev/sdc1  *         2048 232441855 232439808 110.9G 83 Linux
/dev/sdc2       232443902 234440703   1996802   975M  5 Extended
/dev/sdc5       232443904 234440703   1996800   975M 82 Linux swap / Solaris


**Disk /dev/md127: 5.5 TiB, 5990981238784 bytes, 11701135232 sectors**
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


**Disk /dev/md126: 517.6 MiB, 542769152 bytes, 1060096 sectors**
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


**Disk /dev/md125: 6.9 GiB, 7408779264 bytes, 14470272 sectors**
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


**Disk /dev/md124: 448.1 MiB, 469893120 bytes, 917760 sectors**
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


**Disk /dev/md123: 517.7 MiB, 542834688 bytes, 1060224 sectors**
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


**Disk /dev/mapper/vg288-lv544: 55.9 GiB, 60028878848 bytes, 117243904 sectors**
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


**Disk /dev/mapper/vg288-lv1: 5.4 TiB, 5930947182592 bytes, 11583881216 sectors**
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


```

Some links to learn more about this commands (including me :)

/proc/mdstat = [https://raid.wiki.kernel.org/index.php/Mdstat;](https://raid.wiki.kernel.org/index.php/Mdstat;)
vgscan = [https://linux.die.net/man/8/vgscan;](https://linux.die.net/man/8/vgscan;)
lvscan = [https://linux.die.net/man/8/lvscan;](https://linux.die.net/man/8/lvscan;)

I can't understand why I can't mount the two disks. I have two disks on this ubuntu server, from Qnap. But if I only have one disk (for example, one of them had burned) the result would it be the same?

Meanwhile I need copy all this data to another disk on other computer. 
I was think (keeping this in mind: [https://ubuntuforums.org/showthread.php?t=2464280&page=1](https://ubuntuforums.org/showthread.php?t=2464280&page=1)) if I could change all my data with this permissions (rw-rw-r--)? Because I have problems to copy data between disks (some on the same system, because of the permissions and user (sudo or not sudo ou different users between systems/computers).
I have three computers (two servers and a work computer) on the same network. I need transfer (copy/backup) data between them but I have problems with some files because permissions or owner files (the servers I access them through ssh or file manager, on my case it is nautilus - I installed samba on servers to can access them through file manager Ubuntu or windows10).

**Hack on area** [IMG]https://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]
I discovery the fast way to know If the all data it was copy between disks (on same computer or between computers). Through this command I can know how many files I have on source and destiny. I compare the values (visually) and I can know if all data it was copy. Maybe this way it is the most archaic method but for now I only remeber this....I need study more about this awesome system to know new method to manage my all data :) The book "The Linux Command Line, by William E. Shotts. Jr." Is being a big help [IMG]https://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]

```

ls -1 folder/ | wc -l

```

---

### Post by TheFu on 2021-07-11
So the data above says this is a funky mix of mdadm and lvm.  I never understand why companies use mdadm when LVM supports RAID levels using the same libraries, but without having to learn 2 commands.

Anyways, these are advanced volume management tools, so you can't think of a "disk" as only having a file system.  That isn't how either mdadm or LVM work.  LVM - Logical Volume Manager.
To understand what is happening, I'd need to see the output from these commands, run on a shell on the NAS:
```
sudo pvs
sudo vgs 
sudo lvs
df -Th
```

From that, we can know what and how to get the data off.
LVM + mdadm is a logical way to mix and match different storage protection levels on HDDs.  These can be ordered in different ways, with mdadm under LVM or LVM under mdadm.   
But below each will be the HDD and partitions like you are used to.
And above whatever is the last level, will be a file system that gets formatted. 

Normally, a PV maps to a partition like we all know.
A VG is made from 1 or more PVs which can cross partitions and disk drives. There could be 1 or 10 or 100 PVs that make up a single VG.  Or any mix of PVs can be used to make up multiple VGs.  But a PV can only be part of 1 VG at a time.
Then LVs are created from a VG and can use storage from any part of the VG or can be forced to use RAID so the mirror comes from PVs that are inside the same VG, but on different physical devices.  This would be a RAID1 LV (also called a mirror).  It is possible to create a mirror after the fact or to break a mirror if we want 2 copies of the data, but not synchronized any more.

Typically, an LV is where the file system would be created and the LV is what would be mounted directly.

Clear as mud?  For people without any volume manager experience all of this can seem overly complicated, but there are many great things possible by using LVM. Most of these things allow for modification while the system keeps running.

Nothing I wrote above is specific to qnap. These are standard Linux things, but we have to understand how qnap decided to layer each part before we can move forward.  That's why I'm asking to see the specific command output above.  The already provided commands were helpful too. Without those, I wouldn't know to ask for LVM information.

I created a graphic for a trivial, encrypted, single-HDD LVM setup last week.  Here's that, but since you have multiple disk, it will be more complex. 
[ATTACH=CONFIG]288808[/ATTACH]

Hope that helps and doesn't confuse.

TLCL is a good beginner book on Linux.  There are usually 50-500 different ways to gather information. The ls -1 |wc -l is just 1 method. But it won't could only files. It will get directories too, which may or may not be what you want.
**find . -type f | wc -l** can limit the results to only files.  For only directories, use **find . -type d | wc -l**
All of these are limited by the access allowed by the current userid. Permissions are always important on Linux, a multi-user OS.

---

