---
title: "Switching to Ubuntu from Windows 8 on a Samsung Laptop"
date: 2013-05-13
forum: New to Ubuntu
---

### Post by uhhhnoakes on 2013-05-13
I hope I am posting this in the correct section! I have recently learned about Ubuntu and want to make it my new operating system. I'm not the most tech apt individual but I am reading as much as I can and watching videos on YouTube. I found this forum in a Google search and am hoping that it will help with my installation and transition from Windows 8 on my Samsung Series 5 NP510R5E laptop to Ubuntu. I hope to learn all I can and currently I know very little to nothing about changing my OS so any help would be much appreciated! Thank you!

---

### Post by fantab on 2013-05-13
Do you want to completely replace Windows 8 with Ubuntu, or do you want to Dual-Boot? I hope this is your machine: [http://www.samsung.com/nz/consumer/pc-peripherals/notebook-pc/ultra-portable/NP510R5E-S01AU](http://www.samsung.com/nz/consumer/pc-peripherals/notebook-pc/ultra-portable/NP510R5E-S01AU)
Windows8 pre-installed computers come with UEFI and "Secure Boot" enabled, which makes installing Ubuntu on the machine a bit tricky. Most of the online information about how to install Ubuntu won't apply.

If you can tell us what exactly do you want then we can help you. I suggest you opt for Dual-Boot if you use any proprietary software on Windows. Otherwise you will end up frustrated because Windows software doesn't work on Linux.

Regards...

---

### Post by uhhhnoakes on 2013-05-13
I intend to completely erase Windows 8, if that is possible. (EDIT: perhaps I should begin with dual-boot to ensure I can use the OS properly?) 

Yes, that is my computer, I love it a lot but I'm coming from a Windows 7 desktop and it's tricky learning the Windows 8 so I figure now is as good a time as any to make the switch! I've heard nothing but good things about Ubuntu and the only programs I use are Libre Office and Firefox/Chrome for web browsing. I don't play games or use any software that is unique to windows. It's is primarily used for web browsing and document editing, which should be the same in any OS, from what I understand. I don't even use iTunes! 

I understand I will need the 64 but version but is there a particular release that will be better suited for my hardware? Thank you so much for your help :)

---

### Post by ikt on 2013-05-13
> **uhhhnoakes said:**
> I understand I will need the 64 but version but is there a particular release that will be better suited for my hardware? Thank you so much for your help :)

Welcome :)

Ubuntu has a new release every 6 months, and an LTS (Long Term Support) release every 2 years.

The current LTS is 12.04 (2012, April) and the current release is 13.04 (2013, April).

I would try installing the 13.04 release first as I find newer releases tend to have better hardware support than older releases.

Normally you just burn the ubuntu image to a USB stick or CD and then boot off of it, but because of UEFI/Secure boot it looks like there's some more steps involved, this might be some help: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by arubislander on 2013-05-13
Should the OP not first try out Ubuntu on his hardware by way of a live USB / CD? I can imagine that SecureBoot complicates this too, but [this link]("https://help.ubuntu.com/community/UEFI") should provide the starting point for asking some assistence

---

### Post by fantab on 2013-05-13
> **uhhhnoakes said:**
> I intend to completely erase Windows 8, if that is possible. (EDIT: perhaps I should begin with dual-boot to ensure I can use the OS properly?) 

...I'm coming from a Windows 7 desktop and it's tricky learning the Windows 8 so I figure now is as good a time as any to make the switch! 

Like it has been mentioned in an earlier post that Ubuntu releases a new version every six months and every two year a Long Term Support [LTS] is released. LTS is supported for 5 years while regular release is supported for 9 months. The current LTS is 12.04 (the version number is actually a date 2012, April or 4th month) and the current regular release is 13.04 released in 2013, April. Both are current and will support most of the new hardware. You can download either.

Here's how to go about installing Ubuntu:
1. Enter your BIOS set up and disable "Secure Boot". Also check in BIOS your SATA mode, there will be three options, IDE, RAID, AHCI. Ideally it should be AHCI. If its RAID then get back here and tell us you have RAID. 
2. Check if you have UEFI enabled. It will be. We are just making sure. 
3. Disable FAST BOOT/Quick Boot.

If you Want to dual boot then use Windows disk management to shrink your partition to make space for ubuntu, about 50GB should do. Do NOT create any partition just leave the space as 'unallocated'.

