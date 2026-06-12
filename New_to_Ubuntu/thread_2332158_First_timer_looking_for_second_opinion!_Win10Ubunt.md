---
title: "First timer looking for second opinion! Win10/Ubuntu dual boot partition scheme"
date: 2016-07-28
forum: New to Ubuntu
---

### Post by mistamanic on 2016-07-28
Hey everyone, Linux n00b here, hoping to attempt my first dual boot Ubuntu setup alongside Windows, been reading up on the partitioning scheme for 3 days solid now and just wanted to get some second opinions on what i've come up with before taking the plunge!


I had originally planned to install alongside Windows 8.1 but then Windows put the time limit on upgrading to Windows 10, so I upgraded yesterday and quite like it so I think i'd like to keep it. Hopefully this doesn't totally change my plans for Ubuntu.


I'm not sure if upgrading to Windows 10 will have any major effect on how I should set up my partitions, but it may be worth noting that it has added a new recovery partition (Primary 4, 822MB) in addition to the one that was already there from Windows 8.1.


Basically I have a 500GB HD and use a lot of Windows specific programs so i'm hoping to leave Windows plenty of room to breathe, but I also want to give Linux a decent wedge, have a reasonable shared NTFS volume for moving files back and forth between Windows/Ubuntu, and i'd also like to ideally put a chunk aside for experimenting with alternative distros without having to wipe out my Ubuntu installation. 

I'm running an Acer Aspire V5 laptop with Intel Core i3, 6GB RAM and my current Windows partition scheme looks like this:


PRIMARY 1 Windows 8.1 Recovery Partition (300MB)
PRIMARY 2 EFI System Partition (100MB)
PRIMARY 3 C: - Boot, Page File, Crash Dump, Primary Partition (464.44GB) [NTFS]
PRIMARY 4 Windows 10 Recovery Partition (822MB)





And here is what i've come up with for the dual boot:


PRIMARY 1 Windows Recovery Partition (300MB)
PRIMARY 2 EFI System Partition (100MB)
PRIMARY 3 C: - Boot, Page File, Crash Dump, Primary Partition (304.11GB) [NTFS]
EXTNDED (3):
    Logical 1. swap (8GB) [linux-swap]
    Logical 2. /     (50GB) [ext4]
    Logical 3. /home (52GB) [ext4]
        Logical 4. distro2 (20GB) [ext4]
    Logical 5. shared (30GB) [NTFS]
    (TOTAL: 160GB)
PRIMARY 4 Windows 10 Recovery Partition (822MB)




Does this seem like a reasonable structure for what i'm hoping to achieve?


My laptop is UEFI boot but I have downloaded EasyBCD so I can hopefully fix any bootloader issues that might come up, although I must admit I am still a little hazy in this area with regards to any precautions I may need to take around UEFI. I have been switching to Legacy BIOS in order to boot from my live Linux USB, but I'm somewhat confused as to what effect (if any) this will have on the installation process. Any links to further reading on this topic would be welcome!


Thanks in advance for any info or advice, really looking forward to getting involved with the community here :)

---

### Post by mook765 on 2016-07-29
You are in UEFI-mode, so there are no extended or logical partitions, all partitions will be primary.
 You should leave the existing partitions created by your windows installation untouched.
Add Partitions for Ubuntu 
   - for/ 20 to 25 GB should be enough
                                       - for /swap 2 GB should be enough, but if you want it in same size of your RAM, it,s ok
                                        - for /home your 50GB Idea should work
In the remaining unallocated disc space you can create a NTFS-Partition wich you can share for use in both OSes.
Installing in dualboot is a bit tricky, specially when you install in UEFI-mode on a laptop (in your case you have to ), so you should read

[URL="http://ubuntuforums.org/showthread.php?t=2147295"]http://ubuntuforums.org/showthread.php?t=2147295

[/URL]Good luck...

---

### Post by mistamanic on 2016-07-29
Brilliant, thanks very much for the clarification :)

Yes i've just been doing some further reading and realised just how complicated things are with UEFI. I'm going to hold off for now and do a lot more research before I start carving things up, thanks for the warning and the link to the thread, much appreciated!

---

### Post by grahammechanical on 2016-07-29
You should read this. A lot of problems that people have come from not following this guidance.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> **Case when Ubuntu must be installed in UEFI mode**

 Having a PC with UEFI firmware does not mean that you need to install Ubuntu in UEFI mode. What is important is below:  


[LIST]
[*]if  the other systems (Windows Vista/7/8, GNU/Linux...) of your computer  are installed in UEFI mode, then you must install Ubuntu in UEFI mode  too. 
[*]if  the other systems (Windows, GNU/Linux...) of your computer are  installed in Legacy (not-UEFI) mode, then you must install Ubuntu in  Legacy mode too. Eg if your computer is old (<2010), is 32bits, or  was sold with a pre-installed Windows XP. 
[*]if  Ubuntu is the only operating system on your computer, then it does not  matter whether you install Ubuntu in UEFI mode or not. 
[/LIST]
 
