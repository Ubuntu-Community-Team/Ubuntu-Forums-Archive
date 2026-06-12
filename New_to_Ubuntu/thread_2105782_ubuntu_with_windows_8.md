---
title: "ubuntu with windows 8"
date: 2013-01-17
forum: New to Ubuntu
---

### Post by Lea Wick on 2013-01-17
Hi, I'm completely new to Linux/Ubuntu, and have little experience with computers. I have windows 8 OS preloaded on my PC, and i'd like to try ubuntu but keep win8. Should I choose the 32-bit version or the 64-bit one? And how do I install it/ run it alongside windows? Any help would be appreciated!

---

### Post by prodigy_ on 2013-01-17
You can find the latest HOWTO guide here: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

However, before you try anything, you should be aware that troubleshooting a dual-boot system might be a **very** tricky task for a newcomer. And very frustrating when you're unable to boot at all. (I don't mean you're guaranteed to run into issues but it's not an uncommon scenario.)

So you should at least consider scratching your Windows installation in favor of Ubuntu (you can always reinstall it later) or experimenting with Ubuntu on a separate piece of hardware (say, on some cheap used laptop).

---

### Post by mastablasta on 2013-01-17
if win8 are preloaded chances are you have 4 primary partitions taken. you need to remove one of those or change one into secondary partition (or logical as it is called in win8).
 
you can use 64bit. after download first check the md5sum: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
 
then burn the image to a DVD or put it on a USB drive (at least 2GB) using tools such as unetbootin or linuxliveUSB.
 
then choose to boot from it and select try it to see if it all works. once running you can use boot repair tool or just run this script: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
and then post the result here. this script will read your current setup of computer and create a file you can post here using the code tags (the # sign in the thread reply widnow). this will enable others to help you better on how to continue. your probably have UEFI boot.
 
if something doesn't work open a terminal and copy and paste the output of these two commands:
 
lspci
lsusb
 
these commands will throw out data on your hardware so we can see if a hardware not working is compatible with linxu or if there are any additional drivers that are needed to run it.
 
after we see the current setup we can help you partition/divide the disk propperly.
 
there is also a Wubi tool that installs ubuntu in a virtual drive inside windows. this is easy but it has some issues and also soem limitations: [http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)
 
a better and super safe option to try linux out is to install it inside Windows using Virtual box. it is easy to do it: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
again it has it's own limitations (doesn't work as fast, 3D support is experimental...), but at least it gives yet another option to try out the OS safely (appart from runnning it live) without messing up windows.
 
Edit: if you prefer a more traditional desktop interface you can tryout Kubutnu or Xubuntu.

---

### Post by audiomick on 2013-01-17
I have not attempted a Win8 Dual Boot yet, but it seems there are some particular issues. Here are a few threads dealing with it. Pay attention to the posts from Oldfred. He seems to know a fair bit about it.

