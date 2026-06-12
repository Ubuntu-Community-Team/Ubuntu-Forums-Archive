---
title: "Ubuntu 18.04 do not mount a hdd when dual boot aside windows 10 on sdd?"
date: 2018-09-24
forum: New to Ubuntu
---

### Post by shennguyen on 2018-09-24
[COLOR=#242729][FONT=Arial]Hi i recently installed ubuntu 18 aside with windows 1o on a ssd drive. Beacuse i had a Samsung Evo to boot Windows and Ubuntu, and internal hdd to store my data. I want to connect my hdd drive to share files cross by 2 systems. However, my ubuntu only mounted my ssd drive despite of not turn off fast startup on Windows 10. I tried to mount my hdd but it does not success and my hdd still running while can not access. I searched around to define the problems and some solutions that i tried such as - install nfs-common - turn-off fast star-up on Windows 10 Here are some information for you guys to help me. Thank you :)

[/FONT][/COLOR]```

[SIZE=2][COLOR=#242729][FONT=Consolas]Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors[/FONT][/COLOR]
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: F94A6D4D-66FA-11E8-ABB9-3065EC690606

Device         Start       End   Sectors   Size Type
/dev/sda1       2048    616455    614408   300M Windows recovery environment
/dev/sda2     616456    821263    204808   100M EFI System
/dev/sda3     821264   1083415    262152   128M Microsoft reserved
/dev/sda4    1083416 371249216 370165801 176.5G Microsoft basic data
/dev/sda5  371251200 488396799 117145600  55.9G Linux filesystem


Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: DB2FACA4-C1C5-4B2B-9B7E-1190B28103F8

Device      Start        End    Sectors   Size Type
/dev/sdb1      34       2081       2048     1M Microsoft LDM metadata
/dev/sdb2    2082     262177     260096   127M Microsoft reserved 
/dev/sdb3  262178 1953525134 1953262957 931.4G Microsoft LDM data[/SIZE]

```

---

### Post by oldfred on 2018-09-24
You are showing Microsoft LDM data which is Microsoft's proprietary dynamic partition system. 
Linux used to not even see dynamic partitions, but now sees them, but does not work with them.

But part of reason for dynamic partitions was the old MBR 4 primary partition limit. It was Microsoft's work around, somewhat similar to LVM in Linux (logical volumes inside physical partitions). 
But with gpt there is essentially no primary partition limit, so no real reason for dynamic partitions.
How did you convert drive to dynamic partitions.

Some third party Windows tools may convert them back to standard partitions. Microsoft's own solution is backup, total reformat and restore. But even if converting in place, you need to have good backups.

       [http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Shown as SFS, Dynamic also on gpt as LDM 
      
 Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm) 
   Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)

---

### Post by gpeguero on 2018-09-24
Hi, I am currently running a similar setup on my ThinkPad I have a 240gb SSD running Ubuntu 18.04 and Windows 10 Pro. What I use to share data between the two system is a Synology NAS (Network Attached Storage) and a created a shared folder for both systems. the setup is super straightforward and the Synology UI is very easy to use. I would recommend looking into something like this. This is the one I use if you want to find out more information about it: [http://www.synology.com/en-us/products/DS218j](http://www.synology.com/en-us/products/DS218j)  
Good Luck. :)

---

### Post by shennguyen on 2018-09-24
Thank you so much, i have done with my problem :)

---

