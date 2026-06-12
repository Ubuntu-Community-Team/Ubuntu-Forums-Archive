---
title: "Ubuntu Installation onto different hard drive."
date: 2014-01-08
forum: New to Ubuntu
---

### Post by jack-bucinskas on 2014-01-08
Hey guys,

I am new to Linux and would greatly appreciate help.


I have Windows 8.1 Pro - x64 on a 128gb SSD and I want to install Ubuntu onto a seperate 500GB HDD, in the Ubuntu installation can I do this:

480 x 1024 =  491520mb for root ( / )

Then use the left over space as the swap partition? 

In a video guide I was watching he made a /boot partition and a /home partition, I am sure I don't need to do this but I am posting on here just to make sure I don't make any mistakes. Also on the last option do I install the bootloader onto my 128gb SSD (I have Windows installed onto it with plenty of space left)

---

### Post by mastablasta on 2014-01-08
why would you asign 20 GB for swap? that's is too large. how much ram do you have?

/boot partition might be needed.
/home is not necessary

it all depends on how windows was installed: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

don't worry about grub taking space (it replaces or rather installs in front of windows MBR): [http://www.ramkitech.com/2012/01/grub2-and-themes-customization.html](http://www.ramkitech.com/2012/01/grub2-and-themes-customization.html)

about boot partition: _[COLOR=#810081][https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)[/COLOR]_

---

### Post by cincibluer6 on 2014-01-08
Alright, double check everything I say as I'm not familiar with Windows and the GPT partitioning (and all the UEFI nonsense) but-

1) I ALWAYS recommend making a separate /home partition as if the OS is screwed up, you can just replace that and keep your /home directory safe (with all your media, files, etc.)
2) /boot might be needed with GPT and using it with Win8. You need to look that up specifically. Before it was never needed.
3) swap only needs to be about 2GB MAX. Most modern machines have way more than enough RAM (and knowing that you're running Win8 with an SSD I'm guessing you have at least 4GB of RAM, if not more.)
4) Depending on how the UEFI reacts (which makes this a wildcard), you normally just place GRUB on whatever partition/drive your computer is booting from. GRUB will then just let you choose whatever OS. It doesn't necessarily have to be installed on the Ubuntu drive or the Windows one (again, this not taking into account UEFI and all that.)

Hope that helps a little. You have convinced me though to read up on installing with Win8 as I'm tired of not knowing how the new UEFI and GPT stuff has affected installs.

---

### Post by jack-bucinskas on 2014-01-08
I have 8GB of ram and there was about a 6.3GB swap file since hard drives and gigabytes are exactly 1000mb so there was only about 6.3GB of space left on the hard drive the last time i tried to install ubuntu and failed also I have an UEFI Bios so would I need the boot partition?

---

### Post by jack-bucinskas on 2014-01-08
I am not really sure on how to install Windows 8.1 x64 dual boot with Ubuntu since I don't really understand this UEFI business and if it would be possible it would be great to be hand held through my installation :/ this is all very confusing to me and if it werent for my games I would've swapped to Linux months ago.

---

### Post by oldfred on 2014-01-08
I would create an efi partition on hard drive and make sure hard drive is also gpt partitioned. I like to make sure each drive can be booted without any other. Then when one drive fails you can boot the other.
But you probably will install Ubuntu's efi boot files in the SSD's efi file.
I prefer smaller / (root) partitions of 20 or 25GB and have separate /home and/or data partitions. If dual booting with Windows a NTFS data partition is usually suggested.

Best to confirm current partitions.
sudo parted -l

Lots of UEFI info and many links to good UEFI info in link in my signature.

---

### Post by jack-bucinskas on 2014-01-09
Is there a step-by-step EFI/UEFI/Windows 8 & Dual Boot Ubuntu guide that I can follow?

I am probably make the HDD NTFS partitions so I can read/write on my Data HDD with all my music and video's on.

So far, what I have gained off your posts:

~8GB for /boot (EFI/UEFI)
2GB for Swap
Left over space for Ubuntu

I will just re-install Ubuntu clean if I do something wrong instead of making seperate /home folders since I will be mostly reading from my Data HDD with movies, videos, music, etc.

---

### Post by mastablasta on 2014-01-10
8GB for /boot is too much. boot has only a few file as i know. 200MB is enough, 1GB is quite a lot and you can sqeeze a liveOS in it.

