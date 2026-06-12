---
title: "How to get raid1 drive mount automatically?"
date: 2017-01-01
forum: New to Ubuntu
---

### Post by jcfaber1 on 2017-01-01
Hello and Happy New Year.  I have installed Xubuntu onto a SSD drive.  I have 2 6TB drives set as raid 1 through the Dell H310 raid controller.  I can mount the 6 tb drive and set up a partition through Gparted and can copy files onto the drive.  However when I restart the computer the drive is no longer mounted.  I added the following to /etc/fstab: /dev.sbd1 /srv/mythtv jfs defaults 0 2

When the system reboots I get the following error:
lvmetad is not active yet using direct activation during sysinit /dev/mapper/xubuntu  --vg-- root:clean, 283212/216217728 files 2225824/2484220 blocks  Welcome to emergency mode!  And so on.   If I edit the comment out the # /etc/fstab,  it will reboot just fine but I have have the problem with the drive not mounting.

I am not very UNIX/ubuntu savvy and appreciate any help.  What do I need to do to get this drive to mount automatically upon booting?

Thanks
John

---

### Post by jcfaber1 on 2017-01-02
I searched and found out to use the UUID for the device and is now working.

John

---

