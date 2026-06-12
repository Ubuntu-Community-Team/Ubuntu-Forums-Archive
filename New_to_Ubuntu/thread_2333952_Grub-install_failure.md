---
title: "Grub-install failure"
date: 2016-08-14
forum: New to Ubuntu
---

### Post by 4everwikid on 2016-08-14
I just finished my PC build, and am trying to install Ubuntu 16.04, both, first time. I was able to burn an image of the ISO, and boot up Ubuntu through my cd/dvd drive. However, when I try to install it to my SSD I receive an error. It states "Unable to install Grub in /dev/sda... Executing 'grub-install/dev/sda' failed... This is a fatal error". Once I click out of that, it states "Bootloader install failed", and wont let me do anything else after that. I haven't messed with any of the settings. Just burned the image and tossed it in. Any help would be great, and I'll try to provide as much information as possible.


Build Specs: Gigabyte z170 MB, I7-6700k processor, GTX 980ti classified, Trident 16GB ram, h110i cooling system, phanteks enthoo pro case, EVGA 1000G PSU

---

### Post by oldfred on 2016-08-14
UEFI or BIOS? (how you boot installer is then how it installs)
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 


Are you planning on installing Windows?

Is drive gpt or MBR partitioned?
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) 

With gpt you must have an ESP - efi system partition as FAT32 with boot flag for UEFI grub to install. Or if BIOS/CSM/Legacy you must have a 1 or 2MB unformatted partition with bios_grub flag for grub's core.img so it can install correctly.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by 4everwikid on 2016-08-14
UEFI or BIOS? (how you boot installer is then how it installs)
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

**I couldn't honestly tell you UEFI or BIOS. My assumption is BIOS, but I'm not sure. How would I know for sure? I'll try to take some screen shots and post them.**

Are you planning on installing Windows?

**No, I do not plan on installing Windows. My intentions was to run the machine solely with Ubuntu**.

Is drive gpt or MBR partitioned?
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) 

**I'll have to read through the links, but all the parts are brand new and this is a fresh build that I completed this morning. **

With gpt you must have an ESP - efi system partition as FAT32 with boot flag for UEFI grub to install. Or if BIOS/CSM/Legacy you must have a 1 or 2MB unformatted partition with bios_grub flag for grub's core.img so it can install correctly.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)



I've tried google searching and troubleshooting, but haven't found anything that's worked.

---

