---
title: "check trim on SSD   13.04"
date: 2013-06-30
forum: New to Ubuntu
---

### Post by ub9876 on 2013-06-30
Is there an easy way to see if trim is on for a new SSD.?? Something not to complicated to see if its on and how to turn it on...
like a ready to go script...

---

### Post by pqwoerituytrueiwoq on 2013-06-30
You can run trim manually with [FONT=courier new]sudo fstrim /[/FONT]
your sata controller needs to be in AHCI mode for trim to work
To enable auto trim you use the discard option on the partition located on the ssd
```
~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=d842f936-1037-4cd8-96b1-b43e104b4bb0 /               ext4    noatime,**discard**,errors=remount-ro 0       1
# /home was on /dev/sdb2 during installation
UUID=b8362e2b-2cdb-40f4-a2a8-a9ed1207cb81 /home           ext4    defaults        0       2
# /mnt/iso was on /dev/sdb5 during installation
#UUID=156f2dd4-0bfe-414c-95a8-080973d9bedc /mnt/iso        ext4    defaults        0       2
# /mnt/virtual_box was on /dev/sdb4 during installation
#UUID=03cc0da7-dc02-4f82-832a-805f8c2e6c4d /mnt/virtual_box ext4    defaults        0       2
# /var was on /dev/sdb1 during installation
UUID=3d1dd4e3-d423-4802-b52a-aa74d6fdc8bd /var            ext4    defaults        0       2
# /var/cache/apt/archives was on /dev/sdb3 during installation
#UUID=39fbf8c6-5d6f-49b2-8433-c06f58278d36 /var/cache/apt/archives ext4    defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=edcffc51-e736-474e-b338-18182e372f87 none            swap    sw              0       0
# /tmp was moved to RAM after installation
tmpfs                                     /tmp            tmpfs   defaults,noatime,mode=1777 0       0
# /root was moved to /home/root after installation
/home/root                                /root           bind    defaults,bind   0       0
# /media was moved to RAM after installation
tmpfs                                     /media          tmpfs   defaults,size=1M,mode=755 0       0
```

SSD Guide:
[https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Automatic-TRIM:-by-rc.local-by-cron-or-by-discard](https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Automatic-TRIM:-by-rc.local-by-cron-or-by-discard)

---

### Post by oldfred on 2013-06-30
HOWTO: Check If TRIM On Ext4 Is Enabled And Working On Ubuntu And Other Distributions
[http://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking](http://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking)

There seem to be two ways to enable trim. Not sure if one is really better or not.
One is using discard in fstab and the other uses a cron task and fstrim.

      
 Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)
test if trim working using hdparm
[http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2](http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2)

---

### Post by ub9876 on 2013-06-30
I did the manual and it came back ok..that the machine did it and there was a number that it said it trimmed. This verifies
that my bios has ahci enabled no???My Phoenix BIOS does not show any option for enabling ahci...
but otherwise I would not have gotten a comeback on the manual trim..??
am I right??

---

### Post by oldfred on 2013-06-30
Is this a new UEFI system? They may not have AHCI settings.

If you did the fstrim command and it trimmed something then I think it  is not working, but it may depend on how you have it configured.

I did not turn on discard right away on my system, so when I ran the fstrim it did catch up on what was not trimmed as part of the discard command. Some users now seem to think fstrim is  a better way?

---

### Post by pqwoerituytrueiwoq on 2013-06-30
if it is uefi it most likely defaults to ahci
motherboard model
```
sudo hwinfo --bios | grep -i product -B2
```

---

### Post by ub9876 on 2013-07-01
Its a 7 year old Toshiba..

If you did the fstrim command and it trimmed something then I think it is not working, but it may depend on how you have it configured.

how does that make sense??????????????????????????

it did something......... someone find out what is the real story with this and post it to Ubuntu..

---

### Post by oldfred on 2013-07-01
If the fstrim command then trimmed something whatever auto settings you have are not working. I thought you wanted to check to see if it was working.
Yes the fstrim should have worked. But you can check that by looking at the details. Some write 00 and other ff but if random data then not trimmed.

If system is that old it probably does not have AHCI.

---