the problem with UEFI is that each manufacturer implemented it a bit differently. and then there are also different partition tables and different way that OEM's instaleld preinstalled windows etc. i suggest you take a look on oldfred's links.  then first diagnose how your system is actually set up now. once you have theat you can choose the correct howto or correct way to install.

it is a bit difficult to do than under BIOS (i guess this was Microsofts goal) but at the same time once you know how your computer is set up you can follow the appropriate guide and then it is not difficult at all. at the moment you just got stuck at partitioning and this is the part that needs some planning even in BIOS.

for example you do not need separate /home if you plan to put data on NTFS partition. /home is sort of like my documetns in windows or maybe better the stuff that is in windows under user folder. linux programs are also very small in size sicne they share libraries.

---

### Post by jack-bucinskas on 2014-01-10
So the /boot folder stores UEFI / EFI ?

Also under my motherboard there is no option to enable legacy it is stuck in "Asus-EZ mode",
and under my Windows 8 Advanced boot options there is no UEFI / EFI settings or Secure / Fast boot either.

---

### Post by jaimeda104 on 2014-01-10
Hey jack-bucinskas. Some days ago I manage to install Ubuntu 13.10 in dual boot with a pre installed Windows 8. In my case I also have an SSD of 128 GB and one HDD of 1TB. I decided to take full advantage of my SSD high speed (compared to the HDD) installing both systems in it and saving the HDD just for data partitions as oldfred mentioned. First of all, you really don't need to create any other partition than / (root) and SWAP for Ubuntu to work properly. If you want or need (depending on your requirements) you can create more partitions, being the most common ones: /boot, /home and /data (in my experience). 

Now going to the SWAP partition, people recommend creating one of the same or bigger size than your RAM because of hibernatation purposes, in your case I would make a SWAP partition of 8GB. I would recommend installing Ubuntu / on the SSD but since you are using it all for Windows then you have no other option than using the HDD for it. 

To be able to install Ubuntu in dual boot with Windows 8 (I suppose it is the same for 8.1) there are two important things you regularly need to do (things that you did not need before): 

1.- Disable the Fast Boot. If you don't have a Fast Boot option in Windows it is probably because you havae disabled (somehow) hibernate. In this case, Fast Boot is already disabled so you don't need to worry. The thing is Fast Boot works with the hyberfile.sys file in Windows (at shutdown it saves kernel and drivers things to this files so when starting up it only needs to read this files directly, creating a faster startup). In my case I did not have any UEFI settings for Fast Boot or something similar.

2.- Disable Secure Boot in UEFI settings. In this case I think it really depends on the MB. In my case I could only disable Secure Boot but not change to legacy mode. Also, in my case, for installing Ubunut 13.10 I did not have to disable de Secure Boot. Everything went ok with just disabling the Fast Boot.

After this you should be able to load the Ubuntu installer (USB or CD) changing the boot options. You should worry about partitions creations after you do all this and can use the "try ubuntu without installing" option from the live CD or USB.

---

### Post by oldfred on 2014-01-10
An efi partition holds boot files for all systems, usually just grub for Ubuntu or Windows boot loader. It can be considered to be like the MBR in BIOS, but supports as many systems as you install not just one.

Most desktop systems do not need a separate /boot partition. If  a server, or encrypted with LVM or using RAID you may want or need a /boot.

Windows has several partitions that it needs, but both Windows and Ubuntu share the same efi partition.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

    
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

      
 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Do not know much about installing Windows.
      
 [http://www.eightforums.com/](http://www.eightforums.com/)

---

### Post by jack-bucinskas on 2014-01-10
I cannot seem to find Secure boot or any UEFI settings at all on my Motherboard, so I guess I am right to install Ubuntu, I want to install this on a seperate HDD (spare 500GB I found lying around) as I need Windows to stay on my SSD for my fast game loads and such, I have most of my Data on another 2TB HDD. I have got 60GB left on my SSD for a future game I might want to install on there and I want to keep a little space open because I heard they perform and last longer when they aren't jammed full.

I have disable hybernation via CMD Prompt. in Windows since I never used it and I guess just for performance since when you use it, while its hybernating it pretty much writes all your data to the disk you have Windows installed onto then leaves them there when you boot up again.

I think what I did wrong is that I put the bootloader onto my 500GB drive instead of my default drive and that must of done something when I booted. So I will try again when I have some free time :)


EDIT: I have managed to find fast-start up and it is now disabled, so is hibernation

---

