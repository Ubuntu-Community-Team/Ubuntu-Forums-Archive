---
title: "Remove disk from Raid5 configuration"
date: 2013-11-20
forum: New to Ubuntu
---

### Post by info8 on 2013-11-20
In a HP Proliant DL360 G6 i have made a Raid 5 with 4 sas drives.

The HP Proliant makes use of a Array Controller (HP Smart Array P410i/256 mb (RAID 0/1/1+0/5/5+0).
I had to use this otherwise the Ubuntu software doesn't recognize the installed drives.
All drives separately configures as raid0 in the HP Smart Array controller, so Ubuntu could recognize all 4 drives. 
After this i set-up the RAID5 configuration in Ubuntu.

md0 is created as swap area (40gb each drive), 
 md1 (3x106gb and 1x33gb, rest volume all 4 drives) is the bootable area. 
So all 4 disks are configured the same.

 I use 4 disks: 3x 146gb (10k) and 1x73gb (15)

my mdstat is looks like:
[B][I]md0 : active raid5 sdc1[2] sda1[0] sdb1[1] sdd1[3]
          117084672 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]

md1 : active raid5 sdb2[1] sda2[0] sdc2[2] sdd2[3]
          97718784 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]

unused devices: <none>
[/I][/B]

Problem: 
When i use: ***sudo adm --remove /dev/md0 dev/sdd1     ***or                      [B][I]sudo adm --remove /dev/md1 dev/sdd2
[/I][/B]
i get: [B][I]hot remove failed for /dev/sdd1: Device or resource busy 
[/I][/B]
Question: 
What do i forget or wrong? 

How can i remove the 73gb (md0 sdd1 (swap area) and md1 sdd2 boot area) from this raid and add another 146gb sas drive?

---

