---
title: "Unknow partition after install"
date: 2013-10-27
forum: New to Ubuntu
---

### Post by ubuntukid on 2013-10-27
I just installed Ubuntu 13.10. I already have Windows 8.1 running on a seperate HD. I installed the bootloader for Ubuntu and Ubuntu on its own drive and use the bios to select which drive I want to boot from. That way I can keep them seperated. The thing is, I've noticed a partition that I don't remember creating on my Ubuntu drive. The strange thing is that when you add up the sizes of all the partitions, they don't add up with the size of the HD. I've posted a screenshot as I don't really know how to explain it. In the file browser i also have a disk called reserved by system. I can't mount it and only get an error, as you can also so in the screenshot. What is this partition?

The partition I'm asking about is the one that is in grey in "Disks".

---

### Post by Impavidus on 2013-10-27
Unfortunately that screenshot isn't very readable. It should give you a partition type or a mountpoint. For the size of the partitions, it could be due to the difference between [GB]("http://en.wikipedia.org/wiki/Gigabyte") and [GiB]("http://en.wikipedia.org/wiki/Gibibyte").

The reserved by system partition belongs to windows. It cannot be mounted because Windows didn't clean up when shutting down. Maybe it's hibernating or you may have fast boot enabled. Anyway, I don't think it would be a good idea to do anything in windows's system reserved partition, as it may well destroy your windows system.

---

### Post by ubuntukid on 2013-10-27
This one should be easier to read. I checked in windows. I was not aware that Windows had two partitions, so that explains the "reserved by system" partition. I still don't understand what this fourth partition is though. Why is it "on top of" another one?

---

### Post by oldfred on 2013-10-27
With MBR(msdos) partitioning you can only have 4 primary partitions. Back in '80s when designed they thought that is all a PC would need. But then they realized more would be useful and let you convert one primary to an extended partition. The extended partition is just a container for many logical partitions. All logical partitions must be in the one extended partition.

 Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)


Technical info
       MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

---

### Post by VMC on 2013-10-27
> **ubuntukid said:**
> This one should be easier to read. I checked in windows. I was not aware that Windows had two partitions, so that explains the "reserved by system" partition. I still don't understand what this fourth partition is though. Why is it "on top of" another one?
I have my Windows on primary partitions, and all my Linux OS's  inside the extended container using logical partitions. 
Here is a visual look at the _**[Extended & Logical partitions]("http://en.wikipedia.org/wiki/Disk_partitioning")**_.

---