4. This assumes you have UEFI. Boot with Ubuntu install Disk -> "Try Ubuntu". If you run into "Black Screen" kind a situation then you must use 'NOMODESET": [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
5. From "Try ubuntu" will be greeted by a working ubuntu desktop. Establish connection and check if other hardware is working. IF all is good then Open disk management utility, GPARTED.
6. Using Gparted delete all partitions (Before you do this Back up all your data). If you want to dual boot then skip this step. 

** When installing as Dual-Boot just select "install alongside Windows" during installation at the " Installation Type" dialog and that should do.

7. Create New partitions with GPARTED:
# 250-300 MiB FAT32 , put a "boot" flag on this partition. This for EFI.
# 25-30GB Ext4 
# 25-30GB Ext4
# all the remaining GB Ext4 (this is to store your DATA, you can create more partitions if you need but formatted as ext4)
# 2-4GB SWAP (If you want 'hibernate' function then SWAP should be equal to or more than your RAM in GiB not GB.)

Apply all changes in Gparted. Close Gparted.

8. From desktop "Install Ubuntu". 
9. At the dialog which says 'Installation Type" choose 'SOMETHING ELSE' to manually direct your installation.
10. Select you first 25-30GB ext4 partition and click 'Change'... and use "/" as mountpoint.
11. Continue with your installation. When finisthed Reboot as instructed.

If you run into any problems when booting, ie if Uubntu does not boot then you may have to use [BOOT REPAIR]("https://help.ubuntu.com/community/Boot-Repair")... Boot repair when run scans your partitions for any errors and offers "Recommended Repair". That should take care of any boot issues.

Good Luck.

---

### Post by pfeiffep on 2013-05-13
> **uhhhnoakes said:**
> I hope I am posting this in the correct section! I have recently learned about Ubuntu and want to make it my new operating system. I'm not the most tech apt individual but I am reading as much as I can and watching videos on YouTube. I found this forum in a Google search and am hoping that it will help with my installation and transition from Windows 8 on my Samsung Series 5 NP510R5E laptop to Ubuntu. I hope to learn all I can and currently I know very little to nothing about changing my OS so any help would be much appreciated! Thank you!
Welcome!
Since you're experience is with Win7 I assume that you have a number of programs that you use. I suggest making a live USB flash drive (probably 8 GB) and give Ubuntu 13.04 a test run for about a week or so. Doing this will enable you to learn a bit about Ubuntu, find alternative programs to duplicate the functionality of the Win programs you currently use.
Here's a short list of programs that I've found extremely suitable::)

[TABLE="class: grid, width: 500"]
[TR]
[TD]**Windows 7**[/TD]
[TD]**Linux Equivalent**[/TD]
[/TR]
[TR]
[TD]OutLook[/TD]
[TD]Thunderbird[/TD]
[/TR]
[TR]
[TD]Internet Explorer[/TD]
[TD]Chromium[/TD]
[/TR]
[TR]
[TD]MS Office[/TD]
[TD]Libre Office[/TD]
[/TR]
[TR]
[TD]Windows Explorer[/TD]
[TD]Nautilus[/TD]
[/TR]
[TR]
[TD]Quicken[/TD]
[TD]Mint on line[/TD]
[/TR]
[/TABLE]

---

### Post by oldfred on 2013-05-13
If an UltraBook you also have an SSD and dual video. 

 Samsung series 5 UltraBook, erase Windows & install to SSD
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)
      
 Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)

      
 nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
        
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

 Some discussion of limits of new nVidia driver with some Optimus support
