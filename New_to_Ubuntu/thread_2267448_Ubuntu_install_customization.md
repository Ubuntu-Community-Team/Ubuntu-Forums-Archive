---
title: "Ubuntu install customization"
date: 2015-03-01
forum: New to Ubuntu
---

### Post by razvan4 on 2015-03-01
I have just installed ubuntu 14.04.2 on my system. I have a few questions how to mount my hdd drives and get write permisions? I have 6 hdd drives 3 sata 3, 2 sata 2 and one ssd. I have edited the fstab file lets say something like this: 
/dev/sda6 /media/stocare1 ext4 defaults 0 0
/dev/sda7 /media/stocare2  ntfs  defaults 0 0
/dev/sdb1 /media/stocare3  ext4  defaults 0 0
/dev/sdb2 /media/stocare4  ntfs  defaults 0 0
/dev/sdc1 /media/stocare5  ext4  defaults 0 0
/dev/sdc2 /media/stocare6  ntfs  defaults 0 0

etc .

---

### Post by Old_Grey_Wolf on 2015-03-01
It has been a long time since I mounted a ntfs partition using fstab on Linux so things may have changed.

Someone may correct me but I think the ntfs partitions default to read only. I think you need to change "defaults" to "rw" for those entries in fstab.

Try defaults and if that doesn't work try rw.

---

### Post by kerry_s on 2015-03-01
it's easier to use the "disks" app, you can select to mount at start up, it does all the work. you don't have to change anything just turn the option on for each disk.

open "disks", select drive, click gear bottom left, select edit mount options, just turn the switch on.

---

