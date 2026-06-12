---
title: "Partition hdd"
date: 2020-02-26
forum: New to Ubuntu
---

### Post by smitla on 2020-02-26
Hi

Install Ubuntu 19.10 and all the apps but now i want to make a partition to save my files to.

HP Laptop with 1tb hdd. Want 200gb operating system and the rest a separate drive.

Like in windows drive c is the operating drive and then a partition like d or x.

Please can you help me to do that.

Thx

L Smit

---

### Post by Impavidus on 2020-02-26
See this guide: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Also, keep in mind that Windows confuses the words "drive" and "partition". A drive is the entire physical thing, a partition is part of it. And about 25GB should be enough for the OS and all applications, except if you want to run certain server software or something like that, but that's unlikely on a laptop. And when you save a file, you don't choose the partition where you save it. The partition is implied by the directory where you save it. If you mount a partition at the /home directory (which is very common to do), every file saved in the /home directory (i.e., all user files) will end up on the /home partition.

---

### Post by oldfred on 2020-02-26
You also can create a separate data partition either NTFS or ext4 and use it for your data.
When I had XP, I had both, now only an ext4 data partition. 
But with Windows 8 or 10 you have to make sure fast start up is off, or else hibernation flag is set. Linux NTFS driver will not mount any NTFS partitions that are hibernated.

Most discuss SSD with operating system and HDD with data, but data partition(s) can be on same drive. 
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by mastablasta on 2020-02-27
gparted will make the partitions. you can create partition and give it volume name of your choice or you can separate home and root (which would be kind of similar to separating my documents and windows system folder on two different partitions). the home and root is more convenient. i made a mistake of not making it on one of the installs. :-(

---

