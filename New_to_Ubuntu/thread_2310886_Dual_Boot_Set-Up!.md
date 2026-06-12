---
title: "Dual Boot Set-Up!"
date: 2016-01-22
forum: New to Ubuntu
---

### Post by DeathByDualBoot on 2016-01-22
Hello,
         I've recently put a computer together and am just about to make a bootable USB with Ubuntu on it. I wanted to set-up a dual-boot with Ubuntu and Windows 7.

Here are the specs:

AMD 4350 (4.2 GHz, 4-Core Processor)
8 Gigs of DDR 3
GeForce GTX 960 with 4 Gigs of Vram
1 240 Gig SSD
1 1 TB HD
No optical drive.

_Question 1._ So, I am wondering how much of my 240 SSD should I devote to Ubuntu vs Windows to make sure it runs properly. 
I know that with Windows, I can install it on one part of the SSD and then use my 1 TB drive for the programs, but can I do the same with Ubuntu? 

_Question 2._ What should I do when it asks me for how much I'd like to do for the "/" and the "Swap" etc? This part is very confusing for me because I am not fully sure what the different things mean. I know that "/" means the actual system, I think, and "Swap" is virtual ram? This part is VERY confusing for me during the instillation process.

I should mention that I will be using this machine for gaming, in case that's not clear. I want have Linux around if there are games that can use that, which is why I am installing it as a dual boot. 

Thanks for your help in advance.

-DeathByDualBoot

---

### Post by newbie-user on 2016-01-22
> Question 1. So, I am wondering how much of my 240 SSD should I devote to Ubuntu vs Windows to make sure it runs properly. 
I know that with Windows, I can install it on one part of the SSD and then use my 1 TB drive for the programs, but can I do the same with Ubuntu? 
Yes, you can install Ubuntu programs wherever you like but that requires more work.

> Question 2. What should I do when it asks me for how much I'd like to do for the "/" and the "Swap" etc? This part is very confusing for me because I am not fully sure what the different things mean. I know that "/" means the actual system, I think, and "Swap" is virtual ram? This part is VERY confusing for me during the instillation process.
You'll need to read up on linux file structure, as I don't think I'll do a good job explaining it here. A basic/automatic installation will require only "/" and swap. The swap space is a reserved part of the hard drive that is used when the system memory fills up, so it's virtual ram, as you stated. A guided partitioning of the hard drive will automatically set the swap space for you at roughly 1.5-2 times the amount of physical ram you have. You can change that manually during the install process.

---

### Post by yancek on 2016-01-22
15-25GB for the / filesystem partition should be more than enough unless you plan to install an exceptional amount of additional software.  With 8GB of RAM, 2-4GB of swap should be more than enough, in fact most people with that much RAM will never use swap.

---

### Post by oldfred on 2016-01-22
Your new system is UEFI but will offer BIOS boot which is the 35 year old method of booting system.
And Windows 7 default boot is BIOS, but can easily be copied to a flash drive and a few files moved around to make it UEFI.

With new high powered system probably better to use UEFI with gpt partitioning.
       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

But whichever way you decide to install, be sure to install both Ubuntu & Windows in the same boot mode, both BIOS/CSM or both UEFI.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

Windows will not let you stay at Windows 7 for long. It already is nagging everyone to update to Windows 10.

I also suggest both drives be gpt if UEFI, with both drives having an ESP - efi system partition if UEFI. And if you do choose BIOS, you still can have gpt on the data drive. But Windows has to have MBR(msdos) for BIOS boot. Windows reads gpt partitioned drives fine, just will only boot from them with UEFI. 
But Ubuntu can boot with BIOS or UEFI from gpt partitioned drives.

More info on UEFI in link below in my signature.

---

### Post by grahammechanical on 2016-01-22
Somebody correct me if I am wrong, but it is my understanding that we get much improved speed of loading with an SSD drive in comparison with a drive that has spinning discs.

So, it seems to me that with both OS on the SSD each OS will load very quick but with programs on the 1TB hard disk that speed advantage will no longer apply. Correct?

Regards.

---

