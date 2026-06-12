---
title: "installed ubuntu 14 now i need to put my windows image backup on new hdd"
date: 2016-08-15
forum: New to Ubuntu
---

### Post by atctinak on 2016-08-15
My hdd was crashing, i made a windows image backup on an external drive.
I bought a new hdd and put it in my computer.  It has 8gb ram and a 2TB HDD.  
I booted from an ubuntu flash drive and partitioned my HDD with ubuntu to start it, and a larger partition for my windows stuff
I want to put the windows image back up on the the HDD and be able to run windows from time to time.  I am a quicken user and so my plan is to start windows so that i can run quicken then go back to ubuntu for email and surfing the web

how can i do this and maybe there is a better way to have both operating systems where i can choose which to use

I think I need to restore the windows image backup to the new partition on the new HDD, not sure, very new to ubuntu - please help !

---

### Post by grahammechanical on 2016-08-15
Windows should be installed first. The Windows boot loader does not recognize any other operating system than a Microsoft operating system. If you install Windows now, the Windows boot loader will over-write the Ubuntu boot loader. So, no dual booting that way.

With Windows installed first, we can use Windows tools to defrag the Windows partitions. We do this more than once and we restart each time. Then we use Windows tools to resize the Windows partitions to create unallocated space that the Ubuntu installer can use to put Ubuntu in.

If you install Windows now you will need Boot Repair to re-install the Ubuntu boot loader.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Regards.

---

### Post by yancek on 2016-08-15
If you want to restore a windows system backup, I think you would have better luck going to a windows forum for instructions on how to do that.  Is the new hard drive empty or do you have Ubuntu already installed on it?  Are you planning to install Ubuntu on the same drive?

---

### Post by oldfred on 2016-08-15
I used Quicken since DOS days, and kept XP around just for that. But then finally gave up on all the Windows issues.
I looked at several of the Linux financial tools and now use kmymoney. Its not Quicken and I did try to import data, but that ended up being more work that just starting from scratch.

---

### Post by leunam12 on 2016-08-16
[http://www.howtogeek.com/239312/how-to-restore-system-image-backups-on-windows-7-8-and-10/](http://www.howtogeek.com/239312/how-to-restore-system-image-backups-on-windows-7-8-and-10/)

---

