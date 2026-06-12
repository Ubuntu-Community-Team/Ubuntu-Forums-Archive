---
title: "Fake RAID issue"
date: 2012-04-18
forum: New to Ubuntu
---

### Post by DaveSny on 2012-04-18
[SIZE=3][FONT=Calibri]Hello Ubuntu community![/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Yep I’m a beginner for sure and I was hoping someone could help me out. I discovered Ubuntu a couple days ago and had the need to create a machine I could use for redundant backups. I had an antique P4 with a 3 gig processor that I knew still ran and a stack of 80 GB (identical) ATA ST380211AS Seagate barracuda drives. I also had a fake RAID controller (AHA 1420sa). The system disk is new solid state ATA INTEL SSDSC2CW120A3 and 4 gigs of RAM. The build was straight forward and went off without a hitch, hats off to you and truly a sweet OS . I used the Community Doc. MountingWindowsPartitions to create the RAID 0 stack and it seemed to go well though I’m unsure that I have the mount points correct? When I copied a 1 GB file to ntfs share the byte count increased on the system drive or so it seemed and is where I’m “misconfused.” [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Using the command lines provided this is what I’ve got so far.[/FONT][/SIZE]
[FONT=Tahoma][SIZE=3]root@SpDemon:~# sudo fdisk -l | grep NTFS | awk '{print $1}'[/SIZE][/FONT]
[FONT=Tahoma][SIZE=3]/dev/sdb1[/SIZE][/FONT]
[FONT=Tahoma][SIZE=3]/dev/sdc1[/SIZE][/FONT]
[FONT=Tahoma][SIZE=3]/dev/sdd1[/SIZE][/FONT]
[FONT=Tahoma][SIZE=3]---------------------------------------------------------------------------------[/SIZE][/FONT]
[FONT=Tahoma][SIZE=3]root@SpDemon:~# ls -l /dev/disk/by-uuid/[/SIZE][/FONT]
[FONT=Tahoma][SIZE=3]total 0[/SIZE][/FONT]
[FONT=Tahoma][SIZE=3]lrwxrwxrwx 1 root root 10 2012-04-18 08:30 10A06FCF0B1E8297 -> ../../sdc1[/SIZE][/FONT]
[FONT=Tahoma][SIZE=3]lrwxrwxrwx 1 root root 10 2012-04-18 08:30 3F4F48E971C6345B -> ../../sdd1[/SIZE][/FONT]
[FONT=Tahoma][SIZE=3]lrwxrwxrwx 1 root root 10 2012-04-18 08:30 45c60d25-3d34-4b46-b6bb-2f19b3d41cdc -> ../../sda1[/SIZE][/FONT]
[FONT=Tahoma][SIZE=3]lrwxrwxrwx 1 root root 10 2012-04-18 08:30 7B1109992984E3E9 -> ../../sdb1[/SIZE][/FONT]
[FONT=Tahoma][SIZE=3]lrwxrwxrwx 1 root root 10 2012-04-18 08:30 b7ba0162-a840-4558-a2fc-d14b9cdf65ec -> ../../sda5[/SIZE][/FONT]
[FONT=Tahoma][SIZE=3]-----------------------------------------------------------------------------------------------------------[/SIZE][/FONT]
[FONT=Tahoma][SIZE=3]root@SpDemon:~# sudo dmraid -ay[/SIZE][/FONT]
[FONT=Tahoma]no raid disks < ------------------------------------- I was wondering about this.[/FONT]
[FONT=Tahoma][/FONT] 
[FONT=Tahoma]Any help would be greatly appreciated.[/FONT]
[FONT=Tahoma]Kind regards,[/FONT]
[FONT=Tahoma]Dave[/FONT]

---