### Post by DeathByDualBoot on 2016-01-23
Wow, thanks for the help.

I'm going to have to look up a lot of what you wrote, but I guess the main takeaway is that I should use the same method to install BOTH Ubuntu and Linux?

Since I don't have an optical drive, I was going to use a bootable for Windows, as well. I just wanted to know how much of my 240GB SSD I should devote to Ubuntu and how much should go to the "/" and how much to "Swap."

I'll look further into the information you gave me and get back to you guys.




_Small update to anyone that cares:_
I've assembled all the parts and my new rig works! I used the Live USB to test Ubuntu on there and there are no structural problems with the computer's hardware, which is a milestone for me.




_Progress So Far:_
Okay, so I've decided I'll devote around 30 gb to "/", 4 to "Swap". 
So, how would I go about making a Game like The Witcher 3. How would I make it so it installs on the 1 TB drive? Will I have to give Ubuntu ownership of a part of the 1 TB drive?

---

### Post by yancek on 2016-01-23
I did an online search for your game and the latest thing I found was from October, 2015.  At that time, it was not available for Linux but you might do a search yourself .  If you want games, you are better off with windows.

If you want to share data between windows and Ubuntu, create an ntfs partition on the 1TB drive.  You will be able to then view data from both windows/Linux.

---

### Post by DeathByDualBoot on 2016-01-23
Okay,
          so how does one install a program on a drive that Linux isn't located on? So, if I install Linux on my SSD, then have the 1 TB drive vacant, how do I tell Linux to install something on the 1TB drive? Because the SSD is small.

Thanks in advance.

-DeathByDualBoot

---

### Post by Geoffrey_Arndt on 2016-01-24
Because the actual Ubuntu OS will be installed to the SSD, that is also where the programs will be installed.    If you change the basic install so that the users /home directory is on a separate partition on the 1 TB drive, "part" of any given program will be installed there (1 TB drive) and other parts of the program will still be installed to the SSD.   So, the 1 TB drive is essentially a data drive for any OS's installed on the SSD  . . . OR . . . . for any other OS's (Linux Mint, Fedora, etc.) that are installed to their own partitions on the 1 TB drive (can probably install 2 or 3 dozen other versions of Ubuntu and Linux distros there).  By the way, you (the user) doesn't actually install the program anywhere . . . the package manager program will put the various parts of the program (binaries, libraries, etc.) where the programmer specified they should go.    Certain types of programs (mainly scripts) can be installed to user specified directories . . but that's only an occasional exception

