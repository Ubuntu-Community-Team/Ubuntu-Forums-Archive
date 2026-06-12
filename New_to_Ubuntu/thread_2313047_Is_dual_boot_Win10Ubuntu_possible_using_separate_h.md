---
title: "Is dual boot Win10/Ubuntu possible using separate hard drives?"
date: 2016-02-09
forum: New to Ubuntu
---

### Post by snowpaw on 2016-02-09
My PC has 2 separate hard drives installed in it.   I have Windows 10 currently installed on a 450 Gb SSD.   I would like to install Ubuntu on a separate 128 Gb SSD and be able to choose to use either one or the other on dual boot.  I am brand new to Ubuntu.  In fact, I have not downloaded or installed it as yet.   So, one I would like to know if this dual booting from separate hard drives is possible.

---

### Post by yancek on 2016-02-09
Yes, it is possible.  Since you have windows 10 I would suggest you read the link below regarding booting using UEFI so you understand it.  Post back with questions and give more details on your hardware when you do.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by grahammechanical on 2016-02-09
> I would like to know if this dual booting from separate hard drives is possible.

Of course, it is. I would say that it is the better way. But there is a need for preparation and in the case of Windows 8 - 10 we need to understand this

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

So, become familiar with the UEFI boot system utility. The machine should have come with a motherboard user guide that explains all about it.

Regards.

---

### Post by oldfred on 2016-02-09
Or is your Windows 10 an upgrade from Windows 7 and then still BIOS with MBR partitions.

Whichever you want to be sure to install Ubuntu in same boot mode UEFI or BIOS as Windows is installed.
And best to use gpt partitioning on Ubuntu drive. Include an ESP - efi system partition even though with UEFI grub only installs to the ESP on sda.

       It is recommended to use always GPT for UEFI boot as some UEFI firmwares do not allow UEFI-MBR boot.

   For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 15-25 GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[URL="http://ubuntuforums.org/showthread.php?t=2170308"]http://ubuntuforums.org/showthread.php?t=2170308

      [/URL]
 UEFI install,windows 8 with Something Else screen shots (10 should be the same) But does not show selecting second drive.
[URL="http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html"]http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html
[/URL]
 Something Else install, but prefer larger / of 20 or 25GB. Not showing Windows
