---
title: "To partition or not to partition, that is the question"
date: 2016-07-05
forum: New to Ubuntu
---

### Post by jonjon2 on 2016-07-05
Hello all. I hope complete newbie questions are ok. I just have a question about the pros and cons of partitioning my hard drive myself or letting the Ubuntu installation menu handle it for me? Any advice is appreciated, even if the advice is "google it and leave us alone." 

Thanks!

---

### Post by ajgreeny on 2016-07-05
Hello jonjon2 and welcome to the forums.

We do not answer questions here with comments such as "google it and leave us alone."; we are not that type of forum, as I am sure you will find if you continue here once you have installed Ubuntu.

As you are a completely new user of Linux I would suggest that you leave the installer to do its work by default, unless you are wanting to run a dual boot system with Windows or some other OS when you will need to make space for Ubuntu.

Tell us in more detail what hardware you have and what is on it at present, we can then give you better advice about the path to travel in this new adventure.

---

### Post by oldfred on 2016-07-05
I prefer to manually partition in advance as then I have control over sizes and can have more than the default / (root) & swap.

But as ajgreeny says, a new user probably does not even know what a partition is, just Windows "Disks" and is better served by just using the auto install option.

       gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

I also now only use gpt partitioning, even on larger flash drives. But if older BIOS system and dual booting with Windows you have to have Windows on a MBR(msdos) partitioned drive. Windows only boots from a gpt partitioned drive with UEFI. 

       
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by jonjon2 on 2016-07-07
Thanks for the input. @ajgreeny, I actually do plan on doing a dual install of Windows and Ubuntu. Later on I may get rid of Windows (sick of all of those updates that take over an hour to perform), but yeah, want to run both in the beginning until I'm used to Ubuntu. 

As for hardware, I have a AMD APU Micro ATX Gaming PC. The hard drvie is a Seagate 1TB. Do you need to know processor and motherboard too? And no, I'm not this technical, I just looked up my computer model online to find the specs ;-)[[COLOR=#C61919]ajgreeny[/COLOR]]("http://ubuntuforums.org/member.php?u=27747")[COLOR=#000000] [/COLOR][COLOR=#C61919]**ajgreeny**[/COLOR][COLOR=#C61919]**ajgreeny**[/COLOR]

---

### Post by blackeagle2 on 2016-07-07
The Ubuntu installer (from memory because it's been a while lol) will find the Windows installation and give you some options.

1) Erase it and use the whole disk for 'Buntu
2) Keep Windows and install alongside it
3) Something else

If you choose to keep windows, then the size of the windows partition will be reduced and new partitions created for Ubuntu to use.  If your disk is quite full then it may not be possible to reduce the size of the win partition enough in which case you'll have to remove downloads etc to free up space.

Your other option (if you want windows and you have a reasonably powerful CPU) is to use the entire disk for Ubuntu and then install VirtualBox or Virtual Machine Manager, either of which will let you install Windows in a virtual machine.  Advantages are that you can run both OS's at the same time but disadvantages are that your graphics may not be fully supported.

---

### Post by Impavidus on 2016-07-07
> **blackeagle2 said:**
> 
If you choose to keep windows, then the size of the windows partition will be reduced and new partitions created for Ubuntu to use.  If your disk is quite full then it may not be possible to reduce the size of the win partition enough in which case you'll have to remove downloads etc to free up space.


I used the Ubuntu installer just once to shrink the Windows partition. All other occasions I installed Ubuntu was without Windows or over an existing Ubuntu. It worked perfectly. I had previously defragmented the Windows partition. But that one time was using Ubuntu 6.06, dual booting with Windows XP. With later Windows versions it seems less reliable. Better use Windows tools to defrag the Windows partition, then shrink the Windows partition to create unallocated space, then reboot Windows to let it run its disk checks and complete the shrink operation. If your computer uses MBR partitioning (typical for Windows 7 and before), pay attention to the 4 primary partition limit.

---

### Post by ajgreeny on 2016-07-07
Going back to my Windows XP days, I always booted windows in safe mode with virtual memory temporarily disabled, defragged twice, then shrank the WINXP partition, though I can not now remember how I did that; maybe in the installer itself, but it was 11 years ago.

There was no problem when I did this with either OS, both booting from grub simply and easily. UEFI has changed all that now and does add complications to dual boots but added to even more by some mauufacturers who do not use the standards that were supposedly meant to.be used in UEFI setup utilities, eg HP, ASUS and some others, though are always (I think) workarounds to overcome those barriers to dual booting.

---

### Post by mastablasta on 2016-07-07
> **jonjon2 said:**
> 
As for hardware, I have a AMD APU Micro ATX Gaming PC. The hard drvie is a Seagate 1TB. Do you need to know processor and motherboard too? And no, I'm not this technical, I just looked up my computer model online to find the specs ;-)

speccy will generate a nice hardware output in windows.

otherwise if you run msinfo32 then select all & copy that should preety much take the main info. post here and edit out the private parts of info (if any).

edit: re: partition - by default Ubuntu will create partitions /root (like c:\ in windows) and /swap (similar to pagefile in windows). if you think you need more then create more. if you plan on using both OS it is advised to have a separate NTFS formated, data only partition. if you want you can create separate /home partition (home is kind of like MyDocuments/Documents in widnows). again not necessary but some people do it. other than that you do not need extra partitions for deskotop. however since linux is about freedom, feel free to create as many as you want (file system and partition table limits apply).

---

### Post by jonjon2 on 2016-07-08
Wow, thank you all for the detailed responses. Incredibly helpful. You certainly seem to be a great group. :)

---

### Post by RobGoss on 2016-07-08
Hello and welcome to the forum, It you've never partitioned a hard drive it can be a little tricky at first but as you continue doing so it becomes second nature
I might add doing it your self can be rewarding because you will learn how it's done. Ubuntu makes it easy to learn and with this community you won't be lost

If you just want to dual your machines it's pretty straight forward when running the live **USB or DVD, **just choose the try Ubuntu option in order for you to get the feel of what Ubuntu have to offer then, when you're ready click the Install icon on your desktop and begin your installation.

As you proceed with the installation you have the option to install Ubuntu **alongside Windows **this is the option you want because Ubuntu's live session will do all the work for you as far as the partition is concerned 

If you would like to read up of **Dual booting** you can look at the following tutorial it's very handy

**How-To Dualboot Ubuntu & Windows**
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Keep in mind the newer machines made today have the **UEFI / BIOS**, and needs to be handle accordingly and will require you to make changes within your BIO'S settings. This guide with help you with questions you might have getting started. [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

**NOTE:** One very important factor, always **backup** your machines content just in case something goes wrong there have been many cases were users for the first time trying to install Ubuntu or any Linux OS ether deleted one or more partitions in the process.


Best of luck

---

