---
title: "Partition table help?"
date: 2012-02-17
forum: New to Ubuntu
---

### Post by discord on 2012-02-17
It seems my partition table is messed up, see the disk utility screen below. The disk is an external drive that I use with either eSata or USB, if it matters. I thought I already formatted and put something on the /dev/sdc4 extended partition, but disk-utility shows it as unformatted. Also /dev/sdc is showing an impossible amount of free space. I didn't install any windows to the disk, but I do have a windows partition in case I plug it into a windows machine. The SMART tests do not show any errors.

---

### Post by Bucky Ball on 2012-02-17
You're missing the screenshot. ;)

---

### Post by discord on 2012-02-18
> **Bucky Ball said:**
> You're missing the screenshot. ;)

thanks! I attached it but somehow it didn't upload. It's attached now.

---

### Post by oldfred on 2012-02-19
Your unallocated seems a bit large.:)

It may just be a bad entry in the partition table. Best to post this:

sudo fdisk -lu

If last entry end is beyond drive size:

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

Download and run fixparts:
To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) 
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