[http://www.tecmint.com/ubuntu-15-04-installation-on-uefi-firmware]("http://www.tecmint.com/ubuntu-15-04-installation-on-uefi-firmware/")  [ ]("http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html")      [ ]("http://ubuntuforums.org/showthread.php?t=2170308")

---

### Post by snowpaw on 2016-02-09
Thank you for your replay.  I will read the link and get back if I have questions.  New hardware will be MSI MSI Gaming Z170A XPOWER GAMING TITANIUM EDITION LGA 1151 Intel Z170 HDMI SATA 6Gb/s USB 3.1 ATX Intel Motherboard and Intel Core i7-6700K 8M Skylake Quad-Core 4.0 GHz LGA 1151 91W BX80662I76700K Desktop Processor Intel® HD Graphics 530, and some RAM of course.  My plan is to install Win 10 first, and get that up and running along with Word etc so I can copy and print.  When all that is stable, I will install Ubuntu.  I want to basically use Windows to game, and hopefully Ubuntu for almost everything else once I begin to learn it.  Thank you gents!

---

### Post by oldfred on 2016-02-09
Some other MSI threads:

 Z170 chipset compatibility - Dec 2015
[http://ubuntuforums.org/showthread.php?t=2306715](http://ubuntuforums.org/showthread.php?t=2306715)
Best Ubuntu version for new Z170 motherboards /w Intel video? Oct 2015
[http://ubuntuforums.org/showthread.php?t=2292521](http://ubuntuforums.org/showthread.php?t=2292521)
MSI Z170A GAMING PRO motherboard
[http://www.phoronix.com/scan.php?page=article&item=msi-z170a-gaming&num=1](http://www.phoronix.com/scan.php?page=article&item=msi-z170a-gaming&num=1)
[http://askubuntu.com/questions/705796/msi-z170a-gaming-m5-with-linux-dual-boot](http://askubuntu.com/questions/705796/msi-z170a-gaming-m5-with-linux-dual-boot)

---

### Post by snowpaw on 2016-02-12
Thank you for your replies.  I have Windows 10 pro (full version-not upgraded) on a 450 Gb Sandisk SSd.  My motherboard is a MSI Z170A Xpower gaming titanium edition.  My CPU is intel core i7 6700K.  I used UFEI to boot the OS on to the drive.  Right now, the 450 Gb SSD drive is partitioned as follows: (450 Mb- Healthy-recovery partition) + (100 Mb Healthy-EFI system partition) + (446 Gb NTFS Healthy-Boot, Page File, Crash Dump, Primary partition)  Those are the partitions I am looking at for my Windows 10 OS.  My second SSD is roughly 120 Gb and not even formatted yet.  My goal as stated above is to be able to dual boot both Windows and Ubuntu, but have each OS on separate SSD drives.  I also have a DVD disk I have downloaded Ubuntu on to.  My first question is on the 450 Gb SSD, is the 100 Mb partition the boot partition or the 446 Gb partition the boot partition?  I know I have to boot the DVD as UEFI.  But I could sure use some guidance on which partition to boot the dvd into, and then how to actually put the Ubuntu OS on the separate drive.  Thank you so much.

---

### Post by westie457 on 2016-02-12
Re: the 450Gb SSD, the 100Mb partition is the boot partition for Windows 10. Windows 10 should have formatted this as FAT32 on a drive with a GPT partition-table. This partition is also the one Grub will be installed to whichever drive you put Ubuntu on.

Re: booting the DVD, I am not certain it will boot in UEFI mode. If it does you will get a screen with a four lines of text on a blank screen, a screen with a splash image means it is booting in non-UEFI mode.
It will probably be better if you can use a USB stick to boot from to get the screen with the text.

Line one is 'Try Ubuntu'
Line two is 'Install Ubuntu'
Line three is 'OEM Install' (no idea what that does, never used it)
Line four is 'Check for Defects' (or something similar)

Take the first one to check that things work. eg. Wireless network, Graphics card. Have an ethernet cable handy just in case.

When you are happy while in 'Try mode' click on the 'Install' icon.
After a few moments you should get a welcome screen. This will have a list of languages on the left side, highlighted should be the language of your location, click 'Ok/Continue' then in the next window select the keyboard layout for your location.
The screen after this one asks you 'How would you like to install' with some options. Choose the 'Something Else' option otherwise things could go wrong and accidentally wipe everything.

After clicking for 'Something Else' you should get a window showing your current drives and partitions. If you can only see the 450GB drive STOP. Post back here and we will attempt to get the 120GB drive recognised. 

Partitioning is down to personal choice so these are suggestions only.

partition 1 > 20-25GB, this will be /Root
partition 2 > 2GB, this will be Swap
partiton 3 > the remainder, this will be /Home.

Another suggestion is for the Windows drive using Windows tools to create a separate partition/drive to use as a common Data area.

Any more questions feel free to ask.

---

### Post by oldfred on 2016-02-12
Even though grub always installs to the drive seen as sda with UEFI, I still like to have and ESP - efi system partition on every drive. And if it installs to sda, I copy /EFI/ubuntu to the ESP on sdb. While not normally used, if sda fails for any reason I may be able to still boot sdb as sda. It works easier with BIOS.

Use gpt & include at least the ESP on your Ubuntu drive. I normally have both ESP & bios_grub, so I could also change boot mode. 
 I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....


 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25 GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
s

---

### Post by snowpaw on 2016-02-12
When I was playing around with Fedora, I had good luck with the DVD install and very bad luck with creating the Install USB.  I had the USB formatted in FAT32, and I think I just downloaded the Fedora file directly to the USB.  I am not sure what went wrong.  Is that what I need to do to, create a USB install disk?  Just download Ubuntu directly to it, after formatting it to fat32?

---

### Post by snowpaw on 2016-02-12
The 120 GB drive intended for Ubuntu.  Will the installer allow me to partition the drive prior to installing?  Or should I partition it with windows prior to install?

---

### Post by yancek on 2016-02-12
Downloading an iso file of Ubuntu/Fedora or any other Linux will not make it bootable.  It just won't work.

You can partition and format with the Ubuntu installer or with GParted which is also on the Ubuntu install medium before beginning the install.  Better to do either.  You can create partitions from windows but that is kind of pointless because you will have to format anyway and windows is not capable of doing that.

---

### Post by oldfred on 2016-02-12
The standard installers do several things, format flash drive (erasing it) as FAT32, extracting the ISO, and installing a BIOS boot loader. The extraction of the ISO includes a efi folder & UEFI boot file.
It is possibly to manually format and use any extraction tool to create an UEFI only bootable flash drive.
UEFI will normally offer to boot standard flash drives in either UEFI or BIOS mode. And how you boot installer is then how it installs.

Best to use Windows for Windows repairs and Linux tools for Linux repairs.
Or do not attempt to use Windows to create Linux partitions. In some cases that can create difficult to repair systems.
I prefer to partition in advance with gparted, but you can partition during install with Something  Else. Any time you have multiple drives you do need to use Something Else not any auto install option.

---

### Post by snowpaw on 2016-02-13
> **westie457 said:**
> Re: the 450Gb SSD, the 100Mb partition is the boot partition for Windows 10. Windows 10 should have formatted this as FAT32 on a drive with a GPT partition-table. This partition is also the one Grub will be installed to whichever drive you put Ubuntu on.

Re: booting the DVD, I am not certain it will boot in UEFI mode. If it does you will get a screen with a four lines of text on a blank screen, a screen with a splash image means it is booting in non-UEFI mode.
It will probably be better if you can use a USB stick to boot from to get the screen with the text.

Line one is 'Try Ubuntu'
Line two is 'Install Ubuntu'
Line three is 'OEM Install' (no idea what that does, never used it)
Line four is 'Check for Defects' (or something similar)

Take the first one to check that things work. eg. Wireless network, Graphics card. Have an ethernet cable handy just in case.

When you are happy while in 'Try mode' click on the 'Install' icon.
After a few moments you should get a welcome screen. This will have a list of languages on the left side, highlighted should be the language of your location, click 'Ok/Continue' then in the next window select the keyboard layout for your location.
The screen after this one asks you 'How would you like to install' with some options. Choose the 'Something Else' option otherwise things could go wrong and accidentally wipe everything.

After clicking for 'Something Else' you should get a window showing your current drives and partitions. If you can only see the 450GB drive STOP. Post back here and we will attempt to get the 120GB drive recognised. 

Partitioning is down to personal choice so these are suggestions only.

partition 1 > 20-25GB, this will be /Root
partition 2 > 2GB, this will be Swap
partiton 3 > the remainder, this will be /Home.

Another suggestion is for the Windows drive using Windows tools to create a separate partition/drive to use as a common Data area.

Any more questions feel free to ask.

Thank you for your help.  Here is what I did.  I installed 2 more hard drives on my PC.  First one was the 128 Gb SSD I mentioned before.  I also installed a 2 Tb HDD.  It seems a bit big, but I didn't want to have to go out and buy one.  My BIOS allowed me boot using my DVD as UEFI, so I used it.  First thing I did was check the DVD for errors and it came back with "no errors".  Then I selected "Try Ubuntu".  The graphics look fantastic.  I also connected to the Internet using my wireless connection without a problem.  From there I went to "Install Ubuntu", and then to "something else", which led me to my disks .  I played around with that, and found I have some questions.  So I backed all the way out, and came here to ask them.
This is what I was looking at:
/dev/sda
free space     2000398 Mb                                        This is my 2 Tb unformatted HDD

/dev/sdb
free space     1Mb
/dev/sdb1     ntfs          471 Mb             316 Mb (used)    I think this is the Windows Recovery Partition.
/dev/sdb2     efi            104 Mb               33 Mb (used)    Windows boot manager
/dev/sdb3                     16 Mb               unknown           I have no clue what this is.
/dev/sdb4     ntfs          479508 Mb       62952 Mb (used)  This would be my Windows C: 
free space                     0 Mb

/dev/sdc
free space                    128035 Mb                                This is my unformatted 128 Gb SSD

For the "Device For Boot Loader Installation"  I chose, /dev/sdb2  Windows Boot Manager
Next I attempted to partition the 2 Tb HDD.  (I decided that is where I will put Ubuntu)
I saw how to create the swap file, which does not require a mount point.  Since I have 16 Gb of RAM, I thought I would use 16Gb for the swap.
And I could see how to choose the mount points for root and for home.  But the "Use As" completely baffled me.  I had no idea what to choose for root or home.
My choices are:
Ext 4           Journaling File System
Ext 3           Journaling File System
Ext 2           File System
btrfs            Journaling File System
JFS              Journaling File System
XFS             Journaling File System
Fat 16         File System
Fat 32         File System
Swap Area
Reserved BIOS boot area
EFI Boot Partition
Physical Volume for Encryption
Do Not Use this Partition

Questions:  Is /dev/sdb2 the correct device for my boot loader installation?
                 Do the partitions need to be created in any specific order?  Such as Root, Swap, and finally Home
                 For the Root and Home partitions, what do I select for the "Use As" window?
                 Seeing as how I have 2 Tb here, do you have suggestions on the partition sizes?
                 And would you recommend creating partitions in addition to the Root, Swap, and Home?  (keeping in mind I am a total noob, and don't want to mess myself up on doing updates an such)
                 And last, you suggested creating a separate partition on the windows drive to use as a common Data area.  Do you have a link or a little more info on that?  I can create the partition, but I                would have clue on how to configure it as a common data area. 

Again, thank you for all your help.  I am looking forward to your reply.  I am getting close!  (I think, lol)

---

### Post by yancek on 2016-02-13
sdb2 looks like your EFI partition so if you have EFI with windows, I believe that would be good.  Might wait for oldfred or someone else to confirm as I'm basing this on what I've read and don't use UEFI.  The Use as option is the filesystem type and the simplest choice is the Ubuntu default of "Ext4 Journaling File System".

I'd suggest you not concern yourself with additional partitions until you are more familiar with the system.  They are certainly not needed.
If you have 16GB of RAM, you probably will never need swap but since you have a large drive...

---

### Post by snowpaw on 2016-02-13
I thank you for your help, and your advice.  I had no clue what might be the default.  I think I will try to wait for oldfred or Westie457.  I am looking forward to Ubuntu.

---

### Post by oldfred on 2016-02-13
I like to have an ESP - efi system partition on every drive. And I actually have an install on every drive, just as backup or testing.

But with UEFI grub will only install to the ESP on sda. If blank hard drive is sda, it may error out on install. One other user could not get it to install grub until he had an ESP on sda.

Windows is now on sdb, often better to keep it on sda. Drives are usually seen in SATA port order. I also found not to leave or skip a SATA port or have DVD in middle of drives. Then drive order in Booting and grub is confused if you have to manually specify a drive.

Standard format for Linux partitions is ext4. But you may also want extra NTFS partitions which you cannot create during install, but can use gparted from live installer before or after install as long as you leave some unallocated. I still have not fully partitioned either my SSD nor 1TB HDD from a year ago.

You can use separate /home which is easier for newer users as you are owner and have permissions. I prefer a /mnt/data which you cannot create during install and have to manually set up mount, ownership & permissions.

How partitions you want or need is personal. But I find my own optimal partition plan changes in several years, but I do not trust a drive for more than a few years no matter warantee period. But then I repartition a new drive.

Several suggestions as a starting point.
 It is recommended to use always GPT for UEFI boot as some UEFI firmwares do not allow UEFI-MBR boot.

   For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25 GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB Mountpoint /home logical beginning ext4 
[*]2 GB Mountpoint swap logical 
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
[http://askubuntu.com/questions/461394/how-to-partition-ssdhdd](http://askubuntu.com/questions/461394/how-to-partition-ssdhdd)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/581902/how-to-efficiently-partition-a-single-windows-ubuntu-dual-boot-disk](http://askubuntu.com/questions/581902/how-to-efficiently-partition-a-single-windows-ubuntu-dual-boot-disk)

   Oldfred's current partitions Dec 2015
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

---

### Post by snowpaw on 2016-02-13
I used /dev/sdb2    efi  Windows boot manager as "device for boot loader installation.  I created root (50 Gb), then swap (16 Gb), and finally home.  (500 Gb)  The rest of the disk I used "do not use this partition".  As per advice, I used Ext 4 Journaling file system for the "Use as" choice for the root and home partitions.  Everything installed and worked without a hitch. I have Windows 10 Pro installed on one SSD and Ubuntu installed on another HDD.  I can now boot either Windows 10 or Ubuntu from the boot up screen. A sincere **Thank you** to everyone who helped me get this done.

---

### Post by sunil16 on 2016-02-14
yes you can use two hard drives to dual boot all you need to do is partitioning separately while installing ubuntu choosing something else then 
The standard partitions scheme for most home Linux installs is as follows:
 
[LIST]
[*]A 12-20 GB partition for the OS, which gets mounted as / (called “root”)
[*]A smaller partition used to augment your RAM, mounted and referred to as swap
[*]A larger partition for personal use, mounted as /home
[/LIST]

---