[http://ubuntuforums.org/showthread.php?t=2105067&highlight=dual+boot]("http://ubuntuforums.org/showthread.php?t=2105067&highlight=dual+boot")

[http://ubuntuforums.org/showthread.php?t=2098753&highlight=dual+boot]("http://ubuntuforums.org/showthread.php?t=2098753&highlight=dual+boot")

[http://ubuntuforums.org/showthread.php?t=2105628&highlight=dual+boot]("http://ubuntuforums.org/showthread.php?t=2105628&highlight=dual+boot")

[http://ubuntuforums.org/showthread.php?t=2105656&highlight=dual+boot]("http://ubuntuforums.org/showthread.php?t=2105656&highlight=dual+boot")

I can't say for sure that any of them apply to you directly, but they seem to cover the issues that I have been seeing here.

---

### Post by Lea Wick on 2013-01-27
Thanks for the advice...I must admit I am a bit lost. I do want to keep win8, so does anyone know how to make a bootable copy of this operating system? It didn't come with Recovery CDs. (**prodigy_ :** this is in response to you sentence "...when you're unable to boot at all..." !)
**mastablasta**: what exactly is md5sum?! and where can I read up on how to partition drives? what are secondary/logic partitions? what is UEFI boot and how do I know if I have it?
Is there a "Computer Terms" dictionary somewhere online? :-s

---

### Post by prodigy_ on 2013-01-27
You could make a backup image of your Windows 8 partitions (on an external HDD for example). [Acronis](http://www.acronis.com/homecomputing/products/trueimage/) is a great tool for that. It's not free, but comes with a 30-day trial which should be enough for your purposes. Then, should anything go wrong, you could simply restore your system from backup exactly as it was before.

---

### Post by oldfred on 2013-01-27
If you have Windows 8 pre-installed you have UEFI and gpt partitioning. Most of the instructions you find are for the old MBR partitioning.

Use Windows to shrink the Windows NTFS partition to make room for Ubuntu. If you just want the default / (root) & swap you then can just run the auto install into the unallocated space. 

If you want to partition in advance or you can create partitions (similarly) during the install with the Something Else option.
       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

    You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

    Grub does have a bug and you will need Boot-Repair to create valid chain load entries to be able to dual boot Windows.
       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

    
       Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

### Post by andrew.46 on 2013-01-27
Another vote here for the use of VirtualBox. It runs nicely under windows and means you can experiment endlessly with Ubuntu without breaking your system.

---

### Post by tejpatel98 on 2013-01-27
I also have Windows 8 and wanted a Ubuntu partition. I installed the 64 bit operating system using Wubi that can be downloaded off of Ubuntu's website. I have not had any conflicting problems using Windows 8 and Ubuntu. I did opt for the 12.04 LTS version of Ubuntu instead of 12.10.

---

### Post by oldfred on 2013-01-28
@tejpatel98
Wubi will not work with pre-installed Windows as that has gpt partitioning. You must have installed Windows 8 yourself in BIOS/MBR mode?

---

### Post by tejpatel98 on 2013-03-11
Yes, the computer had Windows 7 to begin with but was upgraded to Windows 8, then dual-booted with Ubuntu 12.04 LTS.

---

### Post by squakie on 2013-03-12
a wubi installation isn't true dual boot, and it's normally only used to "try out" ubuntu.  For a true dual boot on a system with Windows 8 pre-installed, do follow oldfred's advice and ask plenty of questions.  I just went through this on a new Dell laptop, and oldfred's help was invaluable.  Do make backups!  If this is a name-brand PC with Windows 8 pre-installed, look for tools from the vendor - this usually includes the ability to back-up (in this, most likely, create an image for resetting to factory default).  Please do this!  These things with uefi, at least in my case, required that I reload an image of the entire disk due to errors I encountered.  Without that type of backup, I would not have been able to boot my PC.

---

### Post by tejpatel98 on 2013-03-12
Sorry if this if off topic, but is there a huge difference of installing and using Ubuntu through Wubi rather than using the CD to install and have a dual-boot that way? I think that my Wubi partition is enough for me, but would like to know the difference as well.

---

### Post by oldfred on 2013-03-13
Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)


If you installed Windows 8 yourself in MBR(msdos) then you can use wubi. If preinstalled you cannot.
Wubi is ok for a longer test than just using liveCD. But with flash drives, you can add persistence or even a full install to a flash drive instead of wubi, if you do not want to modify partitions.

The advantage of wubi is that is is a full install, does not require repartitioning, and is easy to uninstall if you do not like it.

But it is just a large file inside the NTFS partition, relies on the NTFS file structure and the Windows boot loader. If Windows has issues then you cannot boot wubi.

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

   [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

      
 HOW TO Avoid Wubi & Install Ubuntu on USB Drive -
[URL="http://ubuntuforums.org/showthread.php?t=1650699"]http://ubuntuforums.org/showthread.php?t=1650699

      [/URL]
 [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

      
 From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

     
    [URL="http://ubuntuforums.org/showthread.php?t=1650699"]
[/URL]

---

