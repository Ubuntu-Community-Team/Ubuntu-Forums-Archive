---
title: "Optimal partitioning on 256 GB SSD for fresh install"
date: 2013-05-05
forum: New to Ubuntu
---

### Post by Galaxy4877 on 2013-05-05
[COLOR=#282828][FONT=helvetica]Greetings![/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] I am getting my very first SSD (256gb M4) that I plan to use as my OS drive for Ubuntu 13.04.  I have heard that minimizing unnecessary writes to an SSD is a good idea and that there are some things like trim that need to be set up after install.[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]My question is more about partitioning. I would like to get the full speed benefits of an SSD while making sure to limit large writes to the drive (some of my uses will need very large writes to /tmp) and so I would like to use a 500gb platter drive for storage and those large temporary writes. And I would like to keep the OS and all apps on the SSD for the performance increase.  Can anyone recommend exactly how to go about this?[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]The system is quad core with 12gigs of ram, so don't think I will need any swap space, but I'm having trouble figuring out my partitioning set up for /boot, /, /home and the sizes those partitions should be for a 256gb drive and I'm not quite sure how to make my /tmp and any other dir's you guys think might be appropriate point to the 500gb drive which will also be the "storage" drive for the machine. Any help would be appreciated.[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] 
Thanks![/FONT][/COLOR]

---

### Post by TenPlus1 on 2013-05-06
I have my SSD drive partitioned so that 20gb is assigned to the '/' partition and the rest to '/home' ...  No swap partition is required since I have 2gb which is plenty for what I use, and also I have added the following line to the end of the /etc/sysctl.conf file:


vm.swappiness = 0


Also I have added the   noatime   and also   discard   tags to the /etc/fstab partitions to speed up ssd access...  A reboot is required for these changes to work...

---

### Post by Galaxy4877 on 2013-05-06
If I am doing large writes to my temp file is it worth it to have my temp folder on a normal disk? I had heard that was a good way to extend the life of an SSD.  Do you move any parts of the /home to a secondary drive?  I heard it was good to do that as well
?

---

### Post by oldfred on 2013-05-06
I am not sure what I would do with a large 256GB SSD?
My SSD is 64GB and I have two / (root) installs. Since I do not use Windows on SSD, I did use the newer gpt partitioning, partially as it is newer and slightly better, but I thought I was going to soon build a new system with UEFI and it would have to be gpt to work with UEFI. Still have not built new system.

Since I only have 4GB of RAM I do not mount any temp files in RAM, but do have almost all data on my rotating hard drives. I like to have an operating system on every drive that is fully bootable without any other drive, but data scattered across drives. Then when one drive fails I can boot another, but it will give errors on not mounting some data partition.

I was doing this before SSD, but I prefer links. Some suggest bind may be better?
 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

      
 With SSD or Flash (trim do not work on flash) drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode for trim to work.
change to noop i/o scheduler
But per this noop may not now be best.
[http://www.phoronix.com/scan.php?page=article&item=linux_iosched_2012&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_iosched_2012&num=1)
noop may not be best scheduler for SSD, deadline may be better
[http://www.velobit.com/storage-performance-blog/bid/126135/Effects-Of-Linux-IO-Scheduler-On-SSD-Performance](http://www.velobit.com/storage-performance-blog/bid/126135/Effects-Of-Linux-IO-Scheduler-On-SSD-Performance)

---

