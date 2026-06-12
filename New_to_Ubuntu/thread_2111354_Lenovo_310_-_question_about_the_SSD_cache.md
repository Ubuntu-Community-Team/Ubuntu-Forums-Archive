---
title: "Lenovo 310 - question about the SSD cache"
date: 2013-02-01
forum: New to Ubuntu
---

### Post by guppy507 on 2013-02-01
I would like to have both Ubuntu and Windows on my Lenovo U310.  What I'd like is for Ubuntu to be installed on the SSD, and a clean, OEM-partition-free install of Windows on the HDD.  When I tried installing Ubuntu (before first doing a clean install of Windows), it couldn't see the drives or partitions.  

So I did some looking around, and found that I had to turn off the Intel Rapid Start thing, and switch from RAID to AHCI.  So I did those two things, and no luck, still no drives or partitions.  I haven't yet tried the Windows installer to see if it recognizes anything.

Could the OEM partition be messing with it?

What's the best course of action?  The BIOS recognizes both drives individually, so why doesn't Ubuntu?  Also is what I want to do plausible?  Can I run two different OS's on the two different drives?  I imagine I just hit the F12 key and choose which drive I want to boot into, but heck, what do I know?

Thanks!

---

### Post by ronparent on 2013-02-04
There are other issues, but, the primary one is that if you want to 'un-raid' the drives you have to erase the raid meta data on them. Otherwise they continue to be seen as raid. I would wait for advise on how to configure Windows to work without the raid before you do erase the meta data (this is currently unfamiliar territory to me). This wouldn't be necessary if you reinstall Windows after the meta data is erased.

To erase the meta data boot to a live cd, open a terminal and type the command - > sudo dmraid -rE /dev/sdarepeat for sdb

---

### Post by oldfred on 2013-02-04
Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
       
 Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)

       Some info on re-instating  details in post #9
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.   > You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

