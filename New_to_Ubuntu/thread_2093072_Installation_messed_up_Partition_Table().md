---
title: "Installation messed up Partition Table(?)"
date: 2012-12-09
forum: New to Ubuntu
---

### Post by illfated on 2012-12-09
Hey,
this is my first time Installing Ubuntu 12.10. I have a SSD where windows is on and a larger data disk which was only 20% occupied.
So I thought I'd just grab some gigabyte off that disk, make a new partition and install ubuntu on it.

Somehow it got all mixed up in the Ubuntu Installation process so it created a 500gb ext4 partition (which i wanted) but put the rest of the disk (where my data was) into an Unallocated state, even though I clicked not to format the disk, I guess Ive overlooked something.

However as I did not click format, is there a way to restore my partition table for the NTFS partition? I tried Paragon Partition something and it just found the ext4 partition. Im currently running TestDisk 6.13 on INTEL/PC options, which is at 31% and also just found the Linux ext4 partition.

Will testdisk eventually find it when its at 100%? What can I do if it didn't find anything?

---

### Post by debodas on 2012-12-09
So, just to clarify.
Your windows os was on the SSD. Your windows files were on the HDD, using about 20% of the total space. You wanted to take 500gbs of the HDD space, make it into a separate partition, and install Ubuntu onto it?

However, you deleted your existing partition on the HDD?

If so, boot into windows (as your OS was on the SSD you will be able to), and download and install the free trial from [http://www.partition-recovery.com/](http://www.partition-recovery.com/). This should be able to recover your deleted partition.

---

### Post by illfated on 2012-12-10
> **kingnick42 said:**
> So, just to clarify.
Your windows os was on the SSD. Your windows files were on the HDD, using about 20% of the total space. You wanted to take 500gbs of the HDD space, make it into a separate partition, and install Ubuntu onto it?

However, you deleted your existing partition on the HDD?

If so, boot into windows (as your OS was on the SSD you will be able to), and download and install the free trial from [http://www.partition-recovery.com/](http://www.partition-recovery.com/). This should be able to recover your deleted partition.

Thanks for the tip, however Partition Recovery paused on 44%, i could still access the program and do stuff but it just wouldnt continue scanning.
TestDisk finished but only found the ext4 partition.

I'm currently scanning with DiskInternals Partition Recovery 4.2, it'll probably take 8-9 hours. Even if it doesn't interest anyone, I'll edit this post when it's done with the results.

If anyone else has any recommendations on how to fix the partition table after ubuntu(me) broke it during the installation process, I'm open for tips :D

---

### Post by debodas on 2012-12-10
Before you worry about repartitioning you HDD I'd make sure to recover your files first.

I'm going to assume the program asks you where to restore your files. If it does, attach another HDD and restore the files to that HDD, not the one that you're scanning.

Reason - restoring them to the original HDD (the one that you're scanning) has a much lower chance of successfully recovering your data than restoring to another HDD does. :)

---

### Post by illfated on 2012-12-10
> **kingnick42 said:**
> Before you worry about repartitioning you HDD I'd make sure to recover your files first.

I'm going to assume the program asks you where to restore your files. If it does, attach another HDD and restore the files to that HDD, not the one that you're scanning.

Reason - restoring them to the original HDD (the one that you're scanning) has a much lower chance of successfully recovering your data than restoring to another HDD does. :)

Thanks for the tip, however it didn't even come to that.
DiskInternals found the deleted partition with all its files and filenames and even partitionName, however about 80% of them had 0bytes and even the ones with a appropriate filesize were corrupted (jpg, mkv, avi). At least I could rescue some txt files with information. I havent written anything to the disk after ubuntu re-partitioned it, so I guess ubuntu did maybe quick format it or something like that. Anyway, lost is lost. Thanks for the nice help Kingnick42 :)

---

### Post by debodas on 2012-12-11
No need to give your data up as lost just yet.

Try [http://www.easeus.com/datarecoverywizard/recover-lost-partition.htm](http://www.easeus.com/datarecoverywizard/recover-lost-partition.htm) this program. Once again, install it on your SSD.

Finally, as a last gasp measure, you could try [http://www.piriform.com/recuva](http://www.piriform.com/recuva) this. It will not recover a deleted partition, and will most likely not find anything, but its free, so you might as well try.

If neither of these two find anything, your data is gone unless you pay $$$$$$ for a profesinal to recover it. And we are talking a lot of $$$$$$, at least a.

---

