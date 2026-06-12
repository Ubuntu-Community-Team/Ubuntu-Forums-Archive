---
title: "/dev/sda not able to detect"
date: 2013-05-04
forum: New to Ubuntu
---

### Post by sazan on 2013-05-04
Hi
I have a general problem.
I was re-installing Windows in my partition and my desktop restarted during the format session of the disk, now i am unable to see my hard disk and its partition again. 

So, i got into bootable ubuntu and trying to format the disk, though i am getting nothing here too. 

Here is my fdisk result. Need to get a new NTFS filesystem on this disk again, though i hope the other partitions have their data secured. 

ubuntu@ubuntu:~$ sudo fdisk /dev/sda 

Unable to read /dev/sda

---

### Post by deadflowr on 2013-05-04
Do you have anything like gparted installed?

I know gparted has a check function which will check for errors on the disk, and it'll run windows filesystems.

---

### Post by sazan on 2013-05-04
I have gparted in this bootable DVD, i had run gparted, but using this doesn't detect my disk.

---

### Post by chipbuster on 2013-05-04
Do you need the data on that disk? If the disk isn't physically broken, you might be able to get something going by dd'ing the disk. It will destroy anything left on that disk though.

---

### Post by sazan on 2013-05-04
It is ok if I loose the data in this disk. Though I would stil want the partitions except for the primary ones to be ok and data secured as far possible.

---

### Post by sazan on 2013-05-04
this is my gparted msg

> ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 1.8.8.1.159-1e0e
======================
Input/output error during read on /dev/sda



Though the disk is detected in BIOS

---

### Post by fantab on 2013-05-04
Which partition were you formatting when the mishap happened? was it the Windows partition? First partition, /dev/sda1?
Can you find other partitions on the HDD when you boot with Ubuntu LiveDVD/USB? Can you mount them? Can you read the data on 'em?
Does you computer boot with UEFI? What Windows version do you use?

---

### Post by sazan on 2013-05-04
I was formatting the primary windows partition since my windows crashed. It was /dev/sda1.
I am unable to find other partitions now on HDD, maybe because the partition table is lost, so I can't mount them too.  
The windows I use is Windows XP SP2

---

### Post by fantab on 2013-05-04
If the Partition Table is lost then probably you won't have any other partitions.... check and re-confirm from Ubuntu LiveDVD/USB if you have other partitions or you lost 'em. If you have 'em then Make a BACKUP asap of all your important files/folders.

Then boot Windows installer and see if it detects the c: partition or /dev/sda1. Let us know if it doesn't. try again.
Can you also post the screenshot of your partitions from Gparted?

There are tools to recover the lost partitions but I am not sure if you can recover lost partitions without 'Partition Table'. If there was any important DATA that you want to recover then give [TESTDISK]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step") a try.

More info:
[http://ubuntuforums.org/showthread.php?t=2136126&p=12606265#post12606265](http://ubuntuforums.org/showthread.php?t=2136126&p=12606265#post12606265) (read the post by Mark Phelps)
[http://geekyprojects.com/storage/how-to-repair-a-damaged-partition-table-or-mbr/](http://geekyprojects.com/storage/how-to-repair-a-damaged-partition-table-or-mbr/)
[http://datarecoverymethods.blogspot.com/2011/01/recovery-of-lost-windows-partition.html](http://datarecoverymethods.blogspot.com/2011/01/recovery-of-lost-windows-partition.html)

If loosing DATA is not an issue then use Gparted to create a new partition table and start over.

Good Luck...

---

### Post by sazan on 2013-05-04
Hi
Thanks for your reply

I had run gparted and it is not showing any disks available, also there is no partitions being displayed in fdisk. 

I am currently confused if my HDD is ok and running fine and I am unable to use SMART on them.

---

### Post by sazan on 2013-05-04
I have run the dd command to erase all data to start fresh.

---

### Post by prodigy_ on 2013-05-04
> **sazan said:**
> Input/output error during read on /dev/sda
I/O error might indicate a hardware issue. You should start with ```
sudo smartctl -a /dev/sda
``` If SMART readings are OK, check the manufacturer website for HDD utilities. They should have some diagnostics software you can run from a bootable CD.

---

### Post by fantab on 2013-05-04
SMART will not run without partition table, I think. It should be alright. You just damaged the partition table. It may be difficult to restore it but you can easily create a new one.

Without partition table there will be I/O error, I am not sure though.

---

### Post by prodigy_ on 2013-05-04
> **fantab said:**
> SMART will not run without partition table, I think.
SMART has nothing to do with partitions whether they exist or not. It's HDD internal self-test and it generates a report for the entire physical device.

Also you don't need partition table to check I/O or scan for bad blocks because you can read/write directly from/to block device (e.g. with **dd**).

---

### Post by fantab on 2013-05-04
> **prodigy_ said:**
> SMART has nothing to do with partitions whether they exist or not. It's HDD internal self-test and it generates a report for the entire physical device.

Also you don't need partition table to check I/O or scan for bad blocks because you can read/write directly from/to block device (e.g. with **dd**).

Thanks for the clarification.. I wasn't sure.

---

