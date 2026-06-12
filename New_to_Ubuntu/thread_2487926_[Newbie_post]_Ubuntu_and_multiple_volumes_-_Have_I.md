---
title: "[Newbie post] Ubuntu and multiple volumes - Have I made a horrible mistake?"
date: 2023-06-18
forum: New to Ubuntu
---

### Post by produktnz on 2023-06-18
Windows systems engineer / General IT guy for 12 years + here. Made the jump to learning Linux a while back, passively, still struggling =|
 
The mission:
 Supermicro Superserver with Ubuntu server 22 installed on an m.2 512gb. Virtualmin + WP + mariaDB (all configured waiting post hardening)
Raid5 with hotspare using 500gb SSD's (good quality Samsung 870Evo SSD's) [done]

When installing Ubuntu server, I chose a custom disk layout and made:

m.2 (512GB)[INDENT]

sdd           8:48   0 476.9G  0 disk
&#9500;&#9472;sdd1        8:49   0     1G  0 part  /boot/efi
&#9492;&#9472;sdd2        8:50   0   475G  0 part  /


[/INDENT]
r5 (ssd*4)[INDENT]-\sda,sdb,sdc [raid presented as md126][/INDENT]
[INDENT=2]-&#9500;&#9472;md126       9:126  0 884.9G  0 raid5

md126 is mounted to \home
[/INDENT]


Now's the part where I'm not sure if I've screwed this up or not.

In my mind, mounting the raid5 volume to /home effectively means it's a symlink to another device, The idea being: have a separate volume for the websites data, which can grow to around 700GB, mounted as home so that wordpress hosts on virtualmin can have a home directory of a raid5 array (with HS) but the remainder of the files on the faster m.2 ssd. 

Thoughts? or am I insane?

---

### Post by TheFu on 2023-06-18
I think your / partition is much to large.  35G should be sufficient. 

BTW, when posting, it would really help to see the exact command used, since we often like to use options.  When posting anything from a terminal, please, please, use 'code tags' so columns line up correctly. Also, we need to see the header line.  Many of the default columns shown are useless for day-to-day needs and even less so without the header.

For example, here's a storage layout for a system installed about 2 months ago:
```
$ lsblk -e 7 -o name,size,type,FSAVAIL,FSUSE%,fstype,mountpoint    # this is actually an alias, so I don't type it.
NAME                              SIZE TYPE FSAVAIL FSUSE% FSTYPE      MOUNTPOINT
nvme0n1                         931.5G disk                        
&#9500;&#9472;nvme0n1p1                         1M part                ext2    
&#9500;&#9472;nvme0n1p2                        50M part   43.9M    12% vfat    /boot/efi
&#9500;&#9472;nvme0n1p3                       700M part  342.6M    42% ext4    /boot
&#9492;&#9472;nvme0n1p4                     930.8G part                LVM2_me 
  &#9500;&#9472;vg01-swap01                   4.1G lvm                 swap    [SWAP]
  &#9500;&#9472;vg01-root01                    35G lvm      26G    19% ext4    /
  &#9500;&#9472;vg01-var01                     20G lvm    16.4G    11% ext4    /var
  &#9500;&#9472;vg01-tmp01                      4G lvm     3.7G     0% ext4    /tmp
  &#9500;&#9472;vg01-home01                    10G lvm     4.1G    53% ext4    /home
  &#9500;&#9472;vg01-libvirt--01              137G lvm     2.8G    98% ext4    /var/lib/libvirt
  &#9492;&#9472;vg01-lxd--containers--01       30G lvm

$ df -hT -x squashfs -x tmpfs -x devtmpfs        # another alias
Filesystem                        Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg01-root01           ext4   35G  6.5G   26G  20% /
/dev/nvme0n1p3                    ext4  672M  281M  343M  45% /boot
/dev/mapper/vg01-home01           ext4  9.8G  5.2G  4.1G  57% /home
/dev/nvme0n1p2                    vfat   50M  6.1M   44M  13% /boot/efi
/dev/mapper/vg01-tmp01            ext4  3.9G  864K  3.7G   1% /tmp
/dev/mapper/vg01-var01            ext4   20G  2.2G   17G  12% /var
/dev/mapper/vg01-libvirt--01      ext4  134G  131G  2.8G  98% /var/lib/libvirt
/dev/mapper/vg--hadar-lv--backups ext4  459G  1.8G  457G   1% /Backups

```

To get a feel for storage, we need those 2 outputs, shown together.  If you use a volume manager, there are probably summary commands for those as well. For LVM, they are pvs, vgs, and lvs.

There are many reasons why I use LVM and why I have separated /var, swap, /tmp, /home,  libvirt and container areas areas to be separate.  Anyway, I've posted "why" I do this a few times previously.  /tmp being separate is a security thing.  Same for /var and /home.

Much of the empty storage will be directly allocated to virtual machines as block devices. That storage will never be mounted on the host.  I try to never use more than 80% of the available storage so the lifespan of the SSD can be much longer with the extra areas used for wear leveling.  Also, with LVM, having excess storage available for snapshots is important.  When you move up to using a volume manager, you'll want to learn more about snapshots. They can be very useful.

