---
title: "Dual boot windows 7 and ubuntu"
date: 2013-05-15
forum: New to Ubuntu
---

### Post by dragonzoid2001 on 2013-05-15
[SIZE=3][FONT=times new roman]I am a complete beginner in any Linux operating system and I was planning to give it a try due to recommendations from family and friends. I found a great chance to do that with the new computer I was going to build soon, but I have never dual booted, nor have I used Linux before; used to only use windows. I was planning on my main system being Ubuntu, where I do all of my programming (college student learning comp sci) and to just try out Linux. However, I enjoy playing pc games quite a bit and that is mainly what I use windows for. I was reading a few guides online, but I couldn't find any that described the partitioning and the procedure for installing both Windows 7 (so far, windows 8 just annoys me) and Ubuntu and how I should partition my drive. 

I have not built my computer yet, but I think I have my parts planned out already.
[/FONT][/SIZE]**[h=1][SIZE=3][FONT=times new roman][COLOR=#000000]CPU: [/COLOR]Intel Core i5-3570K[/FONT][/SIZE][/h][h=1][SIZE=3][FONT=times new roman][COLOR=#000000]Motherboard: [/COLOR][COLOR=#000000]Gigabyte GA-Z77X-UD5H[/COLOR][COLOR=#000000][/COLOR][/FONT][/SIZE][/h][h=1][SIZE=3][FONT=times new roman][COLOR=#000000]Memory: G.Skill Ripjaws X Series 8GB (2 x 4GB) DDR3-1600 Memory [/COLOR][/FONT][/SIZE][/h][h=1][SIZE=3][FONT=times new roman][COLOR=#000000]Storage: Western Digital Caviar TBlue 1TB 3.5" 7200RPM Internal Hard Drive  [/COLOR][/FONT][/SIZE][/h][h=1][SIZE=3][FONT=times new roman][COLOR=#000000]Video Card: Radeon HD 7870 2GB Video Card  [/COLOR][/FONT][/SIZE][/h][h=1][SIZE=3][FONT=times new roman][B][B][B][COLOR=#000000]Operating System: Microsoft Windows 7 Home Premium Full (64-bit)  && Ubuntu - dual boot[/COLOR]**[/B][/B][/FONT][/SIZE][SIZE=2][FONT=times new roman]**[B][B]**[/B][/B][/FONT][/SIZE][/h][/B][SIZE=3]**[h=1][FONT=times new roman][B][B][B]**[/B][/B][/FONT][/h][h=1][FONT=times new roman]**[B][B]**[/B][/B][/FONT][/h][h=1][FONT=times new roman]**[B][B]**[/B][/B][/FONT][/h][h=1][FONT=times new roman]**[B][B]**[/B][/B][/FONT][/h][h=1][FONT=times new roman]**[B][B]**[/B][/B][/FONT][/h][h=1]**[B][B]**[/B][/B][/h][FONT=times new roman][COLOR=#000000]
Most of these parts are not completely set yet, a lot of them may change a bit, but that is the basic specs of what my computer is going to be like. If there are any suggestions for the parts, feel free to tell me as well. I am probably going to start ordering the parts and this stuff in about a week.

Thank you for your help! [/COLOR][/FONT][FONT=times new roman]
[/FONT][/B][/SIZE][B]

[/B]

---

### Post by oldfred on 2013-05-16
You will have to decide if you want the new UEFI with gpt partitionging. Or the 30 year old but well known BIOS with MBR(msdos) partitioning.

Windows only boots with UEFI from gpt partitioned drives.
Ubuntu will boot from gpt partitioned drives with either BIOS or UEFI.

       GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

How you boot both Ubuntu & Windows flash drive installer either UEFI or BIOS is then how it installs. Both Windows & Ubuntu have to be the same either both UEFI or both BIOS.

      
  You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI.
Install Windows efi to new drive.
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx]("http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx")
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB](https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB)

      
 You will need to use the 64 bit version of 13.04, 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need Windows  fast start up (hibernation) and UEFI/BIOS fast boot quick boot UEFI settings. Vital for some systems. 
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive. Reboot after shrink so it can run its repairs to its new size.
Backup efi(ESP) partition and Windows partition before Install of Ubuntu. Only one efi partition per hard drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI. 
One user posted this which you probably need to do for those systems that only boot Windows with secure boot on:
> The key was to launch into Window 8 with secure boot enabled then choose Restart in Windows 8 selecting USB as the device to restart on. 
This is really strange since the big breakthrough was being able to run Boot Repair launched in "secure boot" mode and checking the "Secure Boot" checkbox in Boot Repair before running it.

