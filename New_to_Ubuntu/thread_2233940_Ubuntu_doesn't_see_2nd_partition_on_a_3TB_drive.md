---
title: "Ubuntu doesn't see 2nd partition on a 3TB drive"
date: 2014-07-11
forum: New to Ubuntu
---

### Post by Kimo Xvirus on 2014-07-11
Hello,

I have a 3 TB Seagate Hard Drive, it was formatted on Windows XP to 2 partitions, one 2TB and the other ~750 GB.
To see the 2 drives on windos correctly, I have to install the Seagate Disc Wizard which includes some drive that that recognizes them correctly.

When I installed Linux, I only found the first partition mounted. The other partition appears as "Unallocated Space" in both Gparted and Ubuntu's Disks.

How can I recognize and mount this 2nd partition on Ubuntu?

---

### Post by oldfred on 2014-07-11
Not sure how XP would have even created a second usable partition. Perhaps drive vendor created some work around.
But XP does not work with gpt partitioned drives and drives over 2.2TB have to have gpt. 
There were a few kluge type work arounds which it seems you have. That also is Windows only unless Seagate also has a Linux driver.

Post this for drive.
sudo parted -l

Install and post from gdisk, but change from sda to drive that is Seagate drive.
       sudo apt-get install gdisk
sudo gdisk -l /dev/sda

      
 MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)


 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