There aren't any \ characters in Unix (except to escape) ... and the / character can be used on Unix, Linux, MacOS and MS-Windows, everywhere as a directory separator.

---

### Post by produktnz on 2023-06-19
SO MUCH gold in your reply, so thanks. And incidentally thanks for not ripping me a new one - I don't have a feel for the Brevity of this forum yet (balance between tomuchinfo/notenough)
Following along via putty, i used your lsblk command - there were a few options I didn't know you could specify.

```
root@micr0tank:~# lsblk -e 7 -o name,size,type,FSAVAIL,FSUSE%,fstype,mountpoint
NAME          SIZE TYPE  FSAVAIL FSUSE% FSTYPE          MOUNTPOINT
sda         465.8G disk                 isw_raid_member
&#9500;&#9472;md126     884.9G raid5
&#9474; &#9492;&#9472;md126p1 884.9G part   825.7G     0% ext4            /home
&#9492;&#9472;md127         0B md
sdb         465.8G disk                 isw_raid_member
&#9500;&#9472;md126     884.9G raid5
&#9474; &#9492;&#9472;md126p1 884.9G part   825.7G     0% ext4            /home
&#9492;&#9472;md127         0B md
sdc         465.8G disk                 isw_raid_member
&#9500;&#9472;md126     884.9G raid5
&#9474; &#9492;&#9472;md126p1 884.9G part   825.7G     0% ext4            /home
&#9492;&#9472;md127         0B md
sdd         476.9G disk
&#9500;&#9472;sdd1          1G part       1G     1% vfat            /boot/efi
&#9492;&#9472;sdd2        475G part   429.6G     3% ext4            /

root@micr0tank:~# df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sdd2      ext4  467G   14G  430G   3% /
/dev/sdd1      vfat  1.1G  6.1M  1.1G   1% /boot/efi
/dev/md126p1   ext4  870G  2.8M  826G   1% /home

```

To me, this looks like I've achieved as intended;
/home mounted to a separate larger, redundant volume. 
The last 'mental niggle' I have is with the device /dev/md126p1 <- this looks to me like i've mounted only 1 of the 3 SSD's despite that ssd being a raid member.

---

### Post by MAFoElffen on 2023-06-19
Not exactly... 

Think of RAID containers, traditionally wanting its containers as being the same sizes... As an engineer, you know that SATA, SAS, SSD, and NVME devices are beyond what is available for use inside of partition tables. Right? Especially on SSD's and NVMe's. There are reserved areas that the silicon storage uses for it's own use.

Often, when I have given mdadm, ZFS, LVM a whole RAW disk, for example you have given devices /dev/sd[a-c] as assets, then you have given unbound access to whatever it can use. Often enough, that has caused troubles for me down the road. You can get 30 disks of the same brand, model, in one lot purchase, and they may be different internally.

Over the last 10 years supporting people on this Forum, sometimes other people have that problem also... Enough for me to recommend to other people here, my customers, and my Computer Science students to always (first) write a partition table. Partition each disk, with partitions of a size you choose. That way you have total control of the size, and where writes are written.

Once I started doing that, I have had no unbound write error problems.

If you look at your output of lsblk, where it says the FSTYPE, the 'type' is written on the disk line instead of the partition line (where it should be). That is how I know you did
```

sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sd[a-c]

```
Instead of
```

sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sd[a-c]1

```
See the difference here:
```

mafoelffen@u-server-raid5-01:~$ lsblk -e 7 -o name,size,type,FSAVAIL,FSUSE%,fstype,mountpoint
NAME           SIZE TYPE  FSAVAIL FSUSE% FSTYPE            MOUNTPOINT
sr0            2.9G rom                  iso9660           
vda             40G disk                                   
&#9500;&#9472;vda1         512M part   504.9M     1% vfat              /boot/efi
&#9500;&#9472;vda2          20G part                 linux_raid_member 
&#9474; &#9492;&#9472;md126       40G raid5                                  
&#9474;   &#9500;&#9472;md126p1   31G part      19G    32% ext4              /
&#9474;   &#9492;&#9472;md126p2    9G part                 swap              [SWAP]
&#9492;&#9472;vda3        19.5G part                 linux_raid_member 
  &#9492;&#9472;md127       39G raid5                                  
    &#9492;&#9472;md127p1   39G part    35.9G     0% ext4              /home
vdb             40G disk                                   
&#9500;&#9472;vdb1         512M part                 vfat              
&#9500;&#9472;vdb2          20G part                 linux_raid_member 
&#9474; &#9492;&#9472;md126       40G raid5                                  
&#9474;   &#9500;&#9472;md126p1   31G part      19G    32% ext4              /
&#9474;   &#9492;&#9472;md126p2    9G part                 swap              [SWAP]
&#9492;&#9472;vdb3        19.5G part                 linux_raid_member 
  &#9492;&#9472;md127       39G raid5                                  
    &#9492;&#9472;md127p1   39G part    35.9G     0% ext4              /home
vdc             40G disk                                   
&#9500;&#9472;vdc1         512M part                 vfat              
&#9500;&#9472;vdc2          20G part                 linux_raid_member 
&#9474; &#9492;&#9472;md126       40G raid5                                  
&#9474;   &#9500;&#9472;md126p1   31G part      19G    32% ext4              /
&#9474;   &#9492;&#9472;md126p2    9G part                 swap              [SWAP]
&#9492;&#9472;vdc3        19.5G part                 linux_raid_member 
  &#9492;&#9472;md127       39G raid5                                  
    &#9492;&#9472;md127p1   39G part    35.9G     0% ext4              /home
mafoelffen@u-server-raid5-01:~$ cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] 
md126 : active raid5 vdc2[3] vda2[0] vdb2[1]
      41908224 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
      
md127 : active raid5 vda3[0] vdc3[3] vdb3[1]
      40855552 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
      
unused devices: <none>

```
I know. That is different than people's online tutorials on how to create mdadm RAID. Both methods will work. Both are correct. But that is just my experience learned with that.

