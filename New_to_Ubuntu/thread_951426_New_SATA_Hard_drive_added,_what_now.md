---
title: "New SATA Hard drive added, what now?"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by fletcham on 2008-10-18
Hi,

I have bought a new SATA hard drive as I'd ran out of space on the other. I have connected it to the PSU and motherboard. I have turned the PC on but it does not show.

Please could someone let me know the steps I need to take to sort it out. Im really new to this so please keep it simple.

Thanks a lot for your help, i'd have no chance without this site

Cheers:popcorn:

---

### Post by cherva on 2008-10-18
Look in /dev there should be sdb1 if it is formated in 1 partition
and sdb2 if they are two and so on.... then mount them where you want ... sudo mount /dev/sdb1 /where/you/want/to/mount/it and then add this drive to /etc/fstab to automount on boot :) When you open fstab it is more than self explanatory what you should do...

---

### Post by hyper_ch on 2008-10-18
install gparted to format the drive to ext3 and then look up how to "mount" it.

---

### Post by expatCM on 2008-10-18
Lots of information in this link that should help you
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

### Post by stinger30au on 2008-10-18
fireup your terminal screen and do a 

gksudo gparted


making sure you have gparted installed first

navigate to /sdb1

so long as this is the only sata drive you have and create a new partition on it and format it

---

