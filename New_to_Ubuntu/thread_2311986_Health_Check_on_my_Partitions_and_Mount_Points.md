---
title: "Health Check on my Partitions and Mount Points"
date: 2016-01-31
forum: New to Ubuntu
---

### Post by stevemid on 2016-01-31
I recently installed 14.4 alongside Windows 10 on a new PC. I accepted the standard installation options and everything was fine: Ubuntu ended up on my SSD along with my home directory which I subsequently realized I wanted on the 2T HD.  I followed the instructions here [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) to move it, however the command to delete the "old home" location returned an error such as "denied access to /medion" which I took to mean that the whole command failed. Rechecking with GParted seems to indicate that the command DID work and that I have now have only one /home directory.

Two questions:  Could someone please take a look at my GParted screen shots to confirm that all is well?  [ATTACH=CONFIG]267056[/ATTACH][ATTACH=CONFIG]267057[/ATTACH]

Second question: For my new /home, I formatted the partition on the 2T HD as ext3 having read that Windows could access ext3 but not ext4 file systems and I didn't see any other major downsides to ext3.    However Windows sees this as a RAW partition. Is there a "best way" to fix this?  I don't intend to use Windows at all unless for some emergency or if I have to to use it to serve up files (pictures and music) which live on ext3 partition to my Tivo and my Apple TV.

Thanks very much for your help.

Medion Configuration
Core™ i5-6400 processor
Windows 10 Home
Intel® HD graphics 530
128 GB SSD
2 TB (2000 GB) hard drive
8 GB DDR4 RAM 
802.11 n- with Bluetooth
Multi-standard DVD/CD burner with DVD-RAM and dual-layer support

---

### Post by Geoffrey_Arndt on 2016-01-31
Looks like the operation went through and your /home is now on the large hdd.    Have you tried to save any data to it yet (to confirm no permissions issues)?   You can enable various column views in nautilus file manager, which also shows owner, group, etc.

Re Windows and ext3 . . . don't know where you read that.    From what I've been told/read, Windows can't read any Linux file system  . . . so you probably would have been better off to format home as ext4.    Linux on the other hand, will read and write to FAT32 & NTFS on the same machine, and to networked PC's if running Samba.

---

### Post by kevdog on 2016-01-31
I've used this driver in Windows to read ext3 formatted partitions (it does ext3 and ext4) although I did it a while ago when I was running WinXP - [http://www.ext2fsd.com/](http://www.ext2fsd.com/).  It worked ok although from what I remember I was using cygwin as well.  I'm not sure if it works on Win 10 although the page would suggest a work-around.  Honestly however when I was using Windows, I usually installed cygwin and would mount the drive using sshfs.  I tried using Samba which should work -- however I always found it unreliable.  Sometimes it would work, and other it would but would then hang.  sshfs always seemed pretty reliable in my opinion.

---

### Post by oldfred on 2016-02-01
Best not to write into any system partition, either from Windows into Linux nor Linux into Windows.
Better to have separate data partition(s). 

I install several Ubuntu versions, so currently have a /mnt/data partition with the folders you normally see in /home, then link those folders back into /home. So data is really on hard drive, but /home is still in / (root) on SSD or on HDD depending on which install I boot.

When I still had XP I also had a shared NTFS data partition for Firefox, Thunderbird profiles & photos for Picasa. I had apps installed in both but data in shared partition.

       The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[URL="http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata"]http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata

[/URL]
 [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

[URL="http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata"]
[/URL]

---

