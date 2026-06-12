---
title: "how recovery my system"
date: 2023-11-20
forum: New to Ubuntu
---

### Post by artemis25 on 2023-11-20
Hi
I have damage iso image from my ubuntu server but i have save all my EXT4 system (/boot/dev/etc/home/root/run/snap...var etc) . I install new ubuntu server with same system (22.04) and i want to know how can recover my old system from backup folder with those folders. My backup folders is in external usb-hdd. Thanks

---

### Post by MAFoElffen on 2023-11-20
As in, they wer backed up? Or the original files are in those folders on the other external hdd?

Basically, you list the devices to find the names an partitions of anything connected to the PC. Make sure with that, you know which filesystem types are inside of the partitions. You temporarily mount the partition to the system, then use rsync to copy the files, with the with their original ownership and permissions, to where you want them to be.

Being you installed server edition, all that would be by commands based on the information you found from commands and how the system see's things.

---

### Post by artemis25 on 2023-11-21
> As in, they wer backed up? Or the original files are in those folders on the other external hdd? My old folders  from old system is copy-paste partition (only EXT4 partition)  from old system (i know is wrong ) via  DISKGENIUS in windows !

 **I have install  new system ubuntu  hdd internal on pc** from zero and i stop on last update. My new system dont have any program run only ubuntu os. I have install new ubuntu system same version ,same user name, same passwd with old (22.04)  . I log in in my new fresh ubuntu system , put my  old folders in external hdd and i put in in usb external ... How can recovery my old system from external hdd ? Thanks

---