[http://ubuntuforums.org/showthread.php?t=2142215](http://ubuntuforums.org/showthread.php?t=2142215)
Installing new nVidia driver 319.12 beta
[http://www.barunisystems.com/index.php/site/page?view=blog](http://www.barunisystems.com/index.php/site/page?view=blog)

---

### Post by uhhhnoakes on 2013-05-14
> **fantab said:**
> Like it has been mentioned in an earlier post that Ubuntu releases a new version every six months and every two year a Long Term Support [LTS] is released. LTS is supported for 5 years while regular release is supported for 9 months. The current LTS is 12.04 (the version number is actually a date 2012, April or 4th month) and the current regular release is 13.04 released in 2013, April. Both are current and will support most of the new hardware. You can download either.

Here's how to go about installing Ubuntu:
1. Enter your BIOS set up and disable "Secure Boot". Also check in BIOS your SATA mode, there will be three options, IDE, RAID, AHCI. Ideally it should be AHCI. If its RAID then get back here and tell us you have RAID. 
2. Check if you have UEFI enabled. It will be. We are just making sure. 
3. Disable FAST BOOT/Quick Boot.

If you Want to dual boot then use Windows disk management to shrink your partition to make space for ubuntu, about 50GB should do. Do NOT create any partition just leave the space as 'unallocated'.

4. This assumes you have UEFI. Boot with Ubuntu install Disk -> "Try Ubuntu". If you run into "Black Screen" kind a situation then you must use 'NOMODESET": [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
5. From "Try ubuntu" will be greeted by a working ubuntu desktop. Establish connection and check if other hardware is working. IF all is good then Open disk management utility, GPARTED.
6. Using Gparted delete all partitions (Before you do this Back up all your data). If you want to dual boot then skip this step. 

** When installing as Dual-Boot just select "install alongside Windows" during installation at the " Installation Type" dialog and that should do.

7. Create New partitions with GPARTED:
# 250-300 MiB FAT32 , put a "boot" flag on this partition. This for EFI.
# 25-30GB Ext4 
# 25-30GB Ext4
# all the remaining GB Ext4 (this is to store your DATA, you can create more partitions if you need but formatted as ext4)
# 2-4GB SWAP (If you want 'hibernate' function then SWAP should be equal to or more than your RAM in GiB not GB.)

Apply all changes in Gparted. Close Gparted.

8. From desktop "Install Ubuntu". 
9. At the dialog which says 'Installation Type" choose 'SOMETHING ELSE' to manually direct your installation.
10. Select you first 25-30GB ext4 partition and click 'Change'... and use "/" as mountpoint.
11. Continue with your installation. When finisthed Reboot as instructed.

If you run into any problems when booting, ie if Uubntu does not boot then you may have to use [BOOT REPAIR]("https://help.ubuntu.com/community/Boot-Repair")... Boot repair when run scans your partitions for any errors and offers "Recommended Repair". That  sure should take care of any boot issues.

Good Luck.

Well, I followed steps 1-5 and am now testing out Ubuntu! Thanks so much for your help; I'm not sure I ever would've figure it out on my own! I have not done any of the Windows Disk Management or Gparted stuff yet... Do I need to allocate space in Windows prior to fully installing Ubuntu or can I do that now?

---

### Post by oldfred on 2013-05-14
If dual booting, I suggest using Windows disk tools to shrink Windows and reboot a couple of times. It will want to run chkdsk and make repairs for its now size.
Then you can use gparted to create partitions. Again if dual booting you use the existing efi partition that Windows has. You can only have one efi partition per hard drive and all installed systems install boot folders into that one efi partition.
Then you can use gparted to create partitions, and manual install to format partitions and specify mount points / , /home etc.

---

### Post by uhhhnoakes on 2013-05-14
Great, thanks so much! I'm installing alongside Windows 8 right now, per your directions. Thanks to everyone who has offered suggestions, I feel like I'm learning so much already! If I decide down the road to either uninstall Ubuntu or Windows, will this be possible?

---

### Post by fantab on 2013-05-14
Yes its possible. Do tell us how did it go.

---

### Post by Shansie on 2013-05-14
I cannot help with the actual changing over of your OS, I'm afraid. However, I've recently switched from Vista to Ubuntu and am keeping a blog where I keep track of the things I've learned and advice I've gotten for Ubuntu. (Otherwise, I'm bound to forget a lot of it.) It's rather small now, but if anything there is of help, feel free to browse through it! I'm also not very technically inclined, but I try. Here's the link:

[http://elucidateobfuscate.tumblr.com/](http://elucidateobfuscate.tumblr.com/)

I wish you luck!

---

### Post by uhhhnoakes on 2013-05-14
Install went perfectly! Everything is running smoothly and I'm now learning how to use the OS, thanks everyone for all your help! I might never log into windows again. If I were to about deleting the partitions in my drive and removing windows, what would be the best way to do this, now that I have Ubuntu installed as dual-boot?

---

### Post by Impavidus on 2013-05-14
You can simply delete the Windows partitions and update grub. The bootloader is controlled by Ubuntu already, uninstalling Windows is therefore easier than uninstalling Ubuntu. Then you can expand the Ubuntu partitions or create new Linux partitions for data or a second Linux install, if you like experimenting with Linux.

But wait for a while. You may find out there is one Windows program you can't miss yet, so it's best to keep Windows until you are really sure you're never going to need it any more or when you decide you need the disk space. Windows does no harm just sitting there on your hard disk.

---

### Post by uhhhnoakes on 2013-05-15
Ok good to know! I'm googling GRUB now.

I do not use any proprietary software and I have a desktop for itunes. My laptop is used strictly for document editing and web browsing. I found Xpad today and that has already been useful! Since I've installed Ubuntu, I've had several people ask how they could get it... Our IT guy has been encouraging us to look into Ubuntu and I think he was correct in doing so!

---

### Post by fantab on 2013-05-15
I still have Windows on its own HDD. I haven't used it in quite a while though. I kept it because I have a few games installed in Windows and they don't work well on Linux with 'playonlinux', but they work great if I run them from Windows partition with WINE.

If you want to remove Windows completely then, I'd suggest you do a clean install of Ubuntu after partitioning your HDD accordingly. Generally resizing partitons by moving them to left is not a good idea.

Install "**Synaptic**" Package Manager. Its better in a lot of ways to the default "Ubuntu Software Center".
To play mp3 and other proprietory formats you will have to install '**ubuntu-resticted-extras**'.
To install AdobeReader, Skype etc, you will have to enable Cannonical 'Partner' repositories. You can do it from Software center or Synaptic... it will be under edit in Software Center or settings under Synaptic.

After changing your repository, from Terminal you have to run:
```
sudo apt-get update
```

**ubuntu-tweak** is a good tool for beginners to have, you can install it with:

```
sudo add-apt-repository ppa:tualatrix/ppa 
sudo apt-get update 
sudo apt-get install ubuntu-tweak
```

The information in the following links is a MUST to understand Ubuntu:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[https://help.ubuntu.com/community/Glossary](https://help.ubuntu.com/community/Glossary)
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

Good Luck...

---

### Post by uhhhnoakes on 2013-05-15
```

Model: ATA WDC WD7500BPVT-3 (scsi)Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start   End    Size    File system  Name                          Flags
 1      1049kB  524MB  523MB   ntfs         Basic data partition          hidden, diag
 2      524MB   839MB  315MB   fat32        EFI system partition          boot
 3      839MB   973MB  134MB                Microsoft reserved partition  msftres
 4      973MB   675GB  674GB   ntfs         Basic data partition
 7      675GB   721GB  46.1GB  ext4
 8      721GB   727GB  6323MB
 5      727GB   749GB  22.1GB  ntfs         Basic data partition          hidden, diag
 6      749GB   750GB  1074MB  fat32        Basic data partition          hidden, diag




Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/cryptswap1: 6323MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop


Number  Start  End     Size    File system     Flags
 1      0.00B  6323MB  6323MB  linux-swap(v1)

```

This is what I see in GParted... from what I understand, I want to delete all but the ext4? 

[ATTACH=CONFIG]242618[/ATTACH]

---

### Post by uhhhnoakes on 2013-05-15
[http://ubuntuforums.org/showthread.php?t=2118532&p=12523182#post12523182](http://ubuntuforums.org/showthread.php?t=2118532&p=12523182#post12523182)

I just came across this post and saw that sometimes I may need to boot into Windows 8 for certain applications? If I were to shrink the partition down to 20 gigs or so, would that be sufficient? I only have a couple pictures and a program or two saved in Windows 8; should I do a restore of Windows then shrink the drive in the Disk Management tool? Thanks for helping me out here :)

---

### Post by fantab on 2013-05-15
If you had disabled 'Secure Boot' then that post is not relavant. Windows needs atleast 25% of free space in C: to run at optimum speed. Anything less than that will affect windows performance. You can shrink /dev/sda4 to about 100GB and use the rest of the space for DATA. Yes it is best if you shrink that partition from Windows only.

Ext4 is the partition where you installed Ubuntu.... also you have not created a SWAP partition, I don't see it. Its ok for now.

My suggestion: run Ubuntu for a month or so without changing anything, once you are comfortable with it you can remove Windows and reinstall Ubuntu after partitioning your HDD properly. Right now it is messy. It will get more messier as create more partitions. It won't affect the performance in anyway but....

---

### Post by oldfred on 2013-05-15
I think the OP installed with encrypted /home. Then swap is not seen by partition tools as it looks like unformatted space and the dev/mapper is swap.

I also suggest not to rush into deleting Windows. A fair number of users come back and have one application that really only works in Windows and they want to re-install it. It took me about 5 years before I totally weaned myself off Windows.

The only partitions that are Windows are the Windows recovery or repair on sda1, msftres on sda3 & the main Window install on sda4. Probably sda5 is the Vendor recovery which would let you reinstall Windows. Both Ubuntu & Windows use the efi partition so you cannot delete it.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)

---

### Post by fantab on 2013-05-15
> **oldfred said:**
> I think the OP installed with encrypted /home. Then swap is not seen by partition tools as it looks like unformatted space and the dev/mapper is swap.

I missed it. 

Thanks...

---

### Post by uhhhnoakes on 2013-05-17
Well, I made the switch completely and I love it! I have no use for Windows on this laptop (I have 3 other computers for different purposes so I'm not concerned about any Windows/Mac only programs)

Below is a picture of what my HD looks like now... I would like to increase the space in my main partition so I can put some music and movies on there without using up my 30GBs. Do I need to use my USBkey to do this?

[ATTACH=CONFIG]242691[/ATTACH]

---

### Post by fantab on 2013-05-17
You can put all your Music, Movies, etc on the /dev/sda5 and lets call it DATA Partition. By default this partition will not be mounted, ie, made available for system. You can either mount it manually by clicking on that partition from File Explorer, Nautillus. or You can automount it with Ubuntu boot by adding its entry in /etc/fstab. I use the former method. I don't like it to be mounted all the time, just when I want/need it.

You can create folders in the Partition like, MyMUSIC, myMovies etc then create a 'symlink' in your Home folder. You can access all your Music from Home folder. The 'symlink' will only work if the Partition is mounted.

Here is how you create symlinks it:
```
ln -s /path/to/the/folder /location/of/the/link
```

To make the Data partition mount with system boot you have edit the /etc/fstab... more instructions:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Then you can place symlinks as show above or [http://ubuntuforums.org/showthread.php?t=2145037](http://ubuntuforums.org/showthread.php?t=2145037) (Read Kopkins' post)

You can also use 'bind' but I can't help you with that in detail.

---

### Post by uhhhnoakes on 2013-05-19
I mounted the sda5 but when I go to drag any files in there it tells me I do not have permission...

---

### Post by oldfred on 2013-05-19
Ownership & permissions in Linux are important. 
Are you mounting with fstab or manually?

       Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

      
 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type; also ownership & permissions of NTFS is only set with the defaults you set as you mount it with fstab or manually, NTFS does not support ownership and permissions. 
sudo fdisk -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown $USER:$USER /mnt/data

For permanent mount with fstab - both NTFS & ext4 examples:
      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

---

### Post by uhhhnoakes on 2013-05-19
Is there a reason to not increase the sda2 partition, or is that even possible? I'm reading up on the links you posted, thank you, they're a bit complicated though (I'm very new at this)

---

### Post by fantab on 2013-05-20
No, you don't need more than you have. The idea is to separate 'system' files and your data.

With regards to permissions and mounting, I think oldfred has covered everything.
The simplest way is to to mount the partition and run:

sudo chown -R username /path/to/mounted/partitions 
(you can determine the path from Nautilus by rightclicking, select properties and look at location) In your case, the most likely path will be /media/username/partitionname

---

### Post by uhhhnoakes on 2013-05-20
Ok awesome thanks for the help! I have a lot to learn still. I should see if there are any Ubuntu Challenged Support Groups in my area ;)

Thanks all!

---

### Post by uhhhnoakes on 2013-05-24
Well, I just did an update and now when I boot up it says disconnected from Plymouth then goes to a black screen. I tried hitting shift at boot the e to edit and placing nomodeset the f10 but it takes me to the same place.... What happened when I updated?

---

### Post by uhhhnoakes on 2013-05-24
[ATTACH=CONFIG]242960[/ATTACH]

I can get here...

---

### Post by newb85 on 2013-05-24
You're looking at a question that is completely independent of the original question in this thread.  I recommend that you instead start a new thread with a title that describes your new question.  It's good practice, and if I remember right, part of the Code of Conduct.

---

