---
title: "impossible to recognize partitions in HD"
date: 2013-05-05
forum: New to Ubuntu
---

### Post by noblex on 2013-05-05
hi all, i have the following problem with all linux distributions i tryed, ubuntu or debian is the same, the problem presented itself now but time ago i alredy installed linux distros on my pc successfully.

the problem is that gparted (or linux installer) sees only a big empty and not-formatted space in my hd, and doesn't see windows and storage partition.

my disk has 3 partition: an ntfs partition with windows, another ntfs for storage and a raw partition unformatted in which i have to install linux..

gparted is like this

 [IMG]http://s22.postimg.org/a0xo9vswx/920551_10200585199167282_356424749_o.jpg[/IMG]


the funny thing is that via the live i can go throught my partitions and open files in these... only when i try to install the problem shows itself

also, after install an updated version of gparted, i receive this warning that might be related

[IMG]http://s23.postimg.org/pga0yutkb/913661_10200585965186432_1728343179_o.jpg[/IMG]

---

### Post by oldfred on 2013-05-05
It looks like drive was originally partitioned with the newer gpt partitioning. But you installed Windows in BIOS mode which has to use MBR(msdos) partitioning. 
But Windows only removes the primary gpt partition table and leaves the backup partition table. Then Linux tools get confused if drive is really MBR or gpt.

       Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325)

---

### Post by noblex on 2013-05-05
> **oldfred said:**
> It looks like drive was originally partitioned with the newer gpt partitioning. But you installed Windows in BIOS mode which has to use MBR(msdos) partitioning. 
But Windows only removes the primary gpt partition table and leaves the backup partition table. Then Linux tools get confused if drive is really MBR or gpt.

       Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325)

thanks for the answer! i0m trying to use that program but i can't understand how make it work... i typed the commands in the tutorial page but i think i made a mistake because nothing happen
i also think i have not istalled it well

---

### Post by oldfred on 2013-05-05
I missed copying this direct link to fixparts. And it is a good idea to back up partition table just in case.

 [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by noblex on 2013-05-07
> **oldfred said:**
> I missed copying this direct link to fixparts. And it is a good idea to back up partition table just in case.

 [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt
it worked! thanks!

---

