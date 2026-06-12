---
title: "Uefi, ssd"
date: 2014-07-02
forum: New to Ubuntu
---

### Post by TDully on 2014-07-02
Been away tooo long!!!

In short I have Toshiba laptop model P55, on win 8.1 (amd64)! Have add the following: 16Gbs RAM @ 1600Mhz; 480Gb SSD; also a Hard Drive Caddy w/ 1Tb Sata 3 disc

Have @ 165Gb on SSD, which WILL have Ubuntu 14.04 (amd64)( as well as having a partition or 2 on the extra hard drive)

Have been reading a lot, to get me back up and going. Have my USB drive ready to go...but... Am rather confused with UEFI. Have seen this posted a few times, as well as answered a few different ways.  what are the current best practices as far as installing with out issues...(only had 1 minor issue before, w/MBR an win XP, fixed in no time)

From what I see at present, is to shut off UEFI, AND secure boot (basically, disable the current set up, in order to use "Legacy" boot orders CORRECT ???

2nd, at the time of install, IS it best to set up the partitions on the 2nd hard drive, or do that at a later time?

3rd with EXT4, ... do I need to add any extra commands for TRIM

Lastly, First time w/SSD on a laptop. One thing i truly love is how fast things move (e.g.  Start up; external/internal data transfers; back ups etc.) have read that the performance is not he best, ANY guidance here, to keep the truly SSD speeds?

Thank you very much for any guidance on this matter....Can't wait till installed and running!!!

---

### Post by grahammechanical on 2014-07-02
> [COLOR=#000000]From what I see at present, is to shut off UEFI, AND secure boot (basically, disable the current set up, in order to use "Legacy" boot orders CORRECT ???[/COLOR]

Not really.

> [COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [/FONT][/COLOR]

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.[/FONT]
[*=left]if Ubuntu is the only operating system on your computer, then it does not matter, you can install Ubuntu in EFI mode or not.
[/LIST]


> [COLOR=#333333][FONT=Ubuntu]To install Ubuntu in EFI mode:[/FONT][/COLOR]

[LIST]
[*=left][FONT=inherit]Use a 64bit disk of Ubuntu ([Ubuntu32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555"))[/FONT]
[*=left][FONT=inherit]Use a supported version of Ubuntu. Support for UEFI appeared in 11.10, but has become more reliable in next versions. Support for UEFI[SecureBoot]("https://help.ubuntu.com/community/SecureBoot") appeared in 12.10 and 12.04.2.[/FONT]
[*=left][FONT=inherit]Set up your firmware (BIOS) to boot the disk in UEFI mode (see the "[Identifying if the computer boots the HDD in EFI mode]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode")" paragraph below)[/FONT]
[*=left]Then:
[LIST]
[*=left]nothing special is required if you use the automatic installer of Ubuntu ("Install Ubuntu alongside others" or "Erase the disk and install Ubuntu"). Important: if you have a pre-installed Windows and you want to keep it, do not choose "Erase the disk and install Ubuntu".
[*=left][FONT=inherit]if you use the manual partitioning ("Something else"), the difference is that you will have to set the /boot/efi mount point to the EFI partition. And if there was not any EFI partition on your HDD, you first will have to create it (see the "[Creating an EFI partition]("https://help.ubuntu.com/community/UEFI#Creating_an_EFI_partition")" paragraph below).[/FONT]
[/LIST]
[/LIST]


Notice this

> 
[LIST]
[*=left][FONT=inherit]In your BIOS, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows8, also [disable FastStartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html").[/FONT]
[/LIST]


You did not mention doing that, did you?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

With Ubuntu we can get the benefits of both UEFI and Secure Boot. I can offer no assurances that this link is useful or accurate.

[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

Regards.

---

### Post by oldfred on 2014-07-02
If you understand partitioning, I strongly suggest partitioning in advance and only using Something Else.
And do a full backup of Windows and efi partition.

Many users just use one of the auto install options and overwrite Windows. Not all the options clearly state that entire drive is overwritten. And on reinstalls it says it will replace previous Ubuntu but overwrites entire drive. And the LVM install or encrypted install is always full drive.
Or only use Something else so you have full control over partition sizes and formats.

Supposedly 14.04 does add a weekly trim for some models of SSD. It did not on mine, but I add a daily trim cron task anyway.
       Shows both discard & fstrim methods for trim
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)
Add commands to trim file in cron.daily:
gksu gedit /etc/cron.daily/trim
sudo chmod +x /etc/cron.daily/trim


```
#!/bin/sh
# trim
LOG=/var/log/trim.log
echo "*** $(date -R) ***" >> $LOG
fstrim -v / >> $LOG
# fstrim -v /home >> $LOG


```


I have my SSD with only Ubuntu. It is only 64GB but has two / (root) partitions. One is my current 12.04 (then 16.04) and the other is my soon to be current 14.04. Or I alternate / installs.
I keep my /home inside / and use about  11GB of the 28GB that each / is. But I have all data including some of the hidden data folders like Thunderbird & Firefox profiles in my data partitions on my hard drive.

My goal is to have a fully bootable system on every hard drive and have data on various other drives. Or any one drive failure should not prevent me from booting. But I also have several bootable flash drives with full installs or multiple repair ISO as emergency backup way to boot.

Some other Toshiba models:
  [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)
Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

### Post by sudodus on 2014-07-02
Thanks *grahammechanical* and *oldfred* for the very informative posts :-)
I will borrow from them to help people in similar situations.

---

### Post by TDully on 2014-07-03
WOW.....

First off, I truly thank you both, Gahammechanical and Oldfred!!!! thank you very much to a quick reply!

More over, I THANK YOU , for what matter most of all, in any Forum, is an up to date, quick, accurate answer to an Issue that someone has!!!

Just awesome! I was on that thinking, but wanted to have it directly answered!! That way, I am not doing any work with trying to have both OS's BOOTING, and working!
Like I did mentioned, did have Ubuntu 12.10 on an XP OS. (x86) Now that the wife, wants me out of the basement, she purchased this Laptop! Sort of like the machine, but would have
never bought win 8.1.
Anyway, what I have read about 14.04lt is that it will work with EFI, as well as Secure Boot. However, will not work with fast startup! In my case I have tested that after the install of the SSD.
I did not see any difference, in Fast start up, (enabled or disabled) with my machine. Awesome!

 When all done, (after the 4th of July!!! Happy birthday America!!!)   I will have this up and running, and will report back on this!

Again, I THANK YOU both! 
Excellent reply!!
thanks

---

### Post by TDully on 2014-07-12
> **TDully said:**
> WOW.....

 When all done, (after the 4th of July!!! Happy birthday America!!!)   I will have this up and running, and will report back on this!

Again, I THANK YOU both! 
Excellent reply!!
thanks

Well sorry fo ra late reply, this week has been rather crazy.

Ok, In my case, i ran into some small issues. One of which I had completely forgot about. (I took the easy route, and cloned my Org. drive on to the SSD...in doing that, the actual boot for Win 8.1 was jacked up. i was able to use "EasyBCD 2.2 to fix that, however, THAT, was an issue, due to EasyBCD palying around in BIOS)...only booted to Ubuntu. Was able to use Command propmt through my usb for Win 8.1 to fix the boot. 
Like I had mentioned, I did want 2 partitons for Ubuntu 14.04, ( set up was 50Gb for each,) the SWAP size was rather odd! seems that there is no set reasonning for size (e.g. some say it is 2x the size of RAM, some say it is 1x, others 1.5x the RAM size) I have 16gb of RAM, I went with 24Gb for the SWAP . 
I can say this is much faster than anything i have used so far, and I just might dumb win 8.1 off my laptop. Truly Love what I have. 

I do thank you for the guidance, has turned out great. 
(I need to research that SWAP partition, so i have the correct size, certainly do not feel it needs to be so large...could be me)

Again, thank you
T

---

### Post by oldfred on 2014-07-12
My suggestion on swap is 2GB.
But if you have 16GB of RAM the other suggestion is 0. You will never need swap.
With an SSD, you do not want nor need hibernation and if you did want hibernation then you would need 16GiB which is a bit more than 16GB as RAM and hard drives count differently.

The very old rule of 2X was when RAM was 256MB. Rule of 1X was pretty much for any system with 2GB or more of RAM. I have 4GB and almost never use swap. As I understand the only time you might need it with more RAM is if editing video as that can use a lot of RAM.

EasyBCD usually creates more issues than it solves for booting. You may need it to fix Windows BCD issues, but I do not know much about it and what it can do.

---

### Post by TDully on 2014-07-13
> **oldfred said:**
> My suggestion on swap is 2GB.

EasyBCD usually creates more issues than it solves for booting. You may need it to fix Windows BCD issues, but I do not know much about it and what it can do.



OH YES... EasyBCD is more of a way to screw up the "boot" for any system.... Just my thought.

SWAP..... I did say I was a bit confused as to all the info that I have researched about it. HOLY MOLY.... Well looks as if I need to fix the HUGE swap locations. I will decrease on the SSD to 2GB, as well as the 2nd Hard drive, (Platter) do to 2 Gb also.
Thank you for help on that. Ceratinly do not want to waste space on the SSD. 2nd drive is actually  for my File back ups. If something would happen to the main SSD drive I would not lose anyting. 

Agian I thank you. Hope Vaction was wonderful!!!

---

### Post by oldfred on 2014-07-13
If you install and have swap on both drives, installer will find both and add them. It does that to me as somewhere one of my test installs must have added a swap and it have two. I just have some swap on a hard drive so it can find it.

I also like to have a bootable install on every hard drive. I also like to test the next version just to see what is new and different so I have several installs on my larger rotating drive as well.

I suscribe to this logic, but do not have Knoppix installed since I have Ubuntu on every drive except my old XP drive which now is not used. (but do have bootable Knoppix ISO on a flash drive).
 Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)

Vacation was good, Visited Son in Denver.

---

### Post by at_first_light on 2014-07-16
It sounds like you've resolved your concerns, but I have a few additional comments anyways for others in the same boat who might be reading this thread.

1. When installing Ubuntu in UEFI mode you must have an active internet connection, or the installation of Grub2 will fail preventing you from booting Windows or Ubuntu. If this happens to you might be able
to fix it with boot-repair.
2. When running Ubuntu on an ssd you may not want a swap partition. In instances where Ubuntu needs to write lots of temporary that the ram can't support without kicking out other files over-frequently having a swap partition will be helpful to performance, but the rest of the time it's not because your drive's read speeds will make copying files to ram quick (and ram gets better performance), and you won't be wearing out the ssd as quickly because you won't be writing temporary files to it constantly. If you aren't sure which to do, then install Ubuntu with swap, and simply turn swap off manually when you want to.
3. Do not put a swap partition on a hard drive if you are running Ubuntu from an ssd unless you are willing to accept a performance decrease on any files cached there due to the lower read/write speeds. 
4. Ubuntu can be installed in CSM mode (Bios emulation for compatibility) on UEFI computers, but if you are dual booting with Windows 8 make sure that both operating systems are installed in the same mode, or you will have to switch modes when switching between operating systems.

---

### Post by kurt18947 on 2014-07-16
I find it useful to install a very lightweight app called "htop" found in the repositories.  It has few functions but one is to enable monitoring of memory used, both RAM and swap.  I let it run in a terminal and check it occasionally when running a demanding or several apps simultaneously.  HTOP enables me get to get a feel for how much RAM is actually used in various scenarios.    I suspect the OldFred is correct, you really don't need any swap with 16 GB. system RAM.  This machine has a whopping 3 GB.:smile:,  no swap no problems with everyday web browsing and office-type  usage.  I have a 'how low can I go' machine -- 667 Mhz. Celeron that shipped with Windows ME.  I upgraded its original 64 MB. RAM to a whopping 512 MB.  That machine has and uses a swap partition.

---

### Post by Bucky Ball on 2014-07-16
You don't need a /swap partition on the data drive. As oldfred mentioned, 2Gb /swap is fine (probably never used anyway).

---

