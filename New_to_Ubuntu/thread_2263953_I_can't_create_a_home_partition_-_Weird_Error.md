---
title: "I can't create a /home partition - Weird Error"
date: 2015-02-04
forum: New to Ubuntu
---

### Post by GakuWai on 2015-02-04
Hello,  I'm a user between Beginner and Advanced and I'm pretty much good with various distros but lately I have upgraded my Hard Drive to 4TB and today when I tried to install Ubuntu it somehow didn't work. I dunno why :mad:. I have created 25GB '/' (root) partition then when I tried to use the rest of my 4TB unallocated space I simply couldn't because I got that error:  [IMG]http://i.imgur.com/kUaejMn.jpg?1[/IMG]  Tho I have created a 1TB partition and even tho I got error, I clicked on OK and it created the partition but I want to use the whole unalocated space which is around 4TB ?  Any help on this one please ?  Thank You.

---

### Post by yancek on 2015-02-04
You are using mbr BIOS to boot which is indicated in the image you posted.  See the link below which gives a brief explanation Under Problems with MBR, #4:

[https://wiki.archlinux.org/index.php/GUID_Partition_Table](https://wiki.archlinux.org/index.php/GUID_Partition_Table)

Either use GPT partitioning or create multiple partitions of smaller size.

---

### Post by oldfred on 2015-02-04
Even multiple partitions will not work, you have to use gpt to fully use drives over 2TiB.
       MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

With gpt Windows only boots with UEFI, but Ubuntu can boot with UEFI if you have an efi partition at beginning of drive or a bios_grub partition on drive for BIOS boot. If there is any chance drive may be used with a newer UEFI system in the future I would include both efi & bios_grub partition at beginning of drive now. Difficult to add later when drive has lots of data. And they are not large relative to size of drive.

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
[http://askubuntu.com/questions/461394/how-to-partition-ssdhdd](http://askubuntu.com/questions/461394/how-to-partition-ssdhdd)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

---