### Post by 4everwikid on 2016-08-14
[[IMG]http://i298.photobucket.com/albums/mm261/4everwikid/Screenshot%20from%202016-08-15%2000-01-07.png[/IMG]]("http://s298.photobucket.com/user/4everwikid/media/Screenshot%20from%202016-08-15%2000-01-07.png.html")[[IMG]http://i298.photobucket.com/albums/mm261/4everwikid/Screenshot%20from%202016-08-15%2000-01-57.png[/IMG]]("http://s298.photobucket.com/user/4everwikid/media/Screenshot%20from%202016-08-15%2000-01-57.png.html")[[IMG]http://i298.photobucket.com/albums/mm261/4everwikid/Screenshot%20from%202016-08-15%2000-04-30.png[/IMG]]("http://s298.photobucket.com/user/4everwikid/media/Screenshot%20from%202016-08-15%2000-04-30.png.html")[[IMG]http://i298.photobucket.com/albums/mm261/4everwikid/Screenshot%20from%202016-08-15%2000-04-41.png[/IMG]]("http://s298.photobucket.com/user/4everwikid/media/Screenshot%20from%202016-08-15%2000-04-41.png.html")[IMG]http://i298.photobucket.com/albums/mm261/4everwikid/Screenshot%20from%202016-08-15%2000-04-48.png[/IMG]

[[IMG]http://i298.photobucket.com/albums/mm261/4everwikid/Screenshot%20from%202016-08-14%2020-10-04.png[/IMG]]("http://s298.photobucket.com/user/4everwikid/media/Screenshot%20from%202016-08-14%2020-10-04.png.html")
[[IMG]http://i298.photobucket.com/albums/mm261/4everwikid/Screenshot%20from%202016-08-14%2020-10-11.png[/IMG]]("http://s298.photobucket.com/user/4everwikid/media/Screenshot%20from%202016-08-14%2020-10-11.png.html")

---

### Post by Geoffrey_Arndt on 2016-08-14
What file system and partitions are currently on the SSD (aka sdb)?    Did you prepare the SSD first?   If not, you can set up the partitions by using the "something else" install option.    So don't use "Erase Disk & Install Ubuntu" for your next try.   IF you have a data HDD (hard drive) in addition to the SSD, you should see if you change loading Grub from sda to sdb instead (using the available dropdown selector).   Be sure to use ext4 as the main ubuntu file system you create & setup your swap on sdb.

---

### Post by 4everwikid on 2016-08-14
> **Geoffrey_Arndt said:**
> What file system and partitions are currently on the SSD (aka sdb)?    Did you prepare the SSD first?   If not, you can set up the partitions by using the "something else" install option.    So don't use "Erase Disk & Install Ubuntu" for your next try.   IF you have a data HDD (hard drive) in addition to the SSD, you should see if you change loading Grub from sda to sdb instead (using the available dropdown selector).

The SSD is labeled sda. I didn't prepare the SSD, but I just tried the "something else". I'm not sure if I got everything right, but it's attempting to install now. I looked at the links that oldfred posted, but some of it was confusing. First time, tackling anything like this.

---

### Post by 4everwikid on 2016-08-14
Well, whatever I did worked. It downloaded and asked to restart. Had to hit the power switch, but it loaded up. I'll take a screen shot of the screen.

---

### Post by 4everwikid on 2016-08-14
My screen resolution is stuck at 640x480 with no other options.

---

### Post by Geoffrey_Arndt on 2016-08-14
OK, so next step is to install video drivers.    Click on the top left icon (called the dash) and type "additional drivers", enter.    It should take you to a screen (a subset of System Settings>Software & Updates>Additional Drivers.   Initiate a scan for drivers and accept what comes up.    It would have been good for you to include full system specs in your first message of this thread, including what graphics system is on the PC . . . (intel, amd/ati, nvidia).   BTW, your screenshots showed an ssd that is identified as "sdb" - - do you have two ssd's in the PC?

---

### Post by 4everwikid on 2016-08-14
> **Geoffrey_Arndt said:**
> OK, so next step is to install video drivers.    Click on the top left icon (called the dash) and type "additional drivers", enter.    It should take you to a screen (a subset of System Settings>Software & Updates>Additional Drivers.   Initiate a scan for drivers and accept what comes up.    It would have been good for you to include full system specs in your first message of this thread, including what graphics system is on the PC . . . (intel, amd/ati, nvidia).   BTW, your screenshots showed an ssd that is identified as "sdb" - - do you have two ssd's in the PC?

The sdb should have been the 1TB HDD that I have as well. Even though I didn't select it for the OS to upload to it, it remained there for whatever reason. I went to additional drivers, and it shows my graphics card and CPU. However, there is nothing to download or a way to scan that I can see. 

I'll update my first post with the build specs.

---

### Post by Geoffrey_Arndt on 2016-08-14
From the screenpics, sdb is ID'd as the 500GiB Samsung SSD, meaning the 1 TB HDD is sda.    Generally, grub is installed to the drive containing the OS as on my Sys76 Galago UltraPro laptop, the 120 ssd is sdb (with Grub), and the hdd is a 500 Gib which is sda.    After you install the video drivers, run the program "gparted" (use Dash to display it), and post a screen shot what your drives and partitions look like.

---

### Post by 4everwikid on 2016-08-14
No drivers downloaded, and my screen is stuck in 640x480 and can't get a shot of what you requested. I'll screen shot what I see for additional drivers in a moment.

---

### Post by 4everwikid on 2016-08-14
[[IMG]http://i298.photobucket.com/albums/mm261/4everwikid/Screenshot%20from%202016-08-14%2023-43-49.png[/IMG]]("http://s298.photobucket.com/user/4everwikid/media/Screenshot%20from%202016-08-14%2023-43-49.png.html")
[[IMG]http://i298.photobucket.com/albums/mm261/4everwikid/Screenshot%20from%202016-08-14%2023-44-01.png[/IMG]]("http://s298.photobucket.com/user/4everwikid/media/Screenshot%20from%202016-08-14%2023-44-01.png.html")

---

### Post by Geoffrey_Arndt on 2016-08-14
Select Nvidia, then use the tab key to navigate to Apply Changes, select that (or enter) and let it download. . . . . then reboot.

---

### Post by 4everwikid on 2016-08-15
Done... screen resolution is normal now. When I type "gparted" only an image icon comes up. Nothing with any information or hard drive data.



EDIT: Had to install the gparted program


[[IMG]http://i298.photobucket.com/albums/mm261/4everwikid/Ubuntu/Screenshot%20from%202016-08-15%2000-39-32.png[/IMG]](http://s298.photobucket.com/user/4everwikid/media/Ubuntu/Screenshot%20from%202016-08-15%2000-39-32.png.html)
[[IMG]http://i298.photobucket.com/albums/mm261/4everwikid/Ubuntu/Screenshot%20from%202016-08-15%2000-39-59.png[/IMG]](http://s298.photobucket.com/user/4everwikid/media/Ubuntu/Screenshot%20from%202016-08-15%2000-39-59.png.html)

---

### Post by oldfred on 2016-08-15
Please attach screen shots.
Easy to do with Forum's advanced editor and paperclip icon.

 If you use the advanced editor, you can use the paperclip icon to attach screenshots. Post #4
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098) 

The Linux NTFS driver will not mount NTFS partitions that are hibernated nor if they need chkdsk. Make sure Windows fast start up is off which is always on hibernation and NTFS partition does not need chkdsk.

Post this. 
      
  sudo parted /dev/sda unit s print

---

### Post by 4everwikid on 2016-08-15
> **oldfred said:**
> Please attach screen shots.
Easy to do with Forum's advanced editor and paperclip icon.

 If you use the advanced editor, you can use the paperclip icon to attach screenshots. Post #4
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098) 

The Linux NTFS driver will not mount NTFS partitions that are hibernated nor if they need chkdsk. Make sure Windows fast start up is off which is always on hibernation and NTFS partition does not need chkdsk.

Post this. 
      
  sudo parted /dev/sda unit s print

Sorry, I tried to attach, but the images were too large. I'll look for an photo editing app through ubuntu. How do I make sure that Windows fast start up is not on? Is that through Bios? I believe it's off.

---

### Post by oldfred on 2016-08-15
Nautilus has nautilus-image-converter for resizing photos, but screenshots are normally smaller and not an issue.

There is UEFI fast boot setting in UEFI. Often best to have off at least until fully configured. It can be so quick that you do not have time to press a key to get into UEFI or one time boot menu key.

Windows has fast start up which is always on hibernation.
       Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

---

### Post by Geoffrey_Arndt on 2016-08-15
I'm not sure why, but I thought Ubuntu was/is the only OS on your system.   If not, and if you're doing a dual-boot, please confirm.   

Also, your Ubuntu partition is WAY too small.   In a short while (2-6 months?), you'll likely run out of space.   That was the purpose of installing/running gparted and attaching the screenshot.

You will need to check out some Youtube video tutorials on how to use "gparted" to manage your partitions.   You will need to "expand" the ext4 partition to give Ubuntu space to grow and handle updates, etc.   It's essential you learn gparted, or this fine machine will be wasted on this haphazard install.

EDIT:   I don''t see any Windows file systems, so it seems you are running Linux only.    But, all that "unallocated" space needs to be managed to provide a more sensible use of the space.

PS:  for OldFred . . am assuming that hibernation not in play (aka a factor) on this system.

PPS:  for OldFred . . is gparted the right tool to use on this UEFI/GPT system?   Can it handle that as it does on BIOS/MBR systems. . . ??

---

### Post by 4everwikid on 2016-08-15
Sorry for the delay. It was a nuisance trying to get the screen shot resized correctly. I tried to find nautilus image converter and followed a youtube video, but it didn't work. Had to use shotwell viewer to edit it. 

Geoffrey, Ubuntu is my only OS on this system. 

I created a new partition, well copied the original and into a larger partition. I'm looking at videos, when I can, trying to learn gparted and terminal. One of the links I found gave me the size of the Ubuntu partition,and that's why they are the size that they are. I'm trying to figure out how to best manage the hard drives.

P.S: I appreciate you guys taking the time to help me with this.

---

### Post by oldfred on 2016-08-15
I started to change to gpt when I installed 10.10 and have only used gparted to partition drives. All new or reformatted drives are converted to gpt. Even most of my flash drives as gpt.
But I also use gdisk to review partitions as old fdisk did not work on gpt. Only with 16.04 does fdisk now recognize gpt.

Your / (root) partition looks small. I normally use 25GB for / on SSD, but have all data normally in /home in a /mnt/data partition on HDD.

Older, but gparted has not really changed much:
       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by 4everwikid on 2016-08-15
I have two root partitions now. I copied the smaller original partition into a larger one with 100GB. I'll look over the links that you supplied. It's a lot to figure out, but loving the potential options and perks of having Ubuntu. Been wanting to build a PC with Linux for a long time, and really don't want to have Windows on the system. I may eventually toss Windows on another SSD, but for now I would like to stay with Ubuntu only. 

Can I edit/modify partitions? Like through Windows or Android OS, there's the ability to move files to different drives or SD cards. I've never messed with partitions before this.

One thing that I kept seeing, was to have the partitions not too large that the system had to search a large area for. I guess the goal is to have a boot and home partition? I would like to have a designated "gaming" partition. I was somehow successful to create a partition on my HDD for "movies". Only reason I know that, is because when I tried to download a game from steam the HDD "movie" folder was an option. Along with the /boot and /home partitions.

---

### Post by Geoffrey_Arndt on 2016-08-15
Not sure if having two root partitions is good (I don't know if I've ever heard or seen that before) . . the approach I've seen that works is to create an empty ext4 partition, place it to the right of the root partition, and then expand root into the empty ext partition.   You would be left with one large / (root) which includes all system files and your home (/home/user1).    

Many folks like to have 3 Linux partitions (root, home & swap).    That's the most common scenario or setup.   It's unusual to see a separate boot partition (and not needed).   The size of the partition (allocation) has little or nothing to do with search speed.

Yes, partitions can be modified (as suggested above) and files can be copied, moved from one to another partition or to different devices or offline.   A second data drive (internal, external or cloud) is often a better solution than too many partitions on the same drive. 

Probably best to learn the basic Ubuntu OS gui and tools, and the file system logic (including uefi/gpt/bios/mbr and their CRUD methods/tools (create, read, update, delete).    Then start to learn the CLI - - starting with navigation and then common commands (get cheat sheets).

Here's a nice all-around beginners learning tool for Linux:    [https://linuxjourney.com/](https://linuxjourney.com/)

---

### Post by 4everwikid on 2016-08-15
Thanks, dude, I appreciate the info. I'll take some more time looking at that link you gave, and the ones oldfred provided.

---

