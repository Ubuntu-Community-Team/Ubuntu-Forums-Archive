---
title: "invalid partition table-wrong signature e1f5"
date: 2013-03-05
forum: New to Ubuntu
---

### Post by odin234 on 2013-03-05
hi guys,
i am a noob ubuntu user, my pc was fine until yesterday and now it says that i have an invalid partition table, i am using the live cd ubuntu 12.04 now since all my HDD is missing,
[IMG]http://img201.imageshack.us/img201/2434/screenshotfrom201303051.png[/IMG]

 i was looking online for solutions and got this w the sudo fdisk -lu comand

```
ubuntu@ubuntu:~$ sudo fdisk -lu
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0xe1f5 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 400.1 GB, 400088457216 bytes
240 heads, 63 sectors/track, 51681 cylinders, total [COLOR=#ff0000]781422768 sectors[/COLOR]
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x29c7d638

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    25189919    12594928+  83  Linux
/dev/sda2        25189920   614416319   294613200    f  W95 Ext'd (LBA)
/dev/sda3       614416320   655376399    20480040    7  HPFS/NTFS/exFAT
/dev/sda4       655376400   781401599    63012600    7  HPFS/NTFS/exFAT
[COLOR=#ff0000]**/dev/sda5   ?  1287063685   941516022**[/COLOR]  1974709817   b9  Unknown

Disk /dev/sdb: 3926 MB, 3926949888 bytes
16 heads, 16 sectors/track, 29960 cylinders, total 7669824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064     7669823     3830880    c  W95 FAT32 (LBA)


```

i think the red part is the problem but i dont know how 2 fix it, i have 2 missing partitions and the sda2 (win7) is way bigger than what i remember in that space there should be 3 partitions and not only the win7

---

### Post by oldfred on 2013-03-05
It says running fdisk and doing a write will correct invalid entry, but I am not sure partition will stil be wrong. It size is not valid. Was it swap inside the extended partition and should have the same size and sector counts as the extended partition?

       First backup partition table,
sudo sfdisk -d /dev/sda > parts_sda.txt

    
You can try fdisk.
       this occasionally fixes issues and is worth trying:
you do the following :
fdisk /dev/sda
use option : x (expert mode)
use option : f (fix partition order)
use option : r (return)
use option : p (to print)
use option : v to verify partition
if it is ok
then you can do
option : w ( to write table to disk)
option : q to quit
else if it is not ok
then post the output of option p and v

But most have good sucess with fixparts.
      
 Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by odin234 on 2013-03-05
It says running fdisk and doing a write will correct invalid entry, but I  am not sure partition will stil be wrong. It size is not valid.** Was it  swap inside the extended partition and should have the same size and  sector counts as the extended partition?**

maybe, idk, not sure...

```
odin@odin-OEM:~$ sudo fdisk /dev/sdb
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5

Command (m for help): x

Expert command (m for help): f
Nothing to do. Ordering is correct already.


Expert command (m for help): p

Disk /dev/sdb: 240 heads, 63 sectors, 51681 cylinders

Nr AF  Hd Sec  Cyl  Hd Sec  Cyl     Start      Size ID
 1 80   1   1    0 239  63 1023         63   25189857 83
 2 00 239  63 1023 239  63 1023   25189920  589226400 0f
 3 00 239  63 1023 239  63 1023  614416320   40960080 07
 4 00 239  63 1023 239  63 1023  655376400  126025200 07
 5 04 112  61  406 102  59  975 1261873765 3949419634 b9

```

@[URL="http://ubuntuforums.org/member.php?u=852711"][B][COLOR=#C61919][B]oldfred
[/B][/COLOR][/B][/URL]      
ty i get this w fdisk will try fixparts now

```
FixParts 0.8.6

Loading MBR data from /dev/sdb
Unable to seek to 2372826984! Aborting!
EBR signature for logical partition invalid; read 0x0001, but should be 0xAA55
Error reading logical partitions! List may be truncated!
Warning: Deleting oversized partition #5! Start = 1287063685, length = 3949419634

MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 781422768 sectors (372.6 GiB)
MBR disk identifier: 0x29C7D638
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *             63     25189919   primary     Y        Y      0x83
   3             614416320    655376399   logical     Y        Y      0x07
   4             655376400    781401599   primary              Y      0x07




```

fixparts


from testdisk dont know if this help...
[IMG]http://imageshack.us/a/img687/2434/screenshotfrom201303051.png[/IMG]
[IMG]http://imageshack.us/a/img585/2434/screenshotfrom201303051.png[/IMG]
[IMG]http://imageshack.us/a/img594/4954/screenshotfrom201303051q.png[/IMG]

---

### Post by oldfred on 2013-03-05
Since the issue was with a logical partition, did you save from fixparts and is it now correct?
post this to see if changed:
sudo fdisk -lu

---

### Post by odin234 on 2013-03-05
```
Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x29c7d638

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    25189919    12594928+  83  Linux
/dev/sdb2       614416319   655376399    20480040+   f  W95 Ext'd (LBA)
/dev/sdb4       655376400   781401599    63012600    7  HPFS/NTFS/exFAT
/dev/sdb5       614416320   655376399    20480040    7  HPFS/NTFS/exFAT


```

it looks like this now...

---

### Post by oldfred on 2013-03-06
That looks correct. But NTFS partitions have to have a valid NTFS PBR or partition boot sector. If if mounts and works it is ok. Otherwise fixBoot and chkdsk may be required. May be a good idea to run chkdsk anyway.

Why did data get corrupted. Have you used Disk Utility and looked at your drive? If you look on right side it shos Smart data on drive. It has lots of detail but all I know is green is good.

Always good idea to have current backups.

---

### Post by odin234 on 2013-03-07
> **oldfred said:**
> That looks correct. But NTFS partitions have to have a valid NTFS PBR or partition boot sector. If if mounts and works it is ok. Otherwise fixBoot and chkdsk may be required. May be a good idea to run chkdsk anyway.

Why did data get corrupted. Have you used Disk Utility and looked at your drive? If you look on right side it shos Smart data on drive. It has lots of detail but all I know is green is good.

Always good idea to have current backups.

my little brother was using testdisk 2 change a swap>ntsf, i think he mess up some stuff

i find the problem w the table i never have a /dev/sdb1 with that size thats what cause the overlapping problem, so i delete it and fix it, i manage to recover 2 of the missing partitions and the chkdsk do the rest, still have one missing but i find the first sector _409,615,983_

---

