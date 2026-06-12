---
title: "Dual boot Windows7/Ubuntu14.04 with 2 drives – somethings wrong!"
date: 2014-05-11
forum: New to Ubuntu
---

### Post by nosto53 on 2014-05-11
Patient: 2009 Dell Studio, T9600(2.8GHz, 6MB Cache), 4GB, 128GB SSD, 350GB HDD
OS Windows 7 Ultimate.  Last week, added 14.04LTS.  Went one fine, can dual boot. BUT....
Windows is in the SSD (NTFS), and Ubuntu is in the last part of the HDD (ext4+swap).
  
 The problem was that I wanted to get both OS in the SSD (64GB Win/64GB Ubuntu) and use the HDD as 2 partitions 'Win7 data'(~150GB, shared) and 'Ubuntu data'(~150GB).  The other problem was I went with “alongside” and not “Something else”(one of my lights went out in the brain...).  So.... should I “Delete” Ubuntu and start over with my DVD with manually fparted?  Or is there a better (easily) answer? 
(Toying with fparted since 8.04LTS and forgetting too much stuff...) 
Thanks, RickO

---

### Post by TheFu on 2014-05-12
never heard of fparted, perhaps gparted?  If you move partitions around, the system will not boot, as UUIDs change. You'll need to manually fix that in the /etc/fstab for every partition involved.  Even if the fstab doesn't use UUIDs, the device names are likely to change when moving partitions around.

Plus if the boot partition changes, grub will need to be updated - this isn't really hard, but a good understanding of linux booting is needed.

Based on your bean count, I suspect reinstalling would be easier/better.

---

### Post by oldfred on 2014-05-12
Use Windows 7 to shrink the Windows 7 system partition and reboot so it can run its own chkdsk and make repairs for its new size. But only create partitions with gparted or installer.

You do not need 64GB for Ubuntu. My 64GB SSD has two Ubuntu installs of 28GB and my main working 12.04 uses about 11GB including /home. But I am aggressive in moving all data including some like the hidden profiles for Firefox & Thunderbird to shared data partitions on rotating drive.

I prefer to use gparted to create partitions in advance. With two drives I am never sure where an auto install will go or what sizes it will make partitions.

Before doing anything make sure you have good backups.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://www.dedoimedo.com/images/computers/2009/gparted-create-extended.png](http://www.dedoimedo.com/images/computers/2009/gparted-create-extended.png)

 Install to external drive. Also any second drive.
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)


My SSD is gpt partitioned as it does not have Windows. So partitions look a bit different.

---

### Post by nosto53 on 2014-05-13
Thanks for the info, TheFu and oldfred. And, ok, gparted, not fparted....
 
So, I did not touched the 128GB SSD/Windows7,  
Deleted Ubuntu OS in the 350GB HDD, removed the 350GB, 
installed a little 64GB SLC SSD, used a burned dvd to install Ubuntu and restarted.
  And got “Grub Rescue- Error: no such device, 6a97b7b..........(UUID).

Found a “BootRepair” software (I love free software), booted, got a bunch of answers there, 
restarted, and ….... What, OMG,  it works.......

RickO 0110 0010

---

