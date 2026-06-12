---
title: "Can't access ubuntu partition after windows upgrade"
date: 2017-07-31
forum: New to Ubuntu
---

### Post by chrisnd2 on 2017-07-31
Hi, started experimenting with ubuntu 16.04 a few months ago in its own partition on my main (C:) drive.  At that time, Windows 7 was my principle operating system.  for reasons I won't bother you with, I upgraded this to Windows 7 SP1 with a clean install into the same windows partition as previously.  From that point on however, I have not been given the option to boot into Ubuntu at startup as previously. How can I retrieve my startup/boot options menu, please?

---

### Post by oldfred on 2017-07-31
Generally any major Windows update or install, removes the Linux partition from the partition table.
This bug has been there for years and is still there with Windows 10.

Partition data is still there, if partitions have not otherwise been changed. You just need to restore the entry to the partition table. You need a current version of Ubuntu live installer. You can use testdisk or parted rescue. Some that know start sectors find parted rescue easier.

Post this from terminal in live installer:
 sudo parted /dev/sda unit s print 

 Backup partition table structure to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt 

 Used parted rescue
[https://ubuntuforums.org/showthread.php?t=2362656](https://ubuntuforums.org/showthread.php?t=2362656)
[http://ubuntuforums.org/showthread.php?t=2315405](http://ubuntuforums.org/showthread.php?t=2315405) 

 Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)

---

### Post by chrisnd2 on 2017-08-02
Thank you oldfred for the detailed response.  I have followed many of the links you suggested - but without coming to a final idea on how to proceed other than to put in the installation dvd and see what options it gave me!  

The three screen shots attached show the options - of which wipe the ubuntu partition and reinstall seems the easiest option.  I have no files stored here I wish to retain, so that is not really a problem. It just seems a shame that, with everything already in place, all I am lacking is the startup menu to access it.  So, unless there is a simple way to reinstate this, then I will have to do that?

Chris D

[IMG]http://www.deuchars.org.uk/temp/IMG_20170802_092555.jpg[/IMG]

[IMG]http://www.deuchars.org.uk/temp/IMG_20170802_092653.jpg[/IMG]

[IMG]http://www.deuchars.org.uk/temp/IMG_20170802_092746.jpg[/IMG]

---

### Post by oldfred on 2017-08-02
The links we to load testdisk or parted rescue to recover a missing partition.

If installing again, always best to use Something Else. You can create a new partition in the unallocated space. But I normally prefer to use gparted to create new partitions. You still have to use Something Else and choose (change button) the new / (root) partition and format as ext4.  If you have a separate /home partition you also choose that partition, but must NOT check the format button or it will erase all you data.

Your screen shot seems to show 16.04 in sda5, so you already have an install. If then it is just not booting it may need repairs. But if you have no data to save a new install is a brute force way to repair it.

---

### Post by chrisnd2 on 2017-08-03
Thanks again oldfred. I have fixed my problem now and everything boots as previously.
I  followed your last link and reached  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)  
Using the disc created  from there has returned my system to previous configuration.
Regards,
Chris D

---

