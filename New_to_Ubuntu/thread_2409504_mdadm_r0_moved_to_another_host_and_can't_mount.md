---
title: "mdadm r0 moved to another host and can't mount"
date: 2019-01-03
forum: New to Ubuntu
---

### Post by alex346 on 2019-01-03
hello,

I have moved my system hdd from normal computer hardware (consumer PC) to pro server hardware (HP proliant)
The system boots and works OK, hostname is the same.


But... I have had also moved disks which are set in RAID based on mdadm (both mobos SATA ports set as AHCI).


And now I can see the disks properly but when I am mounting I cant see any files/content.


When I am running testdisk on /dev/md0 I can see the filelist from root directory but all is in red colour and can't do anything with that.


How I have done it:
I have configured 2 another , independent raid devices md0 and md1. Each one is based on 2 disks. Disks are OK and healthy. 


The only one thing which changed -  the drive letters - ex. sdb instead of sdp 


Should I remove old /etc/mdadm/mdadm.conf file ? I have tried to rename it and do 


mdadm --assemble --scan without success.


I have made the ext4  filesystem over the devices - so, for example,  I have /dev/md0 partitioned as ext4

regards

---

