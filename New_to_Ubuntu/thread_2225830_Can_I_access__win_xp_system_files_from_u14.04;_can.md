---
title: "Can I access  win xp system files from u14.04; can't boot xp to backup files"
date: 2014-05-23
forum: New to Ubuntu
---

### Post by nu2u904 on 2014-05-23
I am running u14.04 from usb in a dual boot situation. Can't boot win xp since a system file is corrupted. I can get file from another pc. I am using HP z400 work station with intel xeon processor  [ is it 64 bit or 32 bit ?] I am using u14.04 i386 32 bit in meantime.  Can I access win xp system files from u14.04?
Primary HDD is 500GB; slave HDD is 1TB with only few MB used for xp recovery. How can I install u14.04 on drive 2. How can I view partition table from u14.04 usb without taking the install option?
Donald

---

### Post by oldfred on 2014-05-23
It looks like system is fairly new? Other than a few lightweight systems in last 8+ years are 64 bit.
How much RAM and what video card/chip?

From your live installer, in terminal run this:
       [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
uname -a
If i386 or i686 = 32-bit
IF x86_64 = 64-bit
Or:
lscpu
[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

You can see partitions with this:
sudo parted -l

Ubuntu should mount and let you see data in NTFS partitions. But if hibernated or needing chkdsk from a Windows repairCD, then it will not mount the NTFS partition to prevent damage that chkdsk might not be able to fix.

      
 **Windows XP EOL will be April, 2014**.
[http://www.microsoft.com/en-us/windows/endofsupport.aspx](http://www.microsoft.com/en-us/windows/endofsupport.aspx)
Better to move to Linux. 
[https://wiki.ubuntu.com/StartUbuntu](https://wiki.ubuntu.com/StartUbuntu)
Older XP probably need Lubuntu, newer systems may run Xubuntu, or Ubuntu with gnome=-panel, but probably not Unity gui.

---

### Post by nu2u904 on 2014-05-26
> **oldfred said:**
> It looks like system is fairly new? Other than a few lightweight systems in last 8+ years are 64 bit.
How much RAM and what video card/chip?

From your live installer, in terminal run this:
       [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
uname -a
If i386 or i686 = 32-bit
IF x86_64 = 64-bit
Or:
lscpu
[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

You can see partitions with this:
sudo parted -l

Ubuntu should mount and let you see data in NTFS partitions. But if hibernated or needing chkdsk from a Windows repairCD, then it will not mount the NTFS partition to prevent damage that chkdsk might not be able to fix.

Thank you Old Fred. Yes it is 32 bits. I was able to run HP program that allowed backup to either the C drive or the D drive.  Running  u14.04 from usb allowed me to see both drives and to examine file contents. I want to install 14.04 on the TB drive. I started this then ubiquity said install and I hadn't had a chance to create the partitions and mount points. Did this install mean write to the disk or to the next step? I clicked quit at this point.  I have 900 GB unused disk space.  How would you partition the ubuntu partitions and mount points, and in what order?
Would 8GB swap [4GB ram], / 10GB, /home  20 GB be in the ball park and would other partitions be advisable? If I installed other versions of linux would they be on there own set of partitions.?  Ubiquity showed dev sda1 for windows [485 GB] , dev sdc1 for HP recovery folders and my backup folder. I opted to install the boot record on dev sdc1 [1TB] drive.
Thank you, Donald

P.S.  Do you have any suggestions how I can  boot xp and locate the corrupted/missing system file? I don't have the original install disk and attempting to use another install didsk didn't work. 
      
 **Windows XP EOL will be April, 2014**.
[http://www.microsoft.com/en-us/windows/endofsupport.aspx](http://www.microsoft.com/en-us/windows/endofsupport.aspx)
Better to move to Linux. 
[https://wiki.ubuntu.com/StartUbuntu](https://wiki.ubuntu.com/StartUbuntu)
Older XP probably need Lubuntu, newer systems may run Xubuntu, or Ubuntu with gnome=-panel, but probably not Unity gui.
abc

---

### Post by oldfred on 2014-05-26
If you have multiple drives, only use Something Else or manual install.
You can partition in advance which I think is slightly easier, or use the partitioning in the installer.
You then must select to install the grub2 boot loader to the MBR of the drive not a partition boot sector.

I suggest 20 or 25GB or / (root). Only if you hibernate, which is not really recommended would you need swap equal to RAM in GiB or a little more than 4GB. Otherwise 2 or 3GB of swap is all you need with 4GB of RAM. I almost never use swap, but have some.
If only allocating 30GB total for Ubuntu then I might not have a separate /home.
I assume you have several NTFS partitions which you can use for shared data. But best not to write into Windows system partition or c: drive. Set it as read only if you decide to mount it to avoid issues.

Some old info:
 How to fix XP/Vista/7 when the boot files are missing meierfra
[http://ubuntuforums.org/showthread.php?p=5726832#post5726832#4](http://ubuntuforums.org/showthread.php?p=5726832#post5726832#4)
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
[http://ubuntuforums.org/showthread.php?t=1423998](http://ubuntuforums.org/showthread.php?t=1423998)

---

