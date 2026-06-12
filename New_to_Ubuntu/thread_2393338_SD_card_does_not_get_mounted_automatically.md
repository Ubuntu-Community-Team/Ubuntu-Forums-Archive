---
title: "SD card does not get mounted automatically"
date: 2018-06-02
forum: New to Ubuntu
---

### Post by wrongusername2 on 2018-06-02
I am using 16.04. Many times SD card does not automatically get mounted. In such cases I mount it manually, but OS won't let me delete the files. In that case only solution is rebooting machine. Please let me know if there is a better solution to come out of such stale situation? I have tried removing the SD card, that does not help.  

```
sudo mount -rw /dev/mmcblk0p1 /media/afterwindows/junk1
```

Thanks

---

### Post by sudodus on 2018-06-02
I think you can write and delete files via sudo (with root privileges). If you want your regular user ID to write and delete files, you can add some mount options. Maybe the following link can help,

[Mount NTFS partition in a USB drive with custom permissions and owner](https://askubuntu.com/questions/11840/how-do-i-use-chmod-on-an-ntfs-or-fat32-partition/956072#956072)

[hr][/hr]
I guess that there is a Microsoft file system in the card, FAT32 or NTFS. Depending of your version of Ubuntu, you may need to install extra packages for exFAT.

If you have a linux file system (for example ext4), things are more flexible.

---

### Post by wrongusername2 on 2018-06-05
Thanks for responding.

I am having slightly different issue in 18.04. Please follow these steps.

1) When I insert the MP3 recorder, partition gets mounted as read-only.

2) LSBLK shows the device & mount point

```
root@afterwindowsP50:/media/afterwindows# lsblk
    sdd      8:48   1   7.8G  0 disk 
    &#9492;&#9472;sdd1   8:49   1   7.8G  0 part /mnt/K-183 
```

3) I unmount so I can remount with RW permission

    ```
 
            root@afterwindowsP50:/media/afterwindows# umount /mnt/K-183 
     
```

4) Now LSBLK shows device but not mount point. That is expected.  

```
root@afterwindowsP50:/media/afterwindows# lsblk    
sdd      8:48   1   7.8G  0 disk 
&#9492;&#9472;sdd1   8:49   1   7.8G  0 part

```

5) Now mount command fails saying device is missing.

```
root@afterwindowsP50:/media/afterwindows# mount -rw /sdd/sdd1 junk1
mount: /media/afterwindows/junk1: special device /sdd/sdd1 does not exist.

```

```
root@afterwindowsP50:/media/afterwindows# mount -rw /sdd/K-183 junk1
mount: /media/afterwindows/junk1: special device /sdd/K-183 does not exist.

```


This method of unmount & mount used to work in 16.04 but not in 18.04 anymore. 

Please  help me. I do not mind remounting just to delete a file but that is also not working any more.  This method used to work on  16.04.

---

### Post by sudodus on 2018-06-06
You should specify the device, that is pointing to the partition, that you want to mount, **/dev/...**

This mount command line might work better, (assuming that junk1 is a directory made to be a mountpoint).

```

sudo mount -rw /dev/sdd1 /media/afterwindows/junk1

```

---

### Post by wrongusername2 on 2018-06-06
Hi,
 
              Thank you. Mount command worked, but filesystem still stays READONLY and does not let me delete the file

```
afterwindows@afterwindowsP50:/media/afterwindows$ sudo mount -rw /dev/sdc1 junk1
```

When I try to delete the file, I get following error.
```

REC087.WAV: Error removing file /media/afterwindows/junk1/RECORD/REC087.WAV: Read-only file system
```


MP3 player has two partitions (K1 & K1-183). By default K1 gets mounted under /media but K1-183 gets mounted under /mnt. Second difference is K1-183 stays read only where K1 is RW.


Here is the outputs of lsblk, blkid, lshw. May be this will help diagnose this issue.

