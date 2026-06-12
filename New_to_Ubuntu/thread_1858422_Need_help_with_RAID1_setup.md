---
title: "Need help with RAID1 setup"
date: 2011-10-12
forum: New to Ubuntu
---

### Post by dementech on 2011-10-12
Hello,
I've been having a very difficult time setting up 2-2TB drives as a RAID1 array with Ubuntu 10.10.

I'm using a separate 320GB drive as the boot drive.
I tried letting the iso install cd auto partition the 320gigger, and used the manual option for the 2-2TB drives, creating a partition on both, using all the 2TB on both, and setting them to physical raid volume.

The install seemed to proceed ok, indicating that the partitions were being formatted etc, but when i popped out the install cd and hit continue to reboot, there were 2 fatal errors displayed.  The boot drive loaded, but the raid1 array (md0) was not present.

I then tried to create the array using mdadm but had issues there also; you see, over the last week or so, the 2-2TB drives have been partitioned a number of times, and I don't think they are completely clean right now. I started sudo dd if=/dev/zero of=/dev/sdb yesterday at about 2PM; TOP tells me dd is still running now @ 9AM - 19 hours later.

I'm not using a RAID card, just a foxconn G41MXE mobo with 4 onboard sata ports; the cpu is an Intel E3400 Socket LGA775 Dual-core @ 2.6 GHz, 2GB RAM, and the 64 bit 10.10 server iso.

I would really appreciate any GOOD suggestions to my issues, and some clearly defined steps for setting up raid1 with mdadm; for example:
Should the drives be formatted before creating the array or only partitioned?

With 2TB drives, is it best to use fdisk or parted?

Does Ubuntu have problems with GPT partitons, or seeing drives over a specific size?

Thanks in advance for helping.

---

### Post by acrazyplayer on 2011-10-12
The drives should have nothing on them as far as I know. Use "Disk Utility" in the System -> Administration menu and then "format drive", when it  pops up a window with the option "Scheme" choose the "don't partition"

do this for both drives. 

then in the menu on "disk utility" chose "file -> create -> raid array" you should know what to do from there. Good luck

---

### Post by carverj on 2011-10-13
Additionally, looks like there is a command line utility at: -
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

---

