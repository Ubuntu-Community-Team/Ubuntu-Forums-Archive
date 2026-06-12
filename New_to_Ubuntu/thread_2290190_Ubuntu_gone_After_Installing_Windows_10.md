---
title: "Ubuntu gone After Installing Windows 10"
date: 2015-08-10
forum: New to Ubuntu
---

### Post by gregorio4 on 2015-08-10
Hi guys my ubuntu installation gone, after installing Windows 10.  His space is now marked as free space.
[http://paste2.org/4ZKV16PF](http://paste2.org/4ZKV16PF)
boot repair not work.
Please say to me that i can recover it :(
[http://paste2.org/t2pwXLxg](http://paste2.org/t2pwXLxg)

---

### Post by grahammechanical on 2015-08-10
Boot Repair is very good at what it does. It repairs boot problems. It does not repair OS loading problems. It does not recover data. You need another application for that.


[URL="https://www.linux.com/learn/tutorials/809671-get-your-data-back-with-linux-based-data-recovery-tools"]https://www.linux.com/learn/tutorials/809671-get-your-data-back-with-linux-based-data-recovery-tools

[/URL]Regards

---

### Post by yancek on 2015-08-10
If you look at the boot repair output, you can see three windows partitions, an Extended partition and the only thing in that partition is the swap partition.  You've ovewritten the Ubuntu installation when you installed windows.  You might be able to recover some data with the software suggested above or software such as TestDisk.  Best to use it from a Live CD/flash drive as every time you boot the computer you will probably lose more data.

---

### Post by oldfred on 2015-08-10
Windows reinstalls have for years forgotten to write a Linux partition that is logical or inside the extended partition. You can use testdisk or parted rescue to restore the partition.

>  /dev/sda4 [COLOR=#ff0000]        879,114,238[/COLOR]   976,771,071    97,656,834   5 Extended
/dev/sda5 [COLOR=#ff0000]974,821,376[/COLOR] 976,771,071 1,949,696 82 Linux swap / Solaris

Your Linux partition starts one or two sectors after the start of the Extended and ends before the start of the swap partition.

Testdisk uses the old CHS cylinders heads sectors. And it shows all old deleted or changed partitions. So if changed several times you may have a lot of deleted partitions. You must recover just the one logical (L) that does not overlap other existing partitions. And you must include all your existing partitions.
If using testdisk, make a backup of partitions to a text file, so if you need to you can at least restore easily to current version. And with lots of math can add the correct entry into the text file to restore it also.
      
 Backup partition table structure to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

      [http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080)
Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)

---

### Post by gregorio4 on 2015-08-13
Thanks, testdisk worked.

---

