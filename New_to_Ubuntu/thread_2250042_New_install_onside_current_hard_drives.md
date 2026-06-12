---
title: "New install onside current hard drives"
date: 2014-10-26
forum: New to Ubuntu
---

### Post by cider2 on 2014-10-26
I have 3 Hard drives and 1 SSD. 

Now I would like to remove windows on the SSD and keep my other data intact. 

I am worried that I wont be able to access it once I have installed Ubuntu. Must I set any permissions now within Windows 8.1 before going ahead with this. 

Apologies for the noob question but I would rather ask.

---

### Post by yancek on 2014-10-26
You have the windows 8 installed on the SSD, the operating system and the other two drives just contain data with ntfs filesystems, is that correct?
Ubuntu should be able to read/write ntfs permissions and you can't set permissions from windows that will work on a Linux system.  Windows doesn't even recognize Linux filesystems much less allow you to read or write to them.  If you plan to replace windows 8 with Ubuntu and keep your windows filesystems on the other drives you should not have problems.  You don't indicate whether you have any other operating systems which would make a difference.

---

### Post by cider2 on 2014-10-26
Correct - all other HDDs are NTFS. I have no other OS so If i replace with Ubuntu , am I correct in saying that ubuntu will read NTFS and there wont be any issues with that?

---

### Post by oldfred on 2014-10-26
With Multiple drives you do need to use the more advanced  Something Else install. That lets you choose your partitions but also choose which drive has the grub2 boot loader. Normally all auto installs, install the boot loader to the drive seen as sda.

Best to make a full backup of Windows. Many users erase Windows and then find one application or game that only runs in Windows and cannot live without it and need Windows back.

Ubuntu will read & write all NTFS partitions without issue as long as you have not left them hibernated. But if NTFS you cannot run chkdsk from Linux and need a way to run that occasionally or after any corruption due to power failure or other causes. 
Best then to have a Windows repairCD or flash drive to run chkdsk. Or plan an backing up all data, reformatting to ext4 and restore data.

Is this a newer UEFI system or BIOS based system?

gpt partitioning is required for UEFI boot, but Ubuntu will boot in BIOS mode from a gpt drive.
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

      
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

---