So, you see (or I hope you're starting to see) . . . that Linux isn't Windows.   It's totally different in how it's managed, and how the file structure works.

So Further . . . if you want a decent version of Ubuntu that can grow over time, I'd give it at least 50 Gib of the SSD - - as some gaming programs in Steam take up a LOT of space.

You have lots to learn Grasshopper . . . . .

---

### Post by pfeiffep on 2016-01-24
> **grahammechanical said:**
> Somebody correct me if I am wrong, but it is my understanding that we get much improved speed of loading with an SSD drive in comparison with a drive that has spinning discs.

So, it seems to me that with both OS on the SSD each OS will load very quick but with programs on the 1TB hard disk that speed advantage will no longer apply. Correct?

Regards.I believe you are correct (the speed advantage will apply to boot up) ... IMO use the spinning disk for data! I have no experience with gaming and how the programs use data.

---

### Post by DeathByDualBoot on 2016-01-24
> **Geoffrey_Arndt said:**
> Because the actual Ubuntu OS will be installed to the SSD, that is also where the programs will be installed.    If you change the basic install so that the users /home directory is on a separate partition on the 1 TB drive, "part" of any given program will be installed there (1 TB drive) and other parts of the program will still be installed to the SSD.   So, the 1 TB drive is essentially a data drive for any OS's installed on the SSD  . . . OR . . . . for any other OS's (Linux Mint, Fedora, etc.) that are installed to their own partitions on the 1 TB drive (can probably install 2 or 3 dozen other versions of Ubuntu and Linux distros there).  By the way, you (the user) doesn't actually install the program anywhere . . . the package manager program will put the various parts of the program (binaries, libraries, etc.) where the programmer specified they should go.    Certain types of programs (mainly scripts) can be installed to user specified directories . . but that's only an occasional exception

So, you see (or I hope you're starting to see) . . . that Linux isn't Windows.   It's totally different in how it's managed, and how the file structure works.

So Further . . . if you want a decent version of Ubuntu that can grow over time, I'd give it at least 50 Gib of the SSD - - as some gaming programs in Steam take up a LOT of space.

You have lots to learn Grasshopper . . . . .

This post REALLY helped.

Thanks a lot, bro.

Can you see what I've done here and let me know if it works? 

I want my "/" and my Swap to be on the SSD and I want my /Home to be on the 1TB HD.

Let me know if this will do what I want it to.

Thanks in advance.

-DeathByDualBoot

---

### Post by oldfred on 2016-01-25
If /home is sda1 then it is primary, if using MBR(msdos).
Primary partitions are always sda1 thru sda4. Any one primary can be an extended partition, and it then "contains" all the logical partitions that start with sda5.
If using gpt partitioning all partitions are primary, in effect as it has only one type.

But if installing Windows, it must have a primary partition to boot from, if BIOS/MBR. 
If UEFI/gpt all systems boot from the ESP - efi system partition.

Because with a large HDD, I like to also install my test versions of Ubuntu on it. My main working install is usually a LTS, but I like to install and have working one of the newer installs, just to see what changes and as a backup way to directly boot  from HDD, just in case of issues on SSD. So I allocated another 25 GB. During first installs, I just do not fully allocate HDD. I do not share /home but do share larger data partition.

---

### Post by Geoffrey_Arndt on 2016-01-25
As you're using a UEFI based system (versus mbr/dos), there are only primary partitions (no logical) - - - so no difference between sda and sdb.   

By putting /home partition on sda (1 TB standard hdd), your system will be slightly slower than if / and /home were on the SSD (sdb).

---

### Post by DeathByDualBoot on 2016-01-25
> **Geoffrey_Arndt said:**
> As you're using a UEFI based system (versus mbr/dos), there are only primary partitions (no logical) - - - so no difference between sda and sdb.   

By putting /home partition on sda (1 TB standard hdd), your system will be slightly slower than if / and /home were on the SSD (sdb).

Are you speaking in theory or will it be a noticeable amount of reduction in speed? 

I'm eventually thinking of playing video games on this thing, you think that will be a problem?

-DeathByDualBoot

---

### Post by Vladlenin5000 on 2016-01-25
The basic OS services, as well as standard installed programs explicitly run by the user will boot and start faster if on SSD. However many of those services/programs will read from and write to its respective config folders which are user specific and therefore reside in /home. That being on a HDD will slow down the process a little bit. Whether or not it will be noticeable depends entirely on what's running.

---

### Post by Geoffrey_Arndt on 2016-01-25
The cpu type, gpu type and amount of ram will be more of a factor with games (although that is not my area of knowledge or interest).   In general, Windows is a better gaming platform, while Linux is a more secure and less intrusive production platform.    

So, you're good to go as you've outlined,  startup time will be 10 -15 seconds longer, shutdown times will be 10-15 seconds versus 5 seconds _or less_ with SSD only OS setup.

Let us know how your install goes.

---

### Post by DeathByDualBoot on 2016-01-28
> **Geoffrey_Arndt said:**
> The cpu type, gpu type and amount of ram will be more of a factor with games (although that is not my area of knowledge or interest).   In general, Windows is a better gaming platform, while Linux is a more secure and less intrusive production platform.    

So, you're good to go as you've outlined,  startup time will be 10 -15 seconds longer, shutdown times will be 10-15 seconds versus 5 seconds _or less_ with SSD only OS setup.

Let us know how your install goes.

Thanks a lot!

It works alright. The boot-up time is like less than 9 seconds and it works well for accessing data. I'll know more when I start installing video games, but this is a good start.

I'll hit you all up again if I need help with other things, but as of right now A HUGE THANKS TO EVERYONE THAT RESPONDED TO THIS THREAD!


-DeathByDualBoot

---

