---
title: "Mount 2nd hard disk"
date: 2014-01-11
forum: New to Ubuntu
---

### Post by Clemens_Wolff on 2014-01-11
Hello everyone,

i have a question regarding to mount a second hard disk. So far I have installed a ubuntu server 12.04 LTS on my system. Now I wanted to add another disk for data storage which will spindown whenever not needed.This disk is formatted in ext3 and should be mounted under /WDGreen (as it's a WDGreen).

I have done the following entre in /etc/fstab and rebooted the system:
/dev/sdb1 /WDGreen ext3 default 0 0

I then created a file in /WDGreen for testing purpose and set the disk manually to sleep. After accessing the file the disk was still asleep which tell's me that the data disk isn't mounted propperly.

What am I doing wrong?

---

### Post by deadflowr on 2014-01-11
This maybe
[http://serverfault.com/questions/93783/make-a-hard-disk-sleep-and-only-wake-up-when-needed](http://serverfault.com/questions/93783/make-a-hard-disk-sleep-and-only-wake-up-when-needed)

---

### Post by Clemens_Wolff on 2014-01-11
Thanks fpr your reply but I think that's not what I am looking for. On my opinion so far the problem is not the spindown - it's rather that the data disk sdb isn't mounted under /WDGreen as it should be...

When I create a folder under /WDGreen it's saved in the sda device and not in the sdb device...

---

### Post by deadflowr on 2014-01-11
Try switching the entry from the device to the UUID.
run 
```
sudo blkid
```
to get the UUID for sdb1.
From 
```
[COLOR=#000000]/dev/sdb1 /WDGreen ext3 default 0 0[/COLOR]
```
to
```
UUID=long-number-here [COLOR=#000000]/WDGreen ext3 default 0 0[/COLOR] 
```

---

