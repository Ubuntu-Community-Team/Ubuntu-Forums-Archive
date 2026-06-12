---
title: "Installing Ubuntu 64 on 2nd Partition"
date: 2011-12-14
forum: New to Ubuntu
---

### Post by EndemicTruth on 2011-12-14
Hey guys, 

        I looked through the forums but couldn't find an exact answer for what I am trying to figure out, so bear with me :D

        I ran WUBI and installed Ubuntu to my 2nd drive partition (Win7 on 1st) and when I run it it asked for an installation size. I put 10GB not knowing what exactly to use, and when I got around to using it I couldn't install / download anything because it said I did not have enough drive space. Since I am installing it on a partition with about 100GB of space, I want to be able to run games and such in Ubuntu, but it only gives me an option to use up to 30GB of space. Am I able to use the rest of my partition or am I stuck at the 30GB limit? 

 I was thinking the "installation size" just referred to how much space the install uses, but I couldn't find a way to use the rest of my space on the partition... it just kept saying not enough space. 

Sorry if this is a silly question... still a newbie here :confused:

---

### Post by mlentink on 2011-12-14
Haven't looked at Wubi much lately, but I can tell you this: Wubi doesn't actually install on a partition. It creates a windows file, and then installs ubuntu within that file. That makes it possible to uninstall ubuntu through the 'Add/Remove Programs'-mechanism.
You might help us help you by giving a bit more info on how exactly you did install it, e.g. on you windows C: or D: drive. Mind you, even those 'drives' could be partitions on the same physical disk.

---

### Post by ppv on 2011-12-14
As the previous post says, Wubi does not install onto a partition. It installs as an application on Windows. Can you try to uninstall your Wubi installation through add/ remove programs in Windows and then install it again using 30Gb as the install size. This size refers to the size of the file that Wubi would use to install Ubuntu rather than the partition size.

---

### Post by Mark Phelps on 2011-12-14
Maybe bcbc will be along, as he's the "resident expert" on Wubi ... but I believe that 30GB is the size limit.  After all, it's intended to be used short-term to try out Ubuntu, and for that, you don't need a lot of space.

If you have a LOT invested in it, there are ways to migrate the Wubi install to its own partition, but that involves a lot of work.  You would probably do better removing the Wubi install and doing a standard dual-boot install in its place.

And, if you are considering that, then read on ...

If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

### Post by Paqman on 2011-12-14
The 30GB size limit is a limitation of Wubi. Tbh, you could install a LOT of apps before hitting the 30GB size limit, especially since the whole rest of the 100GB on that partition can be found at /host, so you can plonk all your data there and leave the entire 30GB for apps and config files.

If you're convinced you need more room than that, then you'll have to burn a LiveCD or USB and do a full install. Don't stress about that, it's actually pretty easy.

---

### Post by EndemicTruth on 2011-12-14
> **Paqman said:**
> The 30GB size limit is a limitation of Wubi. Tbh, you could install a LOT of apps before hitting the 30GB size limit, especially since the whole rest of the 100GB on that partition can be found at /host, so you can plonk all your data there and leave the entire 30GB for apps and config files.

If you're convinced you need more room than that, then you'll have to burn a LiveCD or USB and do a full install. Don't stress about that, it's actually pretty easy.


I would like to have about 100GB free to play with (I want to get into some programming and also hacking / messing around with getting Windows games to run on Linux)... so I would like to do the "standard dual boot" I guess you could call it. 

In other words I want to have 1 partition with Win7 (My main 350GB partition) and then one with Ubuntu (My other 115GB partition - Both are labeled primary partitions and should be good to install an OS to). I would like them to be two completely separate entities... i.e. choosing to boot one or the other via boot options or what have you. Is that possible? I have a Ubuntu 64 disc burned but when trying to install it I got the impression that I could only overwrite Windows or install to my main partition. If anyone knows a simple walkthrough for this I would be eternally grateful. :guitar:

