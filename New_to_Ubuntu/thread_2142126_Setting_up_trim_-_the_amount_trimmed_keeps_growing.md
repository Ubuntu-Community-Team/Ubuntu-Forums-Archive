---
title: "Setting up trim - the amount trimmed keeps growing on consequitive trims!"
date: 2013-05-04
forum: New to Ubuntu
---

### Post by jb0nez on 2013-05-04
I didn't realize that 12.10 or 13.04 doesn't automatically trim the SSD. So I followed the guides out there, made a cron job to do it, but here's the weird thing - I can run it over and over by hand and keep getting stuff trim'd! Watch:

```
justin@justin-FX6831:/etc/cron.daily$ more trim#!/bin/sh
LOG=/var/log/trim.log
echo "*** $(date -R) ***" >> $LOG
fstrim -v / >> $LOG

```

```
justin@justin-FX6831:/etc/cron.daily$ sudo ./trim
[sudo] password for justin: 
justin@justin-FX6831:/etc/cron.daily$ more /var/log/trim.log
*** Sat, 04 May 2013 10:07:39 -1000 ***
/: 873803776 bytes were trimmed
*** Sat, 04 May 2013 10:09:09 -1000 ***
/: 143777792 bytes were trimmed
*** Sat, 04 May 2013 10:16:22 -1000 ***
/: 272334848 bytes were trimmed
justin@justin-FX6831:/etc/cron.daily$ 

```

It's trimming more and more each run. Is that expected behavior?

One confounding variable might be my odd fstab setup, which mount some hard drive partitions into / so they might get hit - but I'd think the hard drive controller would just ignore trim commands. Am I inadvertently blowing away actual data somewhere?

My fstab allows me to boot raring off my SSD, have /home on SSD, but have the big spacehogging directories or ones likely to grow coming from my 2TB hard drive (I was only about to dedicate 15gb of my SSD to linux). I probably would've done it differently if I knew more when I was setting this up but it's too late now and I've put too much work into getting this working (4 reinstalls of 13.04):

 ```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=0b115957-998c-492f-83f0-2f0bc0cdd62a /               ext4    noatime,errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=6de58d89-f303-4f63-8784-76748f960e20 none            swap    sw              0       0
# mount tmp as tmpfs
tmpfs /tmp tmpfs defaults,noatime,mode=1777,nosuid 0 0
# my data HDD
UUID=c165c7b3-f5aa-4379-94c8-9fb25830909e /mnt/linux ext4 noatime,data=writeback,barrier=0,nobh,errors=remount-ro 0 1 
# my bind mounts
/mnt/linux/usr /usr none bind 0 0
/mnt/linux/var /var none bind 0 0
/mnt/linux/opt /opt none bind 0 0

```

And just for good measure, let's TRIM again:

```
justin@justin-FX6831:/etc$ more /var/log/trim.log 
*** Sat, 04 May 2013 10:07:39 -1000 ***
/: 873803776 bytes were trimmed
*** Sat, 04 May 2013 10:09:09 -1000 ***
/: 143777792 bytes were trimmed
*** Sat, 04 May 2013 10:16:22 -1000 ***
/: 272334848 bytes were trimmed
*** Sat, 04 May 2013 10:23:29 -1000 ***
/: 415010816 bytes were trimmed

```

41MB that last time! Can anyone explain what's going on here? Are my bind mounts getting hit with that fstrim / operation? (Going to reboot into windows now and hope it works...)

---

### Post by Paqman on 2013-05-04
A cron job isn't the best way to set up TRIM, the best way to do it is to simply add the option "discard" to those partitions in /etc/fstab.

So assuming your SSD is sda, you should change that line from:
```
UUID=0b115957-998c-492f-83f0-2f0bc0cdd62a /               ext4    noatime,errors=remount-ro 0       1
```
to:
```
UUID=0b115957-998c-492f-83f0-2f0bc0cdd62a /               ext4    noatime,errors=remount-ro,discard 0       1
```

Simple as that.

---

### Post by jb0nez on 2013-05-05
Actually I've done a lot of googling on this and almost everyone recommends doing it with cron - the extra delay everytime you RM a file introduced by the discard option kinda defeats the purpose of discard.  But that's not what I'm asking about here, it's why is the fstrim command consecutively increasing the amount trimmed (even when run by hand)?

---

