---
title: "RAID6 degraded, need Help.."
date: 2019-11-17
forum: New to Ubuntu
---

### Post by purelove on 2019-11-17
Today decided to add 5th drive to the RAID6 array for storage  expansion. 
The disk appeared in fdisk -l, also i double checked the  state of raid after booting with extra drive, and it was clean with 4  drives.  i’ve created needed partitions on the new drive, added to the  mdadm. At this stage 5th drive suppose to stay as “spare”, but i’ve  noticed very strange situation. Instead of 4 healthy drives and 5th as a  spare, i found that 3 drives are healthy, 4th drive is re syncing after  degradation, while 5th drive (not the one i’ve added) is faulty. Would  be not that bad, but… for doing this upgrade i took the server out of  it’s place and lie on the desk. Before leaving server room, i  accidentally moved a bit server case a few centimetres (as i left it on  the desk) and power cord popped out…

Now i have “error: ELF header smaller than expected, entering rescue mode”.

I’ve tried over the grub made these steps:


set prefix=(md/1)/boot/grub
set root=(md/1)
insmod normal (after this command i get: ELF header smaller than expected)


Then i’ve tried “Boot repair”, but for some reason i can't see the button "Recommended repair", i only can make a report.


This is boot repair info:

[URL="http://paste.ubuntu.com/p/mWfWgVFBs7/"]
http://paste.ubuntu.com/p/mWfWgVFBs7/[/URL]


Any ideas for this repair are very welcome.


Thank you.

---

### Post by TheFu on 2019-11-18
I've never used RAID6.  There might be a way to address this but if it has been over a day, I'd wipe all the disks, recreate the RAID set I want using all the disks, then restore from backups.

RAID never replaces backups and sometimes the easiest answer to RAID problems is to start over using backup data.

Boot-repair only works for trivial storage situations. I've never heard of it handling RAID-anything.

---

