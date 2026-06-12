---
title: "Problems w/ Grub and Dual Booting"
date: 2015-12-02
forum: New to Ubuntu
---

### Post by Lazaro_Yero on 2015-12-02
Hi. Recently I've decided to try dual booting with Ubuntu and Windows 10, with Windows 10 being the main OS. I partitioned off ~65 GB of memory for Ubuntu and used a bootable USB drive to install the OS. During installation, I split the partitioned memory into 3 segments. The first segment was the primary "Ext4 journaling file system" with the mounting point at "/" (around 60GB). The second segment was the "swap area" (4 GB). The third segment was something along the lines of "Booting segment", not exactly sure what the name was, but it was recommended by the installer that I make it 1GB in size. 

Anyway, I installed it and everything seemed like it was going fine, until I rebooted my computer. Windows 10 proceeded to boot itself automatically and bypassed Grub. According to the internet, apparently Windows 10 upgrade gets rid of Grub. So I looked up at solution. I found a command which activated Grub for my system:

"bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi" (command for cmd on Windows). 

This command works, but the problem now is that neither Windows 10 nor Ubuntu are appearing on the Grub menu. Clearly I made a mistake and (probably) don't have the correct boot files for my OSs to appear on Grub, but I have no idea how to work with Grub. Can someone please help me?

Side note: I can access the Linux terminal using the "try me" version of Ubuntu. Therefore I can gain access to the sudo command on Linux.


EDIT: [Solved] Both the operating systems needed to be UEFI, the installer essentially took care of the rest afterwards. I appreciate your help, thank you Yancek!

---

### Post by yancek on 2015-12-02
Was windows pre-installed on the computer?
Did you install it yourself?  If so, is it using the default UEFI?  Did you install Ubuntu UEFI?  Both systems need to be UEFI or they both need to be MBR.
This is explained at the Ubuntu site at the link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

To get help, you will need to post more detailed information which you can get by running boot repair.  See the site below for the options to use on your installation medium or to download as a bootable iso file and burn to a CD.  Either way, select the option to Create Bootinfo Summary rather than trying to repair.  There are a number of member here with detailed knowledge who should be able to help.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Lazaro_Yero on 2015-12-02
Windows 7 came pre-installed on the computer, but I recently upgraded to Windows 10 via promotion. 

In the disk management, it says that Windows 10 is running on EFI. I didn't install Ubuntu using UEFI, so I'll fix that soon. I'll edit this post when I get the information from the Boot-Repair tool.

---