Next... In your output there, I see that all 3 ssd's are members of md126, and that md126 is mounted as /home. (Not that only 'one' disk as mounted as /home.) All 3 disks are mounted as /home as a RAID array.

---

### Post by TheFu on 2023-06-19
> **produktnz said:**
> SO MUCH gold in your reply, so thanks. And incidentally thanks for not ripping me a new one - I don't have a feel for the Brevity of this forum yet (balance between tomuchinfo/notenough)
Following along via putty, i used your lsblk command - there were a few options I didn't know you could specify.

```
root@micr0tank:~# lsblk -e 7 -o name,size,type,FSAVAIL,FSUSE%,fstype,mountpoint
NAME          SIZE TYPE  FSAVAIL FSUSE% FSTYPE          MOUNTPOINT
sda         465.8G disk                 isw_raid_member
&#9500;&#9472;md126     884.9G raid5
&#9474; &#9492;&#9472;md126p1 884.9G part   825.7G     0% ext4            /home
&#9492;&#9472;md127         0B md
sdb         465.8G disk                 isw_raid_member
&#9500;&#9472;md126     884.9G raid5
&#9474; &#9492;&#9472;md126p1 884.9G part   825.7G     0% ext4            /home
&#9492;&#9472;md127         0B md
sdc         465.8G disk                 isw_raid_member
&#9500;&#9472;md126     884.9G raid5
&#9474; &#9492;&#9472;md126p1 884.9G part   825.7G     0% ext4            /home
&#9492;&#9472;md127         0B md
sdd         476.9G disk
&#9500;&#9472;sdd1          1G part       1G     1% vfat            /boot/efi
&#9492;&#9472;sdd2        475G part   429.6G     3% ext4            /

root@micr0tank:~# df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sdd2      ext4  467G   14G  430G   3% /
/dev/sdd1      vfat  1.1G  6.1M  1.1G   1% /boot/efi
/dev/md126p1   ext4  870G  2.8M  826G   1% /home

```

To me, this looks like I've achieved as intended;
/home mounted to a separate larger, redundant volume. 
The last 'mental niggle' I have is with the device /dev/md126p1 <- this looks to me like i've mounted only 1 of the 3 SSD's despite that ssd being a raid member.

So, I see some non-Best Practice setups with the mdadm arrays. The main issue is that you didn't put the array into a partition. You pointed it at the whole drive.  Later, when 1 drive fails, and all drives fail, you will likely be screwed.  The Best Practice is to use a partition of a very specific size (that you know) which can deal with slightly different sized drives in the future.  Then create the array on those partitions that you size exactly the same regardless of disk/vendor.  Be certain that partitions begin on sector boundaries to avoid really bad performance.  This can be 20-30% of a performance hit.  I usually take the number of sectors and round down so the number used for the partition end in 0000 or something like that.  Make it a deliberate size and it easy to type, since you'll likely be using this size partition for this array for the next 5 - 30 yrs.  Er ... or until you migrate to ZFS. ;)

Then, use LVM on top of the SW-RAID to split into logical sections for different mount needs.  Most storage doesn't need to allow setuid nor device files, for example, so prevent those through the mount options.
If you go to the effort to have RAID, please, please, please, also use a volume manager like LVM.  There are a number of best practices for using LVM - like allocate only the space you need for the next 3 months.  extending an LV is trivial. Making them smaller is a hassle.  Always leave empty space on the storage for unknown future needs.  In 30 yrs (now) of being an Admin, I've never, not once, guessed the correct storage needs for any system over the entire lifespan of an array. Best not to guess and to extend only when needed, the amount needed.  Plus, when you do run out of space, it is nice to have just a little left to add in as you wait for budget approval for new storage.  In some companies, that could take a day or 6 months.

Not sure if we talked about backups, but RAID never replaces backups.  Sometimes bad things happen to arrays where the easiest solution is to wipe it and start over.  Backups solve 1001 issues.  RAID solves just 2.

Your / partition is much too large. That's an understatement.  Sometimes we need to do a fresh install and not risking data on other partitions is easy, but sometimes we need to wipe the OS partition completely.  If you mix data and the OS, it will be harder.  DON'T.  Just don't.

---