**sudo lsblk**
```

loop26   7:26   0   3.3M  1 loop /snap/gnome-system-monitor/36
loop27   7:27   0  74.8M  1 loop /snap/sqlitebrowser-casept/2
loop28   7:28   0 199.5M  1 loop /snap/gimp/40
sda      8:0    0 903.6G  0 disk 
&#9492;&#9472;sda1   8:1    0 903.6G  0 part 
sdb      8:16   0 465.8G  0 disk 
&#9500;&#9472;sdb1   8:17   0   512M  0 part /boot/efi
&#9492;&#9472;sdb2   8:18   0 465.3G  0 part /
sdc      8:32   1   7.8G  0 disk 
&#9492;&#9472;sdc1   8:33   1   7.8G  0 part /media/afterwindows/junk1
sdd      8:48   1  29.7G  0 disk 
&#9492;&#9472;sdd1   8:49   1  29.7G  0 part /media/afterwindows/K-1
```

**sudo lshw -class disk**
```

*-disk:0
       description: SCSI Disk
       product: USB DISK FOB 2.0
       vendor: ACTIONS
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdc
       version: 0
       size: 7994MiB (8382MB)
       capabilities: removable
       configuration: logicalsectorsize=1024 sectorsize=1024
     *-medium
          physical id: 0
          logical name: /dev/sdc
          size: 7994MiB (8382MB)
          capabilities: partitioned partitioned:dos
  *-disk:1
       description: SCSI Disk
       product: USB DISK FOB 2.0
       vendor: ACTIONS
       physical id: 0.0.1
       bus info: scsi@4:0.0.1
       logical name: /dev/sdd
       version: 0
       size: 29GiB (31GB)
       capabilities: removable
       configuration: logicalsectorsize=512 sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sdd
          size: 29GiB (31GB)
          capabilities: partitioned partitioned:dos
  *-disk
       description: ATA Disk
       product: ST1000LM035-1RK1
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: MBC4
       serial: WCB0ZG7B
       size: 903GiB (970GB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=25e8a1b2-0b2a-4474-93fa-35b847d97ee5 logicalsectorsize=512 sectorsize=4096
  *-disk
       description: ATA Disk
       product: ST500VT000-1DK14
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sdb
       version: MBC1
       serial: S3PG8G3J
       size: 465GiB (500GB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=442d73d9-1700-47b0-8b2f-316a163fd03a logicalsectorsize=512 sectorsize=4096
```

**sudo blkid**

```
/dev/loop7: TYPE="squashfs"
/dev/sda1: LABEL="New Volume" UUID="F61891071890C7CF" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="55c88896-4c1f-479c-985b-9290fd57a137"
/dev/sdb1: UUID="A636-16B7" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="1f1b5456-b43c-4b58-8992-e3ed597a64e8"
/dev/sdb2: UUID="4eaa65fe-baa7-45aa-a28b-9d96abf8f7fb" TYPE="ext4" PARTUUID="799be1c8-582a-4d66-9058-52d44fd550f5"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/loop14: TYPE="squashfs"
/dev/loop15: TYPE="squashfs"
/dev/loop16: TYPE="squashfs"
/dev/loop17: TYPE="squashfs"
/dev/loop18: TYPE="squashfs"
/dev/loop19: TYPE="squashfs"
/dev/loop20: TYPE="squashfs"
/dev/loop21: TYPE="squashfs"
/dev/loop22: TYPE="squashfs"
/dev/loop23: TYPE="squashfs"
/dev/loop24: TYPE="squashfs"
/dev/loop25: TYPE="squashfs"
/dev/loop26: TYPE="squashfs"
/dev/loop27: TYPE="squashfs"
/dev/loop28: TYPE="squashfs"
/dev/sdc1: LABEL="K-183" UUID="EC95-4FBB" TYPE="vfat"
/dev/sdd1: LABEL="K-1" TYPE="vfat"
```

---

### Post by wrongusername2 on 2018-06-06
I ran Fsck and that did not fix the problem'

**sudo fsck -r /dev/sdc1**
```

fsck from util-linux 2.31.1
fsck.fat 4.1 (2017-01-24)
0x41: Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.
1) Remove dirty bit
2) No action
? 1
Perform changes ? (y/n) y
/dev/sdc1: 2659 files, 823958/1022192 clusters
/dev/sdc1: status 1, rss 14636, real 15.399535, user 0.052394, sys 0.048901
```

I think I probably just use WIN10 for deleting files. This issue is taking way too much of time.