---

### Post by Impavidus on 2013-05-16
Good you want win7. Win8 can be a lot more complicated to set up a dual boot.

Concerning that graphics card, have a look at this thread: [http://ubuntuforums.org/showthread.php?t=2054617](http://ubuntuforums.org/showthread.php?t=2054617)
It seems to work well with Ubuntu, although in general nvidia seems more dependable concerning driver support.

---

### Post by fantab on 2013-05-16
> **Impavidus said:**
> Good you want win7. Win8 can be a lot more complicated to set up a dual boot.

Win8 is not complicated to set-up as dual boot if you are installing it yourself. Its the OEM pre-installed Win 8 which is PITA.. with 'Secure Boot' and what not.

@**dragonzoid2001**: Double the Memory/RAM if you intend to use your machine for gaming. Also, consider adding a 100GB+ SSD (if budget is not really a constraint). You can boot both Windows and Ubuntu a lot faster from SSD. 

My two cents...

---

### Post by dragonzoid2001 on 2013-05-16
**@oldfred**: Thanks for the help, but how would you recommended the partitioning of the system? Like how many partitions should I make, and how large should they be? I saw a few guides online but a lot of them were for harddrives around 80-100GB. I don't know if I should follow the sizing of these guides or allot more space in them for windows and linux. Some guides recommend  3 partitions, but others recommend at least 4.

@**Impavidius: **I looked into Nvidia as well, but the prices seem quite a bit higher then radeon, I compared two of them that seemed around the same performance level (GTX 660) and it seemed that the 7870 had higher performance for a cheaper price. A few reviews that I stated said that it worked fine for Ubuntu on the experimental driver so I'll probably try it out. Most of my graphic intensive stuff (games -.-) will probably be using windows anyways. Or am I missing something?

@**fantab:** Is 8 of RAM now enough for games now? I wasn't planning to do any intense video encoding or anything like that at the moment. I have a laptop with 8gb of RAM at the moment and the limitation for high-end games is the fact that my laptop will overheat very often and will crash. For the SSD drive, I was considering it, but I'll need to check if it can fit in my budget. SSD drives are cheaper then before, but are still very expensive -.-.

Also, some guides recommend that I install windows before installing ubuntu, is this valid? I'm not worried to much about wiping memory since the hard drive will be completely empty.

Thanks for the help everyone!

---

### Post by oldfred on 2013-05-16
Your have your system partition for both Windows & Linux. I tend to prefer smaller system partitions for both and separate larger data partitions. Since both Windows & Linux read NTFS then a large NTFS data partition when dual booting is best. Windows just does not seem to like a lot of writes into its system partition from other systems even dual boot with two Windows or it is users modifying something that should not be.

But depending in UEFI or BIOS you need extra support partitions. Windows in BIOS mode normally installs another boot/repair partition. In UEFI it have several.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

So it is usually best to install Windows first and let it do its own thing. But only shrink Windows using Windows disk tools, but do not create partitions with Windows as it may convert to dynamic partitioning which does not work with LInux.

My standard suggestion. But you have to decide how you use system. Some want lots of space for data, some may want extra 10 to 25GB partition or two to experiment with another system, or other uses. If UEFI you wil have gpt partitioning. If BIOS you cannot have the gpt partitions. My standard suggestion:


 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB bios_grub no format (for BIOS boot not required for UEFI)
gpt or MBR(msdos)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by Impavidus on 2013-05-16
It's best to double-check driver support for video, but I think this one will be fine.

---

### Post by fantab on 2013-05-16
> **dragonzoid2001 said:**
> **@oldfred**: Thanks for the help, but how would you recommended the partitioning of the system? Like how many partitions should I make, and how large should they be? I saw a few guides online but a lot of them were for harddrives around 80-100GB. I don't know if I should follow the sizing of these guides or allot more space in them for windows and linux. Some guides recommend  3 partitions, but others recommend at least 4.
....
@**fantab:** Is 8 of RAM now enough for games now? I wasn't planning to do any intense video encoding or anything like that at the moment. I have a laptop with 8gb of RAM at the moment and the limitation for high-end games is the fact that my laptop will overheat very often and will crash. For the SSD drive, I was considering it, but I'll need to check if it can fit in my budget. SSD drives are cheaper then before, but are still very expensive -.-.

I just suggest more RAM because you said you 'game' "quite a bit". I would have gone with 16gigs RAM considering how resource hungry some modern  games can be. I guess it also depends on what games you play.

This is how I paritioned my Bro's HDD when I installed Windows and Ubuntu: (This for BIOS, NON-UEFI Boot with 'msdos' partition table). 
100 GB Windows Primary NTFS C: (considering that you will be installing games adjust appropriately, note that Windows C: should have atleast 25% free space after you install everything to perform at its best).
30 GB Ubuntu Primary EXT4 "/" (I don't use separate /home, so Home Folder (where you store your DATA is created within "/". We use separate DATA partition for the same purpose. see below.)
30 GB Free Primary Ext4
_all the remaining GB_ EXTENDED (Extended Partition is Primary Partition that contains several LOGICAL Paritions). Four Primary Partitions is the Limit with 'msdos' table so we create the fourth partition as Extended.
2-4GB Linux SWAP (If you like to Hibernate your PC then SWAP size should be equal to or greater than your RAM in GiB not GB)
_all the remaining GB_ LOGICAL NTFS (to share data between Windows & Ubuntu). If you want you can create more Logical Paritions.

---

### Post by Jerry N on 2013-05-16
I suggest two hard drives, one for Windows and one for Linux.  Drives are cheap!  During OS installation, I have only one hard drive connected at a time.  When both drives are connected and Ubuntu is running, it will find Windows and provide it as a boot choice.  Partition an area of the Windows drive for backup of Linux files and partition an area of the Linux drive (NTFS) for backup of Windows files.  If your Windows drive fails, Linux will still boot just fine and you will have a backup of the Windows files.  If the Linux drive fails, you can still boot Windows.  I have done this kind of setup numerous times.  One of my computers can boot several versions of Linux (all on the same drive), Windows 7, and Windows XP.

Remember when it comes to keeping backups of your important files, paranoia is a virtue!

Jerry

---

### Post by dragonzoid2001 on 2013-05-22
Thanks for the help everyone, I just finished my finals -.- And now I'm looking at the parts and I'm about to order them. There are a few spec changes, I'm getting a 2TB harddrive along with 16 of RAM now. I was planning to put around 300 GB for Windows. Considering I have only used 250~ish of my current memory with all my files and stuff, I felt that would be more than enough. Some of my friends recommened me put 64GB in the swap partition. I have plenty of space so I was planning to a be a bit more generous with the memory distribution (I can always stick another hd in if I run out of space, which is unlikely). Thanks in advance!

---

### Post by Impavidus on 2013-05-22
Swap space four times as large as your RAM sounds insane, but if you don't need the disk space anyway you're free to do so. It's still only 3% of the drive. I've never filled a hard drive either.

---

### Post by holycow131415 on 2013-05-22
64gb of swap is overkillin it. 16gb or 32gb is good.

> As a base minimum, it's highly recommended that the swap space should be  equal to the amount of physical memory (RAM). Also, it's recommended  that the swap space is twice the amount of physical memory (RAM)  depending upon the amount of hard disk space available for the system

[https://help.ubuntu.com/community/SwapFaq#How_much_swap_do_I_need.3F](https://help.ubuntu.com/community/SwapFaq#How_much_swap_do_I_need.3F)


Also, I suggest just making a ntfs partition for you to put your files on so that you can easily access it between windows and linux.

---

### Post by dragonzoid2001 on 2013-05-30
Hello everyone again, so I recently got most of my parts in, I'm about to get my windows 7 from my school. I was wondering if I should use Ubuntu 12.10 or 13.04? Also, the final specs will be i5-3570k ivy-bridge, Radeon HD 7870, 16 GB of RAM, and 2 TB of memory. I was planning to have at ntfs partition for all my shared files. I was planning on having 250 GB of memory for my windows, do you guys think it will be enough? I will have maybe 4-5 games that's about it. I'm still having some trouble finding out how many partitions I should have in total. I will have 
1 ntfs partition - everything else, 
1 windows partitition - 250 GB, ... then Ubuntu which at the moment I have 
swap - 32 GB, 
home - ?, 
root - ?, 
/ -?.
By the way, I have 2 TB, and I can add more later if I run out, so don't need to worry about being stingy with space. Thanks for the help >.< First time using Linux and I'm completely lost X(

---

### Post by Impavidus on 2013-05-30
The root partition and the / partition are the same thing. It's mounted at /, but talking about / is a bit inconvenient so we often call it root. This is not the directory /root, which has to be on the / partition too.

Concerning your windows partition, I've got no idea how disk space hungry your 4-5 games are, but I think most will be happy with a few GB. Then the size of your /home partition and your ntfs data partition, they more or less fulfil the same purpose. The difference is that the ntfs partition is usable from windows, whilst the /home partition is easier for linux use. It all depends on how much data you want available in windows. If you just need windows for 4-5 games, whose data you don't have to share with Ubuntu, and some office files, it may be most convenient to have a large /home. If you think it will be convenient to share almost everything, you can make a very large ntfs partition and keep /home on the / partition, not making a /home partition at all. This may be the case if you have a large media collection.

If you make a separate /home partition, you can make / about 15-30GB.

---

### Post by fantab on 2013-05-30
With a 2TB HDD I suggest you go for GPT partition table and set up UEFI BOOT, if you BIOS supports it. I am sure it will.

With UEFI and GPT you will need:

250-300MB FAT32 with a Boot-Flag (This is where your EFI boot info will be stored). This HAS to be your first partition.
100GB NTFS (For Windows System Files). We are not making any space for DATA here. Just the system files and other software/games installation files.
???GB NTFS (DATA partition shared between Windows and Ubuntu)
---------------------------------------------------------------
30GB Ext4 / (This is where we will install Ubuntu system files and software)
30GB Ext4   (Free space, just in case you want to try/use another GNU-Linux distro or some other Ubuntu version or flavor)
4GB SWAP (Only and only if you plan to 'Hibernate' Ubuntu then the SWAP MUST be equal to or more then your RAM in GiB, not GB. In your case 16GiB. Anything more than this is wasted).
???GB Ext4 (DATA) You can use this to back up your important DATA. I don't trust NTFS with my DATA much.

No need of separate /home if you have Shared DATA partition + an Ext4 partition to save your DATA.

---

### Post by dragonzoid2001 on 2013-05-31
Thanks for the replies, I finally received the last of my parts and am about to install Windows and Ubuntu shortly, I've seen a number of guides on how to partition the HDD, but I've been having a lot of trouble finding one for a clean install. Should I install windows first and follow one of the windows installed already guides? 
For now, the parititioning looks something like this,
/boot - 1 GB - (It was recommended this was between 250 MB - 1 GB, and since I have space to spare, and more to add if I need it, I decided to just give it 1 GB to be safe.
home - 30 GB - (Still not exactly sure what this is for but some state that this optimizes the file retrival?)
swap - 16GB (so I should reduce this to 16?)
root - 30GB - (Almost everyone recommends me allot 30 GB to this, should this be bigger? I've only ever used Windows and 30 GB seems so small -.-)
NTFS - file sharing (probably around 500 GB or more depending on how much space I have left)
Windows 7 - 250 GB

With all this it still only uses about 1 TB, so NTFS might be 1 TB and the root and home, and maybe windows may be bigger, I'm sorry for being so troublesome >.<, another question, I have never actually partitioned HDD's before, and there are a few guides that don't really help me that much. A lot of them start assuming that the partition is completed or with Windows already installed. So if I want to partition the system before windows how do I do this? And how do I select what type this partition will be. 

I also read that the ubuntu should be in one partition with extended logical partitions? Is all the partitioning done in the same area? I also saw multiple mentions on the UEFI boot, is there somewhere where I can find a comprehensive guide to partitioning or something like that? I've been searching around google and I've been having a lot of trouble finding one. I'm sorry for the long post and the trouble.

---

### Post by Impavidus on 2013-06-01
/ – 30GB: There's a reason why everyone tells you it's enough: It really is. I've no idea how Windows manages to fill more than 10GB.
swap – 16GB: But make sure that is really 16GiB=17179869184 bytes, not 16000000000 bytes. That's the difference between GiB and GB.
/boot – 1GB: If you wish. I don't have a /boot myself. Some older systems with big drives or systems on encrypted partitions may need it.
/home – 30GB: The idea behind /home is that it's easier to reinstall, keeping all your documents and settings (although those settings aren't always compatible with the new version after reinstalling). It's generally recommended, but on small installations not really necessary as copying to and from backup drives is fast on small partitions. Having a small separate /home partition may lead to the problem that on one day your /home may be 90% filled, with your / only 20% filled. To avoid that problem small installations (root + /home = 60GB is small) often don't have a separate /home. But if you decide to make your /home bigger (100GB or so), it is wise to make it a separate partition.

When you've put your computer together you can boot from an Ubuntu live disk. First play around a bit and be amazed by the speed of your new system, than open the program gparted and create all partitions from scratch. It's a nice graphical program providing you with a graphical view of the disk. It's not difficult and as there're no files yet on the drive you can't damage anything. When ready, reboot from a Windows install disk and instruct it to install on the ntfs partition you just created. After you get Windows up and running (maybe reboot a few times, so that Windows can do some system checks and updates to get everything stable), boot again from the Ubuntu live disk and install Ubuntu, using manual partitioning and pointing it to the partitions you created for it.

Doing it this way is definitely easier than first installing Windows to the entire drive, then resizing it and putting Ubuntu next to it.

One additional note: The Ubuntu installer will ask you about encryption. Use it wisely. It can prevent your sensitive data from coming into stranger's hands when your computer gets stolen, but also makes file recovery in case of file system damage or forgotten passwords nearly impossible.

---

### Post by fantab on 2013-06-01
SWAP-16GIB ONLY if you intend to HIBERNATE your Ubuntu. Otherwise 4GB is plenty.

I reiterate and recommend GUID partition Table [GPT] with UEFI BOOT. This is the future. With UEFI boot you don't need /boot.

---

### Post by dragonzoid2001 on 2013-06-01
I'm currently trying to install Ubuntu after installing windows in a UEFI format. When I made the windows it made 3 partitions, but I've been looking through a lot of guides and trying to do the UEFI boot, but I can't find any guides that can help me out with this. I'm currently at the Ubuntu table, I have 1 MB of free space in front of everything, my sda1 (fat32) - 104.9 MB, sda2 (unknown) - 134.2 MB, sda3 (ntfs)-314.3 GB. I have around 1.7 TB of free space left.

---

### Post by fantab on 2013-06-01
I hope you have installed correctly with UEFI: [http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)

Ubuntu install after that is simple. Just choose "Something Else" option when the Installer takes to "Installation Type". Choose your partition where you want to install Ubuntu, click 'CHANGE' then USE AS= Ext4, Mountpoint=/ select format. If you have created space for separate /home then selec that partition, USE AS=Ext4, Mountpoint=/home format. If you have already created SWAP then you don't have to do anything. Continue with Installation and Reboot when asked to.

If you have problems booting later then use "[BOOT-REPAIR]("https://help.ubuntu.com/community/Boot-Repair")".

---

### Post by dragonzoid2001 on 2013-06-01
Thanks, I made those partitions now, and I chose the sda1 for the bootloader, is that right? I put around 17GB for the swap, did the conversion from 16GiB. I made a root and a /home with both sitting at 30 GB at the moment. I couldn't find a place to create a shared NTFS though, so I'm still sitting at about 1.5-1.6 TB of free space -.-lll. I hope I did this correctly, but... well... if it doesn't work I'll just start over >.>.

---

### Post by fantab on 2013-06-01
No. Don't install Ubuntu boot loader to /dev/sda1 this is your first partiion, default will be /dev/sda, the HDD. Keep it default.

To install Ubuntu in UEFI mode you need to boot Ubuntu DVD/USb in UEFI mode. If you see a 'black' screen with Try Ubuntu etc... then you are booting in EFI mode but if you see a Purple screen then you are not. 

Your misconception of 30GB /home beats me. Atleast make it 100GB. /home is where your Documents, Pictures, Videos and Music etc will be stored. Do you think 30GB will be enough for you?

Any NTFS partition can be shared between Ubuntu and Windows. There is no 'different' shared NTFS.

Good Luck...

---

### Post by dragonzoid2001 on 2013-06-01
I did use that exact tutorial when I installed Windows 7, is there a specific order in which I had to create the partitions? My windows is installing a ton of updates right now but when I booted up just now GRUB did not come up at all. So I should try the boot-repair from the Ubuntu USB?

---

### Post by fantab on 2013-06-01
Check the UEFI boot menu in BIOS.. see if there is an option to boot Ubuntu. If yes, select it and boot. If it shows a menu then you are good. If not then use Boot Repair...

NO. It doesn't matter how you order your partitions. However, if I were you I would keep All my NTFS one after another and then Ext4 and SWAP, just for neatness.

---

### Post by dragonzoid2001 on 2013-06-01
I tried doing what you told me but it still won't boot, I have reinstalled Ubuntu with 100 GB as /home and 30 Gb as /root as well as 16GiB for the swap. It didn't work, so I used the boot repair by running it off the USB. But it still doesn't work. What else can I do about this?

---

### Post by dragonzoid2001 on 2013-06-01
This is what I see right now with my partitioning 
free space 1 MB
sda1(fat32) -104.9 MB
sda2(unknown) 134.2 MB
sda3(ntfs) 314.3 GB
sda4(ext4) 100 GB
sda5(ext4) 30 GB
sda6(linux-swap) -17.2 GB
free space - 1.5 TB

---

### Post by Impavidus on 2013-06-01
> **fantab said:**
> 
Any NTFS partition can be shared between Ubuntu and Windows. There is no 'different' shared NTFS.

Except that using Ubuntu to write the the partition where Windows is installed may not be save. Writing to any data partition is fine.
> **dragonzoid2001 said:**
> I tried doing what you told me but it still won't boot, I have reinstalled Ubuntu with 100 GB as /home and 30 Gb as [color=#ff0000]**/root**[/color] as well as 16GiB for the swap. It didn't work, so I used the boot repair by running it off the USB. But it still doesn't work. What else can I do about this?
Do you mean you made a partition mounted at **/root**? I think you are confused. The **/** partition and the **root** partition are used as synonyms here, refering to the place where the system is installed. It's where you find the OS and where you can find the locations where all other partitions are mounted. **/root** on the other hand is just a directory in the root partition. It cannot be in a partition of it's own.

However, I don't think that causes your current problem.

Did boot repair give you a link to a summary, describing your current system? Could you post that link? It may help avoid confusion.

---

### Post by dragonzoid2001 on 2013-06-01
I have got it to work, but in Grub there are 4 options, are there supposed to be 4?
Ubuntu
Advanced Options for Ubuntu
Windows UEFI bkpbootmgfw.efi
Windows Boot UEFI loader

This is the boot-repair link if you still need it.
[http://paste.ubuntu.com/5723892/](http://paste.ubuntu.com/5723892/)

Another thing, Ubuntu is feeling kind of slow and sluggish at the moment, I am updating the software and stuff, but it will get better right? o.O

---

### Post by dragonzoid2001 on 2013-06-01
Thank you for your help everyone! I got the dual booting to work! I'm going to go familiarize with thisnow. Thanks for the help!

---

