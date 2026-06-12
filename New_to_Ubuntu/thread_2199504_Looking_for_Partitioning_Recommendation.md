---
title: "Looking for Partitioning Recommendation"
date: 2014-01-14
forum: New to Ubuntu
---

### Post by ghatt on 2014-01-14
I've read a few guides on partitioning but haven't found a scheme that fully fits my situation. I'm fairly new to linux and am looking for the most effecient setup for easily backing up.

I have two hard-drives: 
[LIST=1]
[*]120GB SSD 
[*]1TB HDD 
[/LIST]

My thinking for my partitioning scheme is:
[LIST=1]
[*]120GB SSD 
[/LIST]

[LIST]
[*]20 GB for / 
[*]8 GB for Swap 
[/LIST]
     2. 1TB HDD
[LIST]
[*]75GB for Home 
[*]925GB for Storage 
[/LIST]

My questions are: 
[LIST=1]
[*]Is this an OK setup for easily backing up? I'm pretty picky about my configurations for programs and don't want to have to re-configure my applications? 
[*]I feel like this is a rather large waste of a lot of space on the SSD but where Ubuntu is my own SSD I don't know what to do with the remaining space. 
[*]During installation if I create a storage partition do I just make it EXT4 and set the mount point to /Storage? 
[/LIST]

Thanks for any suggestions,
           Greg

**SOLVED: Along with everyone's suggestions I took some time and read some of the Ubuntu "help" documentation. If you've got questions about how partitioning works or how to configure a hard disk or really any questions related to storage you should check out: [https://help.ubuntu.com/community/DrivesAndPartitions](https://help.ubuntu.com/community/DrivesAndPartitions)**

---

### Post by bertan2 on 2014-01-14
Application settings will tend to be in /etc. Is that what you want to back up? Or you want /storage to be easily backed up?

---

### Post by ghatt on 2014-01-14
Storage won't have to be backed up; eventually I might by another HDD to back it up but for now I just have my files on a external HDD. I guess I'm thinking of backing up my applications and configurations. Is my thinking right as far as creating the storage partition during installation? My thinking it: to re-install my ubuntu system I'd only have to re-install the / partiion.

---

### Post by Dave_L on 2014-01-14
I don't see any advantage to creating the storage partition during installation vs. creating it afterwards.

I would leave some unallocated space for future use.  For example, you might want to install a newer version of Ubuntu on a trial basis before switching over to it permanently. Or you might want to try out a different edition such as Xubuntu. But the extra space on your SSD should suffice for that.

---

### Post by mastablasta on 2014-01-14
> **ghatt said:**
>  I guess I'm thinking of backing up my applications and configurations.


depends really what applicaitons and how they were installed. if we talk about software center applicaitons... then backup for this will only be a few MB at most. a script can be made for installed applications so they get reinstalled when system i reinstalled. settings and config files don't take up much space especially when compressed.

your setup is a bit strange. most people would use external disk for backup rather than as a main disk. but ok, it's your choice.

what abut th rest of the SSD? why not just create / and /swap (if you even need it) on SSD and use the other disk for storage? then you can image the whole OS to storage disk or you can use for example mint backup tool and backup applications settings etc. (backup software selection button) to storage and just reinstall (even reformat) the whole thing on SSD.

---

### Post by ghatt on 2014-01-14
Thanks for the help. I'm going to go with SSD : / = 25GB, Swap = 8GB, /home = REMAINDER; HDD - 100% Storage. Do I need to make a seperate partitioning for backup?

---

### Post by oldfred on 2014-01-14
I prefer to have each drive fully bootable with a system. And I now partition all drives with the newer gpt partitioning scheme not the older MBR(msdso). Only if you may install Windows may you need MBR as Windows only boots from gpt partitioned drives with UEFI. Ubuntu boots with UEFI or BIOS, if correct supporting partition is available.
Backup is more to worry about hard drive failure. So separate partition on same drive does not help much. It may provide some cases where you have another copy of files, in case of user error, but often backup overwrites files or deletes the copy your really wanted before you know you made a mistake. Or better to have version backups.

On my 64GB drive I have two / (root) partitions one for current install and one for future/testing. Both link into a /mnt/data partition on my rotating hard drive, so I have access to all my data, but each has /home inside its install so I can have different configurations. I may copy some configuration from one /home to another manually, but do not attempt to share /home across versions.

       [https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

      
 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

