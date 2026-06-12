---
title: "Formatting a laptop hard drive"
date: 2012-02-04
forum: New to Ubuntu
---

### Post by gfalcon on 2012-02-04
Hello, everyone.

I have a laptop whose hard drive seems to be  corrupted. The machine will not boot up unless I boot an OS from dvd. I  cannot install Ubuntu to the hard drive because the attempts fail due to  a disk error. 

I would like to re-format the entire disk in  hopes of being able to install Ubuntu to the hard drive. I've found  articles and videos that cover this topic, but they require that my hard  drive already have partitions (when I try to list devices and  partitions I only get info on the dvd player ) or that I have access to  the root user (which I have been unable to reach).

I will be glad for any help offered.

---

### Post by dagroves on 2012-02-04
> **gfalcon said:**
> Hello, everyone.

I have a laptop whose hard drive seems to be  corrupted. The machine will not boot up unless I boot an OS from dvd. I  cannot install Ubuntu to the hard drive because the attempts fail due to  a disk error. 

I would like to re-format the entire disk in  hopes of being able to install Ubuntu to the hard drive. I've found  articles and videos that cover this topic, but they require that my hard  drive already have partitions (when I try to list devices and  partitions I only get info on the dvd player ) or that I have access to  the root user (which I have been unable to reach).

I will be glad for any help offered.

Try to boot up to the desktop on a Live CD then run GParted, then select your hard drive and format it. I hope it works.

---

### Post by JRV on 2012-02-04
It sounds like the partition table is corrupted.
Boot from a live CD as suggested above and run gparted.
Click on Device and create a new partition table.
(This will wipe the drive, be sure this is what you want.)
Then re-try the install.
You should be able to re-partition within the installer.
Or just use the guided partitioning.

---

### Post by Bartender on 2012-02-04
If you boot from a LiveCD, then go into GParted, you might want to format the disk as primary ext4 instead of just wiping it clean.

Once it's one big primary ext4 partition, your Ubuntu installer CD oughta work fine for a standard automatic install if that's what you want.  If it can't, then the HDD may have problems.  Or it may not.  Your install CD could be bad, loose wire inside, power supply failing, RAM stick starting to fail, etc.

---