Thanks

---

### Post by sudodus on 2018-06-07
Please run the following command lines and post the results, when you have mounted the SD card with the recommended command (that I thought would mount it read-write),

```

sudo lsblk -f
sudo lsblk -m
sudo parted -ls
df -h
cat /etc/mtab

```

---

### Post by wrongusername2 on 2018-06-08
Thanks for the response. i will post the results tomorrow. I also read that kernal marks the filesystem as RD-only if it encounters any error during mounting time. They suggested to run fsck.

---

### Post by wrongusername2 on 2018-06-09
Hi,


Sorry i was late getting the response. Here is the outputs. K-183 is the problem VOLUME. Here is lay out of MP3 player


MP3 player 
              ---->SD-card              (**K1** *[COLOR=#000000][FONT=&amp]sdd1[/FONT][/COLOR]*)
              ---->Internal memory  (**K1-183** *[COLOR=#000000][FONT=&amp]sdc1[/FONT][/COLOR]*)




 
**lsblk -f**
```

NAME   FSTYPE   LABEL      UUID                                 MOUNTPOINT
loop0  squashfs                                                 /snap/core/4571
loop1  squashfs                                                 /snap/gnome-characters/96
loop2  squashfs                                                 /snap/gnome-calculator/154
loop3  squashfs                                                 /snap/gnome-logs/31
loop4  squashfs                                                 /snap/gnome-calculator/167
loop5  squashfs                                                 /snap/sqlitebrowser-casept/2
loop6  squashfs                                                 /snap/gnome-characters/69
loop7  squashfs                                                 /snap/core/4486
loop8  squashfs                                                 /snap/core/4650
loop9  squashfs                                                 /snap/gnome-3-26-1604/59
loop10 squashfs                                                 /snap/gnome-characters/86
loop11 squashfs                                                 /snap/gnome-logs/25
loop12 squashfs                                                 /snap/gnome-3-26-1604/64
loop13 squashfs                                                 /snap/gnome-calculator/170
loop14 squashfs                                                 /snap/gnome-logs/34
sda                                                             
&#9492;&#9472;sda1 ntfs     New Volume F61891071890C7CF                     
sdb                                                             
&#9500;&#9472;sdb1 vfat                A636-16B7                            /boot/efi
&#9492;&#9472;sdb2 ext4                4eaa65fe-baa7-45aa-a28b-9d96abf8f7fb /
sdc                                                             
&#9492;&#9472;sdc1 vfat     K-183      EC95-4FBB                            /mnt/K-183
sdd                                                             
&#9492;&#9472;sdd1 vfat     K-1                                             /media/afterwindows/K-1

```


**lsblk -m**
```

NAME     SIZE OWNER GROUP MODE
loop0   86.6M root  disk  brw-rw----
loop1     13M root  disk  brw-rw----
loop2    1.6M root  disk  brw-rw----
loop3   21.6M root  disk  brw-rw----
loop4    2.3M root  disk  brw-rw----
loop5   74.8M root  disk  brw-rw----
loop6   12.2M root  disk  brw-rw----
loop7   86.6M root  disk  brw-rw----
loop8   86.6M root  disk  brw-rw----
loop9    140M root  disk  brw-rw----
loop10    13M root  disk  brw-rw----
loop11    21M root  disk  brw-rw----
loop12 139.5M root  disk  brw-rw----
loop13   2.3M root  disk  brw-rw----
loop14  14.5M root  disk  brw-rw----
sda    903.6G root  disk  brw-rw----
&#9492;&#9472;sda1 903.6G root  disk  brw-rw----
sdb    465.8G root  disk  brw-rw----
&#9500;&#9472;sdb1   512M root  disk  brw-rw----
&#9492;&#9472;sdb2 465.3G root  disk  brw-rw----
sdc      7.8G root  disk  brw-rw----
&#9492;&#9472;sdc1   7.8G root  disk  brw-rw----
sdd     29.7G root  disk  brw-rw----
&#9492;&#9472;sdd1  29.7G root  disk  brw-rw----

```


**parted -ls**
```

Model: ATA ST1000LM035-1RK1 (scsi)
Disk /dev/sda: 970GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End    Size   File system  Name                  Flags
 1      1049kB  970GB  970GB  ntfs         Basic data partition  msftdata




Model: ATA ST500VT000-1DK14 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End    Size   File system  Name                  Flags
 1      1049kB  538MB  537MB  fat32        EFI System Partition  boot, esp
 2      538MB   500GB  500GB  ext4




Model: ACTIONS USB DISK FOB 2.0 (scsi)
Disk /dev/sdc: 8382MB
Sector size (logical/physical): 1024B/1024B
Partition Table: msdos
Disk Flags: 


Number  Start  End     Size    Type     File system  Flags
 1      131kB  8382MB  8382MB  primary  fat32




Model: ACTIONS USB DISK FOB 2.0 (scsi)
Disk /dev/sdd: 31.9GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type     File system  Flags
 1      4194kB  31.9GB  31.9GB  primary  fat32        boot



```


**df -h**
```

Filesystem      Size  Used Avail Use% Mounted on
udev             12G     0   12G   0% /dev
tmpfs           2.4G  1.9M  2.4G   1% /run
/dev/sdb2       457G   11G  424G   3% /
tmpfs            12G   17M   12G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs            12G     0   12G   0% /sys/fs/cgroup
/dev/loop1       13M   13M     0 100% /snap/gnome-characters/96
/dev/loop0       87M   87M     0 100% /snap/core/4571
/dev/loop2      1.7M  1.7M     0 100% /snap/gnome-calculator/154
/dev/loop3       22M   22M     0 100% /snap/gnome-logs/31
/dev/loop4      2.4M  2.4M     0 100% /snap/gnome-calculator/167
/dev/loop5       75M   75M     0 100% /snap/sqlitebrowser-casept/2
/dev/loop6       13M   13M     0 100% /snap/gnome-characters/69
/dev/loop7       87M   87M     0 100% /snap/core/4486
/dev/loop8       87M   87M     0 100% /snap/core/4650
/dev/loop9      141M  141M     0 100% /snap/gnome-3-26-1604/59
/dev/loop10      13M   13M     0 100% /snap/gnome-characters/86
/dev/loop11      21M   21M     0 100% /snap/gnome-logs/25
/dev/loop14      15M   15M     0 100% /snap/gnome-logs/34
/dev/loop12     140M  140M     0 100% /snap/gnome-3-26-1604/64
/dev/loop13     2.4M  2.4M     0 100% /snap/gnome-calculator/170
/dev/sdb1       511M  4.7M  507M   1% /boot/efi
tmpfs           2.4G   16K  2.4G   1% /run/user/120
tmpfs           2.4G   52K  2.4G   1% /run/user/1000
/dev/sdc1       7.8G  6.1G  1.8G  78% /mnt/K-183
/dev/sdd1        30G   24G  5.9G  81% /media/afterwindows/K-1

```


**cat /etc/mtab**
```

sysfs /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
proc /proc proc rw,nosuid,nodev,noexec,relatime 0 0
udev /dev devtmpfs rw,nosuid,relatime,size=12163796k,nr_inodes=3040949,mode=755 0 0
devpts /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
tmpfs /run tmpfs rw,nosuid,noexec,relatime,size=2438640k,mode=755 0 0
/dev/sdb2 / ext4 rw,relatime,errors=remount-ro,data=ordered 0 0
securityfs /sys/kernel/security securityfs rw,nosuid,nodev,noexec,relatime 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
tmpfs /run/lock tmpfs rw,nosuid,nodev,noexec,relatime,size=5120k 0 0
tmpfs /sys/fs/cgroup tmpfs ro,nosuid,nodev,noexec,mode=755 0 0
cgroup /sys/fs/cgroup/unified cgroup2 rw,nosuid,nodev,noexec,relatime,nsdelegate 0 0
cgroup /sys/fs/cgroup/systemd cgroup rw,nosuid,nodev,noexec,relatime,xattr,name=systemd 0 0
pstore /sys/fs/pstore pstore rw,nosuid,nodev,noexec,relatime 0 0
efivarfs /sys/firmware/efi/efivars efivarfs rw,nosuid,nodev,noexec,relatime 0 0
cgroup /sys/fs/cgroup/cpu,cpuacct cgroup rw,nosuid,nodev,noexec,relatime,cpu,cpuacct 0 0
cgroup /sys/fs/cgroup/devices cgroup rw,nosuid,nodev,noexec,relatime,devices 0 0
cgroup /sys/fs/cgroup/rdma cgroup rw,nosuid,nodev,noexec,relatime,rdma 0 0
cgroup /sys/fs/cgroup/pids cgroup rw,nosuid,nodev,noexec,relatime,pids 0 0
cgroup /sys/fs/cgroup/freezer cgroup rw,nosuid,nodev,noexec,relatime,freezer 0 0
cgroup /sys/fs/cgroup/memory cgroup rw,nosuid,nodev,noexec,relatime,memory 0 0
cgroup /sys/fs/cgroup/blkio cgroup rw,nosuid,nodev,noexec,relatime,blkio 0 0
cgroup /sys/fs/cgroup/cpuset cgroup rw,nosuid,nodev,noexec,relatime,cpuset 0 0
cgroup /sys/fs/cgroup/hugetlb cgroup rw,nosuid,nodev,noexec,relatime,hugetlb 0 0
cgroup /sys/fs/cgroup/net_cls,net_prio cgroup rw,nosuid,nodev,noexec,relatime,net_cls,net_prio 0 0
cgroup /sys/fs/cgroup/perf_event cgroup rw,nosuid,nodev,noexec,relatime,perf_event 0 0
systemd-1 /proc/sys/fs/binfmt_misc autofs rw,relatime,fd=25,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=19318 0 0
mqueue /dev/mqueue mqueue rw,relatime 0 0
debugfs /sys/kernel/debug debugfs rw,relatime 0 0
hugetlbfs /dev/hugepages hugetlbfs rw,relatime,pagesize=2M 0 0
configfs /sys/kernel/config configfs rw,relatime 0 0
fusectl /sys/fs/fuse/connections fusectl rw,relatime 0 0
/dev/loop1 /snap/gnome-characters/96 squashfs ro,nodev,relatime 0 0
/dev/loop0 /snap/core/4571 squashfs ro,nodev,relatime 0 0
/dev/loop2 /snap/gnome-calculator/154 squashfs ro,nodev,relatime 0 0
/dev/loop3 /snap/gnome-logs/31 squashfs ro,nodev,relatime 0 0
/dev/loop4 /snap/gnome-calculator/167 squashfs ro,nodev,relatime 0 0
/dev/loop5 /snap/sqlitebrowser-casept/2 squashfs ro,nodev,relatime 0 0
/dev/loop6 /snap/gnome-characters/69 squashfs ro,nodev,relatime 0 0
/dev/loop7 /snap/core/4486 squashfs ro,nodev,relatime 0 0
/dev/loop8 /snap/core/4650 squashfs ro,nodev,relatime 0 0
/dev/loop9 /snap/gnome-3-26-1604/59 squashfs ro,nodev,relatime 0 0
/dev/loop10 /snap/gnome-characters/86 squashfs ro,nodev,relatime 0 0
/dev/loop11 /snap/gnome-logs/25 squashfs ro,nodev,relatime 0 0
/dev/loop14 /snap/gnome-logs/34 squashfs ro,nodev,relatime 0 0
/dev/loop12 /snap/gnome-3-26-1604/64 squashfs ro,nodev,relatime 0 0
/dev/loop13 /snap/gnome-calculator/170 squashfs ro,nodev,relatime 0 0
/dev/sdb1 /boot/efi vfat rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,relatime 0 0
tmpfs /run/user/120 tmpfs rw,nosuid,nodev,relatime,size=2438636k,mode=700,uid=120,gid=125 0 0
tmpfs /run/user/1000 tmpfs rw,nosuid,nodev,relatime,size=2438636k,mode=700,uid=1000,gid=1000 0 0
gvfsd-fuse /run/user/1000/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,relatime,user_id=1000,group_id=1000 0 0
/dev/sdc1 /mnt/K-183 vfat rw,nosuid,nodev,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro 0 0
/dev/sdd1 /media/afterwindows/K-1 vfat rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro 0 0

```


Thanks

---

### Post by sudodus on 2018-06-09
Things look OK, as far as I can understand.

```
cat /etc/mtab
``` tells us

```

/dev/sdc1 /mnt/K-183 vfat rw,nosuid,nodev,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro 0 0
/dev/sdd1 /media/afterwindows/K-1 vfat rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro 0 0

```

Both of these (/dev/sdc1 and /dev/sdd1) are mounted with read and write permissions 'rw', so at least with sudo you should be able to write.

If it is still not working, there is some other problem than mounting, either that the device is failing (for example a gridlocked memory card) or that the electronic system in the mp3 player is not allowing writing or not managing to make it work. Sometimes a peripheral device (in this case the mp3 player) is not working correctly with the computer hardware or software.

---

### Post by wrongusername2 on 2018-06-09
Thanks. I will try to to delete using sudo.

---

### Post by Keith_Beef on 2018-07-28
I also get this problem, but not with all SD cards.

For example, a card used in a Canon G11 camera gets mounted automatically, but a card used in a no-name Chinese action camera does not get mounted automatically.

When I insert the action camera card, here's what I see appear from dmesg

```
$ sudo dmesg | tail
[535182.301956] mmc0: new high speed SDHC card at address b368
[535182.302850] mmcblk0: mmc0:b368       29.8 GiB 
[535182.304275]  mmcblk0: p1
```

and

```
$ sudo lsblk -f
NAME                     FSTYPE      LABEL UUID                                   MOUNTPOINT
sda                                                                               
&#9500;&#9472;sda1                   ext2              [id removed]   /boot
&#9492;&#9472;sda5                   crypto_LUKS        [id removed]   
  &#9492;&#9472;sda5_crypt           LVM2_member        [id removed] 
    &#9500;&#9472;machine--vg-root   ext4              [id removed]    /
    &#9500;&#9472;machine--vg-var    ext4              [id removed]    /var
    &#9500;&#9472;machine--vg-swap_1 swap              [id removed]    [SWAP]
    &#9500;&#9472;machine--vg-tmp    ext4              [id removed]    /tmp
    &#9492;&#9472;machine--vg-home   ext4              [id removed]    /home
mmcblk0                                                                           
&#9492;&#9472;mmcblk0p1              vfat              4CCA-862D
```



```
$ sudo lsblk -m
NAME                       SIZE OWNER GROUP MODE
sda                      232.9G root  disk  brw-rw----
&#9500;&#9472;sda1                     243M root  disk  brw-rw----
&#9492;&#9472;sda5                   232.7G root  disk  brw-rw----
  &#9492;&#9472;sda5_crypt           232.7G root  disk  brw-rw----
    &#9500;&#9472;machine--vg-root    23.3G root  disk  brw-rw----
    &#9500;&#9472;machine--vg-var      9.3G root  disk  brw-rw----
    &#9500;&#9472;machine--vg-swap_1  15.9G root  disk  brw-rw----
    &#9500;&#9472;machine--vg-tmp      1.9G root  disk  brw-rw----
    &#9492;&#9472;machine--vg-home   182.3G root  disk  brw-rw----
mmcblk0                   29.8G root  disk  brw-rw----
&#9492;&#9472;mmcblk0p1               29.8G root  disk  brw-rw----
```




I created a mount point in /mnt and tried to mount the filesystem

```
$ sudo mount /dev/mmcblk0 /mnt/sdcard/
mount: wrong fs type, bad option, bad superblock on /dev/mmcblk0,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
```



Looking with parted

```
$ sudo parted -ls
...snip...
Model: SD  (sd/mmc)
Disk /dev/mmcblk0: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      4194kB  32.0GB  32.0GB  primary  fat32        lba
```

---

### Post by Holger_Gehrke on 2018-07-28
'/dev/mmcblk0/' is the whole device, '/dev/mmcblk0p1/' is a partition on the device with a filesystem in it. Unless a device is set up as a "superfloppy" - no partitions, filesystem directly on the device - you can't mount a whole device (there might be multiple partitions on it - which one goes where ?). The partition on the other hand should be mountable. So your mount command should be```
sudo mount /dev/mmcblk0**p1** /mnt/sdcard
``` 

Holger

---

