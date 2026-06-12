---
title: "How To - create a RAID array in Edgy"
date: 2007-02-25
forum: Outdated Tutorials &amp; Tips
---

### Post by caffienda on 2007-02-25
I decided to create a 5 disk RAID 0 array in Linux.  I'm running Ubuntu 6.10

Here is the procedure I used and seems to be working very well.  
```
sudo apt-get install mdadm
sudo fdisk /dev/hda1 
(delete all partiions, by using the "d" command, then the partition #. Then created a primary 
partition, with a "n" then "p" and then "1"  and select the defaults by hitting enter for start and 
end size.  Then used "t" and "83" for partition type)  Repeat for all the drives to be used in the 
array
                    /dev/hde1 
                    /dev/hdf1 
                    /dev/hdg1 
                    /dev/hdh1
```

```
[COLOR="Blue"]cd /dev/
sudo  MAKEDEV md
sudo modprobe md
sudo mdadm --create --verbose [COLOR="Red"]/dev/.static/dev/md0[/COLOR] --level=0 --raid-devices=5 /dev/hda1 /dev/hde1 /dev/hdf1 /dev/hdg1 /dev/hdh1[/COLOR] 
You can change the --level=0 to the appropriate level for the array you are configuring
***mdadm: layout defaults to left-symmetric
***mdadm: chunk size defaults to 64K
***mdadm: /dev/hde1 appears to be part of a raid array:
***    level=raid5 devices=5 ctime=Wed Feb 21 03:27:41 2007
***mdadm: /dev/hdf1 appears to be part of a raid array:
***    level=raid5 devices=5 ctime=Wed Feb 21 03:27:41 2007
***mdadm: /dev/hdg1 appears to be part of a raid array:
***    level=raid5 devices=5 ctime=Wed Feb 21 03:27:41 2007
***mdadm: /dev/hdh1 appears to be part of a raid array:
***    level=raid5 devices=5 ctime=Wed Feb 21 03:27:41 2007
***mdadm: size set to 156288256K
***Continue creating array? y
***mdadm: array /dev/.static/dev/md0 started.
``` ***denotes operation output
I used [COLOR="Red"]/dev/.static/dev/md0[/COLOR]  because it was posted in another HowTo that I used some info from. Why not just use /dev/md0?  How does this affect the array down the road?  id the /dev/.static needed?
```
[COLOR="Blue"]cat /proc/mdstat[/COLOR]
***Personalities : [raid5] [raid4] [raid0] 
***md0 : active raid0 hda1[0] hdh1[4] hdg1[3] hdf1[2] hde1[1]
***      781443648 blocks 64k chunks
```
```
sudo mdadm -S /dev/md0
``` Used to stop the array
```
sudo gedit /etc/mdadm.conf
```Add the following lines:
```
DEVICE  /dev/hda1 /dev/hde1 /dev/hdf1 /dev/hdg1 /dev/hdh1
ARRAY   /dev/md0 devices=/dev/hda1,/dev/hde1,/dev/hdf1,/dev/hdg1,/dev/hdh1
```
```
[COLOR="Blue"]sudo mdadm --detail --scan[/COLOR]
***ARRAY /dev/md0 level=raid0 num-devices=5 UID=54623f8b:b3b44af:45dca40a:d0833744

```
The following is used to start the array
```
[COLOR="Blue"]sudo mdadm -A /dev/md0 /dev/hda1 /dev/hde1 /dev/hdf1 /dev/hdg1 /dev/hdh1[/COLOR]
***mdadm: /dev/md0 has been started with 5 drives.

```
```
[COLOR="Blue"]sudo mdadm -E /dev/hda1[/COLOR]
/dev/hda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 54623f8b:b3b44af:45dca40a:d0833744
  Creation Time : Sun Feb 25 13:54:18 2007
     Raid Level : raid0
    Device Size : 0
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Sun Feb 25 13:54:18 2007
          State : active
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 436417f3 - correct
         Events : 0.1

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       3        1        0      active sync   /dev/hda1

   0     0       3        1        0      active sync   /dev/hda1
   1     1      33        1        1      active sync   /dev/hde1
   2     2      33       65        2      active sync   /dev/hdf1
   3     3      34        1        3      active sync   /dev/hdg1
   4     4      34       65        4      active sync   /dev/hdh1

```
I created /media/raid directory for my array mounting point,  then adding this to my fstab
```
sudo gedit /etc/fstab
```
I added the following:
```
 /dev/md0      /media/raid     ext3    defaults  0    0
``` 
```
[COLOR="Blue"]sudo gedit /etc/mtab[/COLOR]
```
add```
 /dev/md0 /media/raid ext3 rw 0 0
```
I then created the FS with this:
```
[COLOR="Blue"] sudo mke2fs -j /dev/.static/dev/md0[/COLOR]
***mke2fs 1.39 (29-May-2006)
***Filesystem label=
***OS type: Linux
***Block size=4096 (log=2)
***Fragment size=4096 (log=2)
***97681408 inodes, 195360912 blocks
***9768045 blocks (5.00%) reserved for the super user
***First data block=0
***Maximum filesystem blocks=197132288
***5962 block groups
***32768 blocks per group, 32768 fragments per group
***16384 inodes per group
***Superblock backups stored on blocks: 
***        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
***       4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
***        102400000
***Writing inode tables: done                            
***Creating journal (32768 blocks): done
***Writing superblocks and filesystem accounting information: done
***This filesystem will be automatically checked every 24 mounts or
***180 days, whichever comes first.  Use tune2fs -c or -i to override.

``````
[COLOR="Blue"] sudo fdisk -l[/COLOR]

***Disk /dev/hda: 160.0 GB, 160041885696 bytes
***137 heads, 8 sectors/track, 285202 cylinders
***Units = cylinders of 1096 * 512 = 561152 bytes

***   Device Boot      Start         End      Blocks   Id  System
***/dev/hda1               1      285202   156290692   83  Linux

***Disk /dev/sda: 37.0 GB, 37019566080 bytes
***255 heads, 63 sectors/track, 4500 cylinders
***Units = cylinders of 16065 * 512 = 8225280 bytes

***   Device Boot      Start         End      Blocks   Id  System
***/dev/sda1   *           1        4314    34652173+  83  Linux
***/dev/sda2            4315        4500     1494045    5  Extended
***/dev/sda5            4315        4500     1494013+  82  Linux swap / Solaris

***Disk /dev/sdb: 74.3 GB, 74355769344 bytes
***255 heads, 63 sectors/track, 9039 cylinders
***Units = cylinders of 16065 * 512 = 8225280 bytes

***   Device Boot      Start         End      Blocks   Id  System
***/dev/sdb1               1        1200     9638968+  83  Linux
***/dev/sdb3            1201        3000    14458500   83  Linux
***/dev/sdb4            3001        9039    48508267+  83  Linux

***Disk /dev/hde: 160.0 GB, 160041885696 bytes
***255 heads, 63 sectors/track, 19457 cylinders
***Units = cylinders of 16065 * 512 = 8225280 bytes

***   Device Boot      Start         End      Blocks   Id  System
***/dev/hde1               1       19457   156288321   83  Linux

***Disk /dev/hdf: 160.0 GB, 160041885696 bytes
***255 heads, 63 sectors/track, 19457 cylinders
***Units = cylinders of 16065 * 512 = 8225280 bytes

***   Device Boot      Start         End      Blocks   Id  System
***/dev/hdf1               1       19457   156288321   83  Linux

***Disk /dev/hdg: 160.0 GB, 160041885696 bytes
***255 heads, 63 sectors/track, 19457 cylinders
***Units = cylinders of 16065 * 512 = 8225280 bytes

***   Device Boot      Start         End      Blocks   Id  System
***/dev/hdg1               1       19457   156288321   83  Linux

***Disk /dev/hdh: 160.0 GB, 160041885696 bytes
***255 heads, 63 sectors/track, 19457 cylinders
***Units = cylinders of 16065 * 512 = 8225280 bytes

***   Device Boot      Start         End      Blocks   Id  System
***/dev/hdh1               1       19457   156288321   83  Linux

[COLOR="Red"]***Disk /dev/md0: 800.1 GB, 800198295552 bytes
***2 heads, 4 sectors/track, 195360912 cylinders
***Units = cylinders of 8 * 512 = 4096 bytes

***Disk /dev/md0 doesn't contain a valid partition table[/COLOR]
```
Finally, make sure you have nothing else running and reboot your computer.

```
sudo reboot
```

---

### Post by fakie_flip on 2007-02-27
What about running all partitions in raid instead of just adding new partitions to put in a raid? How can you do it? You can't format your / partition partition that your system is running on. I added another drive to my computer. I would like to mirror all of the first drive onto the second drive using raid 1. How can I do it?

---

