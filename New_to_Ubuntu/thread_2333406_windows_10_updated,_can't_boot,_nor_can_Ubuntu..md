---
title: "windows 10 updated, can't boot, nor can Ubuntu."
date: 2016-08-09
forum: New to Ubuntu
---

### Post by sebastianrs95 on 2016-08-09
Hello, I come from the Boot Repair help post, from the wiki. It said to ask for help here.
I tried using the Boot Repair tool, and I got the BootInfo URL, but not access to my OSs.

here's the URL: [http://paste.ubuntu.com/22872074](http://paste.ubuntu.com/22872074)

Thank you.

---

### Post by yancek on 2016-08-09
Your windows update seems to have rewritten the partition table and not included the Linux partition.  You can see in the output that there are no Linux partitions.  Your fdisk output shows a lot of space between the beginning of sda3 and sda5.  Generally, using testdisk can repair the partition table.  Download from the site below and make sure you read the Step by Step Guide on the page.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by oldfred on 2016-08-09
I have no idea why Boot-Repair thought boot flag should be on sda5, it must be on sda1.
Windows has to boot from a primary partition with its boot files which are in sda1.

You can use gparted or Disks in live installer to move boot flag. Or using your Windows repair/recovery disk it is the make active commands.

Also a few have had issues with testdisk and not restored all the current partitions.
Good idea to back up current table so you can get back to where you are now if you have to start over.
 First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX >parts_ parts.txt
sudo sfdisk -d /dev/sda > parts_sda.txt 

Some have also used parted rescue, but many have used testdisk and had it work. Some could just boot, others had to reinstall grub.

 Used parted rescue
[http://ubuntuforums.org/showthread.php?t=2315405](http://ubuntuforums.org/showthread.php?t=2315405) 
      
 Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)

---

### Post by sebastianrs95 on 2016-08-10
Thank you so much, to both of you. I followed the tutorial, and I was able to recover it, using TestDisk.

---