> **General principles**

 To install Ubuntu in UEFI mode: 


[LIST]
[*]Use a 64bit disk of Ubuntu. ([Ubuntu32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555").   This is a problem if 32-bit UEFI is the only way your computer can  boot, e.g. if you have a modern Intel Atom based laptop.  In this case,  you will need [a complicated work-around]("https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md").) 
[*]In your firmware, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows 8, also [disable Fast Startup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"). 
[*]You might want to use an [EFI-only image]("https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_an_EFI-only_image") to avoid troubles with mistakenly booting the image and installing Ubuntu in BIOS mode. 
[*]Use  a supported version of Ubuntu. Support for UEFI appeared in 11.10, but  has become more reliable in next versions. Support for UEFI [SecureBoot]("https://help.ubuntu.com/community/SecureBoot") appeared in 12.10 and 12.04.2. 
[*]Set up your firmware (BIOS) to boot the disk in UEFI mode (see the "[Identifying if the computer boots the HDD in UEFI mode]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode")" paragraph below) 
[*]Then:
[LIST]
[*]nothing  special is required if you use the automatic installer of Ubuntu  ("Install Ubuntu alongside others" or "Erase the disk and install  Ubuntu"). Important: if you have a pre-installed Windows and you want to  keep it, do not choose "Erase the disk and install Ubuntu". 
[*]if  you use the manual partitioning ("Something else"), the difference is  that you will have to set the /boot/efi mount point to the UEFI  partition. And if there was not any UEFI partition on your HDD, you  first will have to create it (see the "[Creating an UEFI partition]("https://help.ubuntu.com/community/UEFI#Creating_an_UEFI_partition")" paragraph below). 
[/LIST]
  
[/LIST]



When pre-installed, Windows 8/10 are always installed in EFI mode and that means Ubuntu must also be installed in EFI mode as well. How we load the Ubuntu live session becomes the mode Ubuntu is installed in. If you load the Ubuntu live session in Legacy mode, as you are doing, then Ubuntu will be installed in BIOS/Legacy/CSM mode. You need to load the Ubuntu live session in EFI mode.

With a UEFI boot system we get hard drives that are GPT partitioning. This makes partitioning less complicated because we no longer have the limit of 4 primary partitions that we got with MBR partitioning. So, we do not need the Extended + Logical partitions workaround.

With Windows 8/10 preinstalled there will also be an existing efi_boot partition where the Microsoft efi boot files reside. The Ubuntu installer will put the Ubuntu efi boot files in the same partition and the Windows & Ubuntu efi boot files will happily co-exist.

If we install Ubuntu in BIOS/Legacy mode on a drive with GPT partitioning we will need to create a bios_boot partition. The only non-complicated way to install another OS is the "erase disk and install OS" method. Careful thinking and planning are necessary.

Use Windows tools to defrag Windows and do it more than once and restart each time . Use Windows tools to resize/move Windows partitions. Have a method of restoring/reinstalling Windows .

Regards.

---

### Post by mistamanic on 2016-08-01
Thankyou grahammechanical for pointing me in the right direction! It was only after making my original post that I realised what a massive headache UEFI is likely to be if not done properly, so i've held off on my plans and been reading up on it like crazy for the past few days before going any further.


So, here is the progress I have made so far:




SecureBoot
------------
I have figured out how to turn off SecureBoot while leaving UEFI turned on, which basically involved setting up a supervisor password in my UEFI firmware settings (Acer Aspire V5 171 - Intel Core i3 - insydeh20 setup utility). This unblocked the previously greyed out secure boot settings. My laptop absolutely refuses to boot the live USB unless i either boot in either Legacy Mode (which I now understand is not appropriate for a coherent dual boot with my UEFI Windows 10 install) or disable SecureBoot, so SecureBoot is now turned off. 


From what I understand this is quite rare and I should file a bug report, although I have never filed one before and have no idea how to do so, any guidance on this would be appreciated :) 


Live USB
--------
I have set up an EFI-only 64bit live Ubuntu USB, which I achieved by formatting the drive to FAT32 and opening up my ubuntu-16.04.1-desktop-amd64.iso with Windows Explorer then copying all files across, as described here: [https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_an_EFI-only_image](https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_an_EFI-only_image)


When I boot from the live USB i am presented with the black and grey GRUB 2 bootloader menu which confirms my USB is booting in UEFI mode.


Fast Startup/Hibernate
----------------------
I have disabled Fast Startup and Hibernate in the Windows power settings.


QuickBoot/FastBoot and SRT
--------------------------
There are no options to disable QuickBoot/FastBoot, nor any mention of Intel Smart Response Technology (SRT) anywhere in my firmware settings, so i'm assuming these don't apply to my machine... please correct me if there is something I have missed.


EFI Partition
-------------


As I mentioned in my original post, my current partition scheme when viewed in Windows Disk Management is as follows:


PRIMARY 1 Windows 8.1 Recovery Partition (300MB)
PRIMARY 2 EFI System Partition (100MB)
PRIMARY 3 C: - Boot, Page File, Crash Dump, Primary Partition (464.44GB) [NTFS]
PRIMARY 4 Windows 10 Recovery Partition (822MB)


I am planning to shrink the volume from Disk Management and then manually partition from the live USB when installing Ubuntu. When I do this I will select PRIMARY 2 EFI System Partition (100MB) as my /boot/efi mount point (although if i'm not mistaken the Ubuntu installer should do this automatically anyway). GPT dictates that I can make all my new partitions Primary so there's no need for the extended/logical workaround.



Recovery
--------
I have all my files backed up on an external HD, I have a Windows 8 recovery/installation media USB drive and I've also got another USB with a full system image of my prior Windows 8.1 install at the ready made with Macrium Reflect as well as Macrium Reflect recovery media USB :)




QUESTIONS
---------
So from what i've gathered, I am taking all of the precautions necessary for a safe UEFI dual boot install for my machine. A few things I just wanted to ask before I go any further:


1. I was under the impression that Windows 8 onwards no longer required defragmenting, so is this not the case? Or does that only apply to SSD's? 


2. Do you mean to defrag before shrinking my Windows partition, after, or both?


3. Also, how many times would you recommend i defrag and reboot before beginning the install process?


4. Just out of curiosity, I am really torn on whether I would like to install Ubuntu or Mint. Is it safe to assume that all of these steps and precautions would work exactly the same for installing Mint, considering it is based on Ubuntu, or would this be opening up a whole new can of worms entirely? 


To be honest I think it's mainly the familiarity of Cinnamon that I'm after, so I could always install Ubuntu and get rid of Unity in favour of Cinnamon or possibly Mate if that's an option :)


I have been so overwhelmed with information on this whole topic that I nearly gave up at several points over the past few days, but looking back it's been a great learning experience and i'd just like to say many thanks once again for all of your advice and assistance!

---

### Post by mook765 on 2016-08-01
It is not a bad idea do defrag before shrinking the partition. the more free space is on your partition, the faster the defrag will work.
 Remind that when you shrink your partition, don't make it to small...
How many passes you need depends on the grade of fragmentation.
Windows is doing some work on that itself, but depends on your use of the computer, when your computer is never idle it will not happen.
I myself use the open-source-tool UltraDefrag, it's pretty fast and does some more optimization.
It is recommended to run chkdsk first ( run > cmd > chkdsk ).
[http://sourceforge.net/projects/ultradefrag/](http://sourceforge.net/projects/ultradefrag/)

---

### Post by mook765 on 2016-08-01
> 
When I do this I will select PRIMARY 2 EFI System Partition (100MB) as my /boot/efi mount point

I think you need to mount only the three partitions which you want to create
> 
- /
- /swap
- /home

but for this point please wait for some more replies from the gurus here...:)
Also a nice idea is following:
as you planned to create an extra ntfs-partition for sharing, it would be good to move all your private data  (e.g. the documents folder) from your windows partition to this shared partition.
You could make your windows partition a bit smaller than, system-backups will be smaller too
You can do that from windows, i guess it is right-click on your documents folder and then choose properties.
or you could realize that using ntfs-links ( google for that ).
When i work with windows, i always separate my private data from the system, only system is on c: my documents and other data i store in another partition d:
Doing that makes life a bit safer...( i live somewhere what you could call the ass off the world, when i run in problems i don't want to have too much headache ).

---

### Post by oldfred on 2016-08-01
If manually partitioning on the bottom of the partitioning screen is a device for boot loader. 
That whether BIOS or UEFI should be a drive like sda. 
But with UEFI, grub will only install its boot files into the ESP - efi system partition on sda.

If wanting to multiple boot, I might not use /home, but have a large data partition (or two). Back with XP I used a NTFS shared data partition, then with more Ubuntu installs, added a shared data Linux partition. Then stopped XP and all shared data was in Linux partition.

But partitioning is very personal. Even my most optimal partition plan is usually not so good a few years later, but by then I want a new main working drive anyway as I do not trust drives to last, no matter what warrantee is.

Your Acer has a unique requirement. All Acer require you to set the supervisory passwork and then enable "trust" on the .efi files in /EFI/ubuntu to allow Ubuntu to boot. Actually better than many brands now that violate UEFI and use description to boot and only valid description is "Windows Boot Manager" (but we have work arounds for them).

Some threads on Acer trust settings say you must downgrade UEFI. Newer ones say that upgrade to UEFI works. So best to have newest UEFI from Acer for your model.
       Acer Trust Settings - details:
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757
[/URL]
 Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757) 
      
 How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3 Supervisory password required
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273) 
    [URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]
[/URL]

---

