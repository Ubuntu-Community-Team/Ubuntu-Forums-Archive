---
title: "Store data on one specific disk"
date: 2013-09-09
forum: New to Ubuntu
---

### Post by Tjalleman on 2013-09-09
Hi all,

I've a home file-server with two disks: a SSD (16GB) and a normal HD (2TB). I want to store all my data on the HD and use the SSD for install puposes only. How can I setup Ubuntu in such way that a specific folder (lets say \data) is stored only on the SD and not partly on the SSD? I want to do this because I want to spin down the HD when it is not in use.

Thanks!

---

### Post by bab1 on 2013-09-09
> **Tjalleman said:**
> Hi all,

I've a home file-server with two disks: a SSD (16GB) and a normal HD (2TB). I want to store all my data on the HD and use the SSD for install puposes only. How can I setup Ubuntu in such way that a specific folder (lets say \data) is stored only on the SD and not partly on the SSD? I want to do this because I want to spin down the HD when it is not in use.

Thanks!

Wherever you create a mount point and subsequently mount a partition is where all of the data will be stored.  

An example could be something like the following.  You create a mount point such as /data on the SSD.  This is nothing more than making a directory data at the / (aka /data).  Then you create a single partition on the 2TB HDD.  You now can mount that partition at /data.  Everything you store on /data will be on the 2TB partition on the HDD.  The original /data directory is hidden from use as long as the partition is mounted.

---

### Post by Tjalleman on 2013-09-09
Thank you for the reply. I did as you recommended and it worked perfectly.

what i did:
- made a new folder (/data)
- partitioned HD (I did this already during the installation)
- made a new file system that contains the whole disk (/dev/sdb)
- mounted the disk to /data

I checked the setting with the sudo df -H command. The output confirms that the HD is mounted to /data

---

