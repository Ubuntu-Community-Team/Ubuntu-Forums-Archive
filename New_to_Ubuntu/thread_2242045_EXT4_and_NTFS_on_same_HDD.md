---
title: "EXT4 and NTFS on same HDD"
date: 2014-08-30
forum: New to Ubuntu
---

### Post by sscotty on 2014-08-30
I'm a Linux newbie and would like to multi-boot a couple of Windows systems and a Linux system on separate SSDs - with one extra HDD holding an EXT4 partition plus an NTFS partition, just for data use in each case

There has been much advice over the years about formatting an HDD with mixed file systems, but I recently noted these two warnings specifically _against _doing so:-	
[https://help.ubuntu.com/community/LinuxFilesystemsExplained](https://help.ubuntu.com/community/LinuxFilesystemsExplained)		
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Could someone please clarify the situation?  Do the warnings apply when the HDD does not contain operating systems and is only used for reading/writing data?

Great forum. 
Thanks for help.

---

### Post by mcduck on 2014-08-30
The warning is not about havng NTFS and Ext partitions on the same drive, but about trying to use NTFS as your /home (without formatting it into Linux native filesystems such as Ext4). On both pages it's pretty much saying that both the Linux root partition and the /home (if you have it on a separate partition) should be formatted as Linux-native.

There is absolutely no problem in having different filesystems on the same disk. (And it's even fine to use and store your personal files located on NTFS partition, you just can't use it as the /home and need to keep it as  and additional storage partition instead)

edit: Actually the second link seems to give the idea that there would be some issue with having multiple filesystems on the disk. That's nonsense, as is the suggestion that using NTFS as both / and /home would be an option. It's not a question of what filesystem is used and what the other filesystems on the same disk might be, but simply that Linux needs to be able to store additional information like file ownership and permissions on the root partition and in user's home directories, and Windows filesystems like FAT and NTFS are not able to do that... So as long as you make sure any system partitions use Linux filesystem, you are free to do whatever you want with any additional partitions.

---

### Post by mue.de on 2014-08-30
Hello,

I'm not familiar with SSDs but i alwas used a dualboot-system with Windows on an ntfs-Partition and Linux on -at least- one other ext4-Partition (most two partitions of ext4-type one for root ('/') and one for '/home') on the same harddisk without problems

Greetings  mue.de

---

### Post by sbnwl on 2014-08-30
@[**[COLOR=#000000]sscotty[/COLOR]**]("http://ubuntuforums.org/member.php?u=518522")
Just to add some more to what  [**[COLOR=#000000]mcduck[/COLOR]**]("http://ubuntuforums.org/member.php?u=17309") said:

There should be absolutely no problem. Make two separate partitions in your HDD, and format one with NTFS and format the other with EXT4 filesystem. The NTFS partitition will be useful in case you browse the HDD using Windows OS and need extra space to store your data. BUT THE OTHER (EXT4) PARTITION WILL NOT BE READ BY WINDOWS OS! You might be suggested by the Windows OS that it is an empty raw partition with no filesystem, and clicking on it will bring a prompt to format it. DO NOT FORMAT THEN.

However both the NTFS and EXT4 partitions of your HDD will be available for use when you are up in Linux. Linux is able to read both partitions, so it will not make the mistake of tricking you into formatting any of the partitions.

---

### Post by ThatBum on 2014-08-30
I've run a dual boot 7/Ubuntu system for 3 years with no problems (don't have the machine anymore, sadly). There might be some non-filesystem related issues that need addressing when setting it up, such as faffing about with GRUB to get the boot menu how you want it, setting Ubuntu to use local time on the realtime clock so the time isn't all messed up when you change OSs, etc. Also NTFS support in Linux has historically been flaky, especially involving permissions, but I think that's been sorted out now.

---

### Post by newb85 on 2014-08-30
Indeed. There was a day when it was best to have a FAT32 partition for both systems to store shared data, rather than NTFS. That day is past, and Linux support for NTFS is great.

---

### Post by sscotty on 2014-09-01
Many thanks for all replies. They are a great help - just what I wanted.
All your time and interest are greatly appreciated.

---