---

### Post by EndemicTruth on 2011-12-14
Anyone? Help :(

---

### Post by Mark Phelps on 2011-12-14
> **EndemicTruth said:**
> Anyone? Help :(

Did you even bother to READ my post?? 

The instructions there tell you what to do to prepare your PC for installing dual-boot with Win7 and Ubuntu.

---

### Post by jwbrase on 2011-12-14
> **Mark Phelps said:**
> 

If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Just a minute. That's assuming that the only storage device attached to the machine is a single physical hard drive. That might not be the case. You get four primary partitions per hard drive, so if someone with two physical hard drives with a total of four partitions between them comes across your post, they might end up getting rid of a partition when both of their drives can accommodate at least one more partition. 

> **EndemicTruth said:**
> I would like to have about 100GB free to play with (I want to get into some programming and also hacking / messing around with getting Windows games to run on Linux)... so I would like to do the "standard dual boot" I guess you could call it. 

In other words I want to have 1 partition with Win7 (My main 350GB partition) and then one with Ubuntu (My other 115GB partition - Both are labeled primary partitions and should be good to install an OS to).

Is there any data on this second partition? Is it an NTFS partition or an ext3/ext4 partition? Did you create it with the intention of installing Ubuntu on it (and, if so, with what software), or did you create it for Windows before you decided to install Ubuntu?

If it has any data on it, and isn't an ext3 or ext4 partition, be warned that you'll have to reformat the partition to ext3 or 4 to install Ubuntu, and this will overwrite any data on the partition.

EDIT: Frankly, though, if your computer has a spare drive bay, I'd put in a second hard drive and install Ubuntu to that. That way you don't even need to touch the disk that Windows is on. I've even installed Ubuntu to external hard drives in the past.

---

### Post by EndemicTruth on 2011-12-14
> **Mark Phelps said:**
> Did you even bother to READ my post?? 

The instructions there tell you what to do to prepare your PC for installing dual-boot with Win7 and Ubuntu.

Um... yes. I did. It didn't help me. I already know how to partition my drives... I just don't understand why it isn't prompting to install Ubuntu to the 2nd partition when I try to install it (It's an obtuse question... I'm not sure how to word my issue properly I guess.) 


> **jwbrase said:**
> Just a minute. That's assuming that the only storage device attached to the machine is a single physical hard drive. That might not be the case. You get four primary partitions per hard drive, so if someone with two physical hard drives with a total of four partitions between them comes across your post, they might end up getting rid of a partition when both of their drives can accommodate at least one more partition. 



Is there any data on this second partition? Is it an NTFS partition or an ext3/ext4 partition? Did you create it with the intention of installing Ubuntu on it (and, if so, with what software), or did you create it for Windows before you decided to install Ubuntu?

If it has any data on it, and isn't an ext3 or ext4 partition, be warned that you'll have to reformat the partition to ext3 or 4 to install Ubuntu, and this will overwrite any data on the partition.

I have two partitions: One is my C: drive... 350GB, primary, NTFS, which is running Windows 7 just fine. 

The second partition is my G: drive... 115GB, NTFS, also a primary partition. (This is the one I want Ubuntu on... it is free of data) 

I split these using the disk management area of my device manager in Win7. From what I'm reading it looks like I need to change the 115GB partition from NTFS to ext 3 or 4 in order to install Ubuntu on it? The "how" part of installing it on this second partition is where I'm hitting a wall... and if I get it installed properly from there... will it give me the option to boot drive C: or G: when I start up my PC? 

Forgive my ignorance on this matter. :(

---

### Post by Dlambert on 2011-12-14
WUBI will not install to a separate partition. If you really want it on that 100GB partition, download and burn the Ubuntu image to a CD and install.

---

### Post by EndemicTruth on 2011-12-14
> **Dlambert said:**
> WUBI will not install to a separate partition. If you really want it on that 100GB partition, download and burn the Ubuntu image to a CD and install.

That's what I want to do... maybe I'm just missing something but when I install it (or try to) to the 2nd partition it never gives me the option to boot that partition; just loads up windows as usual. Am I just doing something wrong? :confused:


Edit: It appears that I can't make a partition in disk management (Through Win7 device manager) that is ext3/4... which further complicates things for me.

---

### Post by jwbrase on 2011-12-14
> **EndemicTruth said:**
> I have two partitions: One is my C: drive... 350GB, primary, NTFS, which is running Windows 7 just fine. 

The second partition is my G: drive... 115GB, NTFS, also a primary partition. (This is the one I want Ubuntu on... it is free of data) 

I split these using the Disk Management area of my device manager. From what I'm reading it looks like I need to change it to ext 3 or 4 in order to install Ubuntu on it?

As long as they aren't dynamic disks, that should suffice.

> And if I get it installed properly from there... will it give me the option to boot drive C: or G: when I start up my PC? 

Forgive my ignorance on this matter. :(

It should, but dual booting Windows and Linux on the same drive is something I've never done. I've only done a dual boot setup with the two on separate drives. I'll leave it to someone else to advise you in this matter.

---

### Post by EndemicTruth on 2011-12-14
No one knows how to dual-boot without using the WUBI thing or using a 2nd hard drive? There has to be some way to run Ubuntu on one partition, and Win7 and the other... with a choice as to which on boot-up. 

Please[-o<

---

### Post by EndemicTruth on 2011-12-14
Well since my other thread appears to be DoA: 

I have a single-drive laptop with two partitions. One is NTFS running Win7; the other is unformatted.

On the unformatted partition I want to install Ubuntu 64... I am at the install window and it is asking for "Device for boot loader installation" and shows my main HD, as well as the two partitions. If I want to be able to select which OS I load when the system boots... which should I pick? 

Thank you in advance!

---

### Post by wolfen69 on 2011-12-14
You can just select the main HD if it allows you to. GRUB will be installed, and you will be given the choice of which OS to boot.

---

### Post by JohnDillinger43 on 2011-12-14
What wolfen69 said: if you select the main HD, you'll get the GRUB menu that'll allow you the pick which OS you want to boot.  Probably your options are going to be sda (your primary hard drive), sda1, sda2, sda3, etc. (since Win7 uses several partitions, and I assume you'll set up several for Ubuntu).  You'd want to select sda (the entire device) rather than one of the specific partitions.

---

### Post by EndemicTruth on 2011-12-14
Well I didn't see this post but I tried installing it to the same partition as Ubuntu but yet again it just boots straight to Windows... :frown:

---

### Post by supercheetah on 2011-12-14
You do want it on that first partition or else your computer won't boot GRUB which can then give you the option of booting either Windows or Ubuntu.

---

### Post by EndemicTruth on 2011-12-14
> **supercheetah said:**
> You do want it on that first partition or else your computer won't boot GRUB which can then give you the option of booting either Windows or Ubuntu.

Many thanks... think I have it under control now :D

---

### Post by JohnDillinger43 on 2011-12-14
I'd suggest using GParted.  Great utility for (re)partitioning that comes with Ubuntu.  Win7 typically takes up three partitions, so probably what you'll want to do is create an extended partition and stick your Ubuntu partitions in there as logical partitions.  This is what I did on my laptop and it worked just fine -- same setup as you basically, I had a prebuilt laptop with Win7 installed, and shrunk down the Win7 partition to make room for the Ubuntu installation.  I did separate partitions for boot (/boot), OS (/), swap, and data (/home).

Basically I followed this tutorial: [http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html).  I found it very helpful, maybe you will as well.  I don't really know anything about Linux filesystems or partitioning, so probably you shouldn't assume that my way is the best way, but so far my system has worked with no problems.  I did my /boot partition as ext2, root (/) and /home as ext4.  The swap partition has its own filesystem (linux-swap).  The /boot partition is the only one whose purpose I don't really know (other than the obvious); root is for the OS and /home is for your files (this makes it easier to upgrade or change the OS without messing up your data), and swap is used for virtual memory.  GParted makes it easy to do all this stuff.  Once you have things partitioned the way you want, install Ubuntu to your root partition, and install the bootloader to your main drive (e.g., sda) rather than one of the specific partitions (e.g., sda1, sda2, etc.).  This will allow GRUB to give you options of which OS to boot to each time you turn on the computer.  Sometimes installing side by side like this can tweak Windows a bit, so make sure you have a Win7 CD or backup image (on the Win7 recovery partition) ready, though in my case Windows just had to run chkdsk after installation and everything was fine after that.

Hope that helps, feel free to reply if anything's unclear; I just did this earlier this week so most of the info (and uncertainty) is fresh in my mind.

---

### Post by oldos2er on 2011-12-14
Linux doesn't require a primary partition (or partitions), extended logical will do fine. You'll need a small swap partition, say 2GB (or less, depending on how much RAM you have and if you'll be using hibernation).

Once you've booted the CD and started the installation, choose "Something else", formerly known as manual installation.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

[http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Dual-Booting_Windows_and_Ubuntu)

---

### Post by Ms. Daisy on 2011-12-14
I've got ubuntu & Windows happily playing on separate partitions of  my computer.  I'm confused by what you're saying.  You'll have to help  me understand so I can help you. First, you have uninstalled wubi from  windows, correct? And you're definitely not installing a second hard  drive, yes?

So you burned an Ubuntu installation iso cd from [here]("http://www.ubuntu.com/download/ubuntu/download").  And you say you installed it, but you don't get the menu at  boot-up to choose ubuntu or windows. Is that correct?  Are you certain  that you don't get the menu? It only displays for 30 seconds or so,  perhaps you walked away?  If we know for certain it's installed then we know what the path is to fix that.

If you haven't actually installed Ubuntu, then the following applies.
[QUOTE=EndemicTruth]The second partition is my G: drive... 115GB, NTFS,  also a primary  partition. (This is the one I want Ubuntu on... it is free of data) I  split these using the Disk Management area of my device manager. From  what I'm reading it looks like I need to change it to ext 3 or 4 in  order to install Ubuntu on it? [/QUOTE] 
[QUOTE=EndemicTruth]Edit: It appears that I can't make a partition in  disk management  (Through Win7 device manager) that is ext3/4... which further  complicates things for me.[/QUOTE] This is where you totally lost me.   So you're saying that the G drive is brand new, created by you, and it  is formatted but otherwise completely empty.  Right?  Can you go into  Windows disk management and report back exactly what's on your hard  drive (screen shot, type it, whatever)?  We all need to understand  exactly how many partitions you have existing right now.

Anyway, the instructions on creating a dual boot are [here]("http://www.ubuntu.com/download/ubuntu/download").  There are some important steps to take on your windows partition before  you install Ubuntu- markphelps hit the highlights, more detailed ones  are [here]("https://help.ubuntu.com/community/DualBoot"). 

Edit: I wasn't quick enough on the draw- two people posted while I typed this!

---

### Post by oldos2er on 2011-12-14
Threads merged. Please don't start more than one thread per issue.

---

### Post by ppv on 2011-12-15
Probably, is it the case that OP is trying to install using Wubi and hence does not see the installation options that are being looked for.

@OP can you let us know how are you trying to install Ubuntu.

---

### Post by Miljet on 2011-12-15
The OP has stated that he intends to use "drive G" for Ubuntu. That suggests that he already has at least five partitions. Either he has created an extended partition or he is not using MBR/MSDOS. In the latter case, that is a whole 'nother ball game.

Perhaps it would be a good idea to boot the live CD, open a terminal,and type ```
sudo fdisk -l
```

Or better yet, run the live CD, download and run the Boot Info Script from here: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

