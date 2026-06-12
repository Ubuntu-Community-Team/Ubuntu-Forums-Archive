---
title: "Failed Grub install in Natty Narwhal"
date: 2012-06-30
forum: New to Ubuntu
---

### Post by E-Tramp on 2012-06-30
OK, I have a new thread here for the installation of Natty Narwhal. I just installed the program and in spite of wanting to install manually, I wasn't familiar with the way the program installed so ended up with it actually doing an auto install that thankfully installed it in the unformatted space adjacent to my Windows 7 program as intended, however, and this is to Jim Kyle, the automatic installation only put two partitions in an extended drive and appearantly the grub didn't install so there is no access to the program now that it is there.  Also, the Swap file is actually 26 GB, I wonder if that is because my RAM is 24 GB, because I know that swap files in Windows are suppose to be as much or more than the RAM in size. 

I spent the whole installation sweating whether the program would screw up all of my work yesterday installing Windows, but, for the most part it went better than I expected.  I really hate doing things blind like that, they really need a much more user friendly way of doing it manually.

So, now, what should I do about this installation?  Think I should just start over, and install something different?  The installation program seemed to think that the some of the disk files were corrupted and that is why they couldn't install some of the software.  Maybe a good time to download and install Xubuntu to see what it will do.

---

### Post by jmfal on 2012-06-30
If you can boot into ubuntu you have grub, it's just thwt you are not seeing it, restart and select ubuntu from the boot menu, then hold down the shift key,
That should get you to the grub screen.
24gb of ram ,,,, are you running a server?

What version are running 10.01,11.10,120.4??

---

### Post by drs305 on 2012-06-30
If you only see the Grub menu when holding down the SHIFT key, it means it hasn't 'found' Windows yet. Boot into Ubuntu, then open a terminal and run the following command:
```
sudo update-grub
```
Enter your password when asked. You won't see it but it's there. Press ENTER after you've typed it.

Grub will then perform a search for other operating systems. Hopefully it will then find Windows and add it to your Grub menu.

---

### Post by E-Tramp on 2012-07-02
Maybe I didn't make myself clear here.  The grub menu doesn't even come up.  The computer continues to boot right into the Windows 7 program without interuption.

It appears that the program didn't even install the grub program, or at least the entry on the boot list that sends the system to where the grub is suppose to be.

It is Ubuntu that isn't accessable.  The installation is there on the drive, but, I don't even know if it is bootable because no grub.  It installed but, beyond that I don't know.  Fortunately 
Windows 7 still works fine, but, I am looking to have Ubuntu or one of the Linux programs working on this system.  It is what I built this system for.  It is my intention to never buy another Windows program if I know that the Linux system will do everything I want to do.

---

### Post by oldfred on 2012-07-02
Best to post link to BootInfo from this. It may also repair the install, if you are adventurous, but better if we can review first.

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

You only need swap equal to RAM if using hibernate. I find Ubuntu boots fast enough on my system that hibernation does not save enough time to be worth the effort. And it sometimes adds issues.

If you have that much RAM you may never use swap, some with lots of RAM have not swap and say it works, others suggest system boots better as it does not have to search for swap and timeout or when running look for swap. I then suggest just a small 2GB swap to have some.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Some others use a swap file, more like Windows.
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

---

### Post by E-Tramp on 2012-07-07
OK, I used the Boot Repair to scan the programming on my computer.  This is the URL it posted.  I checked it and it looks to me like the grub didn't install.  But, since I am new to this, I will leave it to you to tell me if that is true or not.

URL: [http://paste.ubuntu.com/1079114/](http://paste.ubuntu.com/1079114/)

There you are.  Thanks.

---

### Post by YannBuntu on 2012-07-07
> **E-Tramp said:**
> OK, I used the Boot Repair to scan the programming on my computer.  This is the URL it posted.  I checked it and it looks to me like the grub didn't install.  But, since I am new to this, I will leave it to you to tell me if that is true or not.

URL: [http://paste.ubuntu.com/1079114/](http://paste.ubuntu.com/1079114/)


I confirm.
I think Ubuntu tried to install GRUB in the MBR of sda and failed because sda is GPT and has no BIOS-boot partition.
If I were you, i would simply use Boot-Repair's "Recommended repair", then make sure your BIOS is setup to boot on the sdb disk (the disk containing your OSs). Indicate the new URL that will appear if any problem.

---

### Post by oldfred on 2012-07-07
It does not look like it even fully installed as it is missing the kernel and grub files. Did you have a separate /boot that is now missing?

```
=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 205.394493103 = 220.540657664  boot/vmlinuz-2.6.38-8-generic                  1
 205.394493103 = 220.540657664  vmlinuz                                        1
 
```You  also have some issues on sda:
> /dev/sda1 overlaps with /dev/sda4
 /dev/sda2 overlaps with /dev/sda4


NTFS and Fat info:
FAT 4GB file max & no journaling 
[http://technet.microsoft.com/en-us/library/cc938932.aspx](http://technet.microsoft.com/en-us/library/cc938932.aspx)
[http://technet.microsoft.com/en-us/library/cc940351.aspx](http://technet.microsoft.com/en-us/library/cc940351.aspx)

Keep systems separate from Data.
Keep an entire system on a drive so the drive can boot even if other drives fail.
Do not write into another systems partition unless you have to to make repairs. Reading is ok or mount windows system partition as read only.
Even in Data partitions use reliable drivers. i.e. NTFS driver in Linux is now considered reliable enough to read data partitions. Do not use FAT32 unless other device - camera, xbox, etc have to have it. And not for large partitions.

---

### Post by E-Tramp on 2012-08-02
Thanks Fred, I have decided to just do a complete re-installation, and burn a whole new disk to install with, this time from a torrent file, in case the original disk had some problems.  I have downloaded 4 different flavors of Mint and burned them to disks, and I have tried what I could of them, (some would not boot from the live disk), and I have tried xupbuntu, and Lubuntu, and Ubuntu 11.10, and 11.10 of course you probably know, was the first use of the Unity interface,(that once again really sucks in the intuitive department), and in the end I have decided to either use Ubuntu 10.10 or 11.04 since they are the last of the nice, comfortable, and intuitive original interface.  Much better for beginners with the menus.

In answer to your question, no, no separate boot, that is the way it installed the first time, and if it is caused by what you say, then doing a complete re-installation may do the same thing as this time, but, what I am hoping is that there is something wrong with the original disk,(a CD not a DVD), and having burned a new one from a torrent file maybe it will work right this time.

If it installs properly this time then it was probably a disk problem from either a corrupted download, or something to do with the disk because I didn't use a DVD when I burned it the first time.

I am going to look at my partitions again on the 3TB hard drive and probably go ahead and make them NTFS, if I haven't already.  I have pretty much been changing this system around since I built it and find out that this or that needs to be changed.  Trial and error pretty much on everything.  I forget if I changed The Fat32 files or not, already.  I have been busy doing other stuff so will have to look at them to see how they are now.

One thing I will say is that I tend to share disk space with both of my OS's on the machine, but, never open Linux programs in Windows, though sometimes I do get virus warnings from my AVG program on Linux files in Windows.  I tend to ignore them and so far nothing has gone amiss.  All of my data files,(whether Linux or Windows are kept on drives separate from the OS systems themselves.  I don't like to put any downloads on the OS drives.

I don't know what to do about the overlaps on sda.  Maybe when I change the file system they will be cleared up.  Since it is the 3TB drive and GPT, I guess I will have to partition them more carefully and see.  I will eventually work it out. Lots of stuff to learn, and lots to study first.  Trial and error, trial and error.  Wish it would go faster though.  Too much to do, not enough time.

Will get back to you after I have tried a new install and changed some things around to see what happens.

---

### Post by oldfred on 2012-08-02
With gpt you have to have a bios_grub partition for grub to correctly install. I use gpt with BIOS boot and once I created the bios_grub partition have not had any issues. (Other than always needing nomodeset on first boot to get nVidia to work.)

Since I plan a new system with UEFI and the efi partition has to be first, if you think drive will ever be used with a new UEFI system, it would be better to create efi now. It will not be used unless booting from UEFI.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
    250 MB efi FAT32
    1 MB bios_grub  no format 
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

I find gnome-panel to be very close to the old menu structure. A few things are in different locations & it works better with a few additions.

gnome3 classic
sudo apt-get install gnome-panel
On login screen click on cog-wheel/star and choose 

12.04 LTS / Precise Classic (No effects) Tweaks and tricks
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

With gnome2 it was called fallback and if you install fallback in 12.04 you get gnome-panel.

---

### Post by E-Tramp on 2012-08-02
Oh, OK, so I can use 12.04 and get the old interface back.  I am glad to hear that.  I really do like it much better.  Seems rediculous to me that they didn't leave it the way it was.  Especially with newbies like me who don't have years of experience working with this program and so don't know the names of the various systems tools you need to call up from the operating system to make changes.  I am afraid that who ever designed Unity wasn't thinking things out very well.

Since that is the case I guess I will try to install 12.04, and then use the fallback conversion.  That way I get the best of both worlds.

I do plan to upgrade my motherboard to the Rampage Extreme IIII that I believe is UEFI capable, because if I had known that they have changed from the BIOS system before I bought this board I would have gotten it before.  I really didn't know that R3E was more than three years old when I bought it, so, had no idea that there would be changes I would have to deal with.

Such are the complications of building a new system from scratch.

At present I only have the 3TB drive set up with GPT and I did change the formating to NTFS, but, I see now that I need to change the partitioning to allow the UEFI change over.  On the GPT drive does every data partition need the fat32 and 1MB no format or just the beginning of the disk itself?

Also, does the partitioning have to be  extended partions since I will be creating more than the four simple partitions that Windows allows? I don't know how Linux responds to the partitioning since I haven't used it much, but, the last time I tried partitioning a hard drive with four partitions one of them defaulted to extended drive no matter what I did.  That is windows however, and I am speaking of it only as a matter of compatibility of both systems, and since I will probably create the partitions in windows first, I want to make sure that I get everything right.

I will probably be using the sleep mode because I kind of like it (in Windows) because it saves me time booting up the motherboard each time.  This board is the slowest I think I have ever had.  So, many systems to boot up on it, expecially the drive hubs.  Not having to sit through that every time I sit down at the keyboard is nice.  First time I have actually used the sleep system.

OK, let me see if I have these partitions straight.  1st, 250MB FAT32, 2nd,1MB unformatted, 3rd, remaining harddrive space minus at least 2GB, for mount point, and 4th, 2GB or more, up to equal the RAM swap file partition,(I will probably use 24GB like my RAM). Correct?  Probably be better to set these up using the live disk, huh?  Now that I think about it, I don't think I can even set them up in Windows, since Linux seems to block access to its space from Windows.

Setting up the other disks in Windows and Linux, I need to add partitions at the beginning and end of ?each partition?each drive? for the information that will be need for the UEFI programming, is that not true? I am deliberately vague on the questions above because I know I read some of the information you gave me before that talked about redundant information at both ends of the drives  I just don't remember if it is actual drives or the various partitions.

To make changeover from BIOS to UEFI these things need to be done now for convience. If I get it right now it will save me a lot of work later.

I do need to re-read the part on the UEFI redundant information and the part on how to configure partitions so you don't have the overlap problems.  I set my 3TB drive up before I knew it would matter, so, I didn't really pay attention to the need to begin and end them in the right place.  I have to figure out where "the right place is going to be.

I will count on you tell me what other things I will have to change in the 12.04 system to get it as much like the classic gnome when I get it all arranged later.

---

### Post by oldfred on 2012-08-02
If you are going to put Windows on the gpt drive then you need several Windows  partitions also.

Only the efi partition is FAT32 and it will only be used for UEFI booting. Only the bios_grub is unformated and it is  only used with BIOS booting. But both are small, so no real space is wasted. LInux partitions are all ext4 (or ext3 or many others) except swap which is just swap.

I like to have additional partitions, especially when dual booting. A shared NTFS partition allows you to save data in a separate partition and use it from both systems. I also like extra 25GB partitions for another root to test another or next version Ubuntu. I also do not use /home but make the major of my space data but that is so I can mount the data partition in multiple installs.

I do not like hibernating when dual booting. My new cheaper SSD boots in 9 sec from grub menu to working system. BIOS & grub take another 15 sec or so for a total time of 25 sec. Hibernation does not buy much for me. If you write data from Ubuntu into a hibernated Windows you will corrupt it or lose what data copy thought you copied.

With gpt all partitions are primary. The gpt partition table info at the front of disk & the backup at the end are not in partitions and not really shown, somewhat like the MBR & PBR for each partition are not really shown.

With MBR partitions you will need an extended partition if creating more than 4 partitions. Do not use Windows as it does not create extended but converts to a Windows only proprietary dynamic disk arrangement that will not work with Linux (and even some Windows repair tools).

---

### Post by E-Tramp on 2012-08-03
OK, well it isn't my harddrive boot that is the agrivation part but the motherboard which has a lot of systems to boot.  Once I get to the software I agree it doesn't take very long.  The sleep cycle cuts out that motherboard boot time.  From what you are saying is it possible to boot into both systems simutaneously if they sleep?  It never occured to me that that might be possible.  It could pose a problem if you did boot the Ubuntu program up while Windows was sleeping, but, I think by paying attention to your power light, you should be able to avoid that mistake, don't you think?

I did take a good long look at 12.04 and 11.04 yesterday and finally decided that I am going to go ahead and use 11.04, because I really like the interface and how flexible the appearance is to manipulate.  Since 12.04 seems to have sacrificed that ability I will run 11.04 as long as possible and hope that subsiquent versions will either go back to the gnome interface or it will improve the unity appearance and flexibilty as well as practicality.

So, on the 3TB harddrive I don't have to do anything, since I did format it with GPT, does it then automaticly put the partitions at the front and back of the drive for information?

Let me see if I have this right.  When I go to partition the SSD, I first have to create the extended drive in the entire drive space I intend to use.  Then I create the other partitions inside the extended partition, in the sizes and formats above stated.  The installation will then use those various partitions for the installation. You said that you, "don't use /home, but make the major of my space data but that is so I can mount the data partition in multiple installs.", I am afraid I don't know what that means, exactly, to what are you refering when you say "multiple installs" and how does it benifit you by not using the /home designation?

I don't know if the information is relevent, but, since you mention it, I guess I would like to understand exactly what I am being told.  Also, since you and I have a common goal of upgrading to the UEFI system in the near future, the way you are recommending the partitions would in fact make it unnecessary to reinstall the Ubuntu programming?  But, since it is likely that I will have to install the Windows software from scratch, won't I still have to re-install the Ubuntu programming since you don't reccommend installing Windows after installing Ubuntu?

Granted having the partitions already laid out would save some work, but, not really that much, would it?

---

### Post by oldfred on 2012-08-03
If using Windows you have to use MBR and then the efi partition and bios_grub partitions are moot. Either you continue to boot with BIOS mode in the new UEFI system or totally reinstall.

The issue is if any data is written into the NTFS partition while Windows is hibernated then the hiber file does not see that data and corrupts system. See info on Windows 8 for more detail as that is 8's default:

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

You only need an extended partition in MBR(msdos) partitioning where you want more than the 4 primary partitions. And Windows only boots from a primary partition, the extended counts as a primary. But you can have essentially an unlimited number of logical partitions for Ubuntu in the extended.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

As I mentioned before gnome-panel in 12.04 is almost the same as the old gui.

Some really good info on SSD.
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

### Post by E-Tramp on 2012-08-03
Wow. That is weird.  I am glad I didn't buy into Windows 8 then, because that would have been a terrible surprise to fall into, though the hybrid sleep mode sounds like a neat idea.  It would certainly discourage me from doing a dual boot system if I had Windows 8.  Maybe, Ubuntu should start working on a failsafe GRUB that would prevent booting from Ubuntu when another system isn't completely shut down. Doubt if it would be very difficult for the GRUB to check the state of the two systems before it boots anything.

I assume that since you didn't say that my picture of the extended drive and partitions is correct, that it is.  From what you told me I will need to have five partitions for the Ubuntu install plus the partition that Windows is already in, for a total of six.

> "Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
250 MB efi FAT32
1 MB bios_grub no format 
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical"
So, if I understand this correctly, the partitions are laid out this way:

1. 250 MB efi FAT32
2. 1MB BIOS grub no Format
3. (Root?) 10-25GB Mountpoint/Primary or logical beginning ext4(or ext3)
4. All but 2GB (or greater up to the amount of RAM, which in my case is 24GB)Mountpoint /home logical beginning ext4(or ext3)
5. 2-24GB of swap.

Correct me if I am wrong here, that is how I interpret what you have stated.

On the gnome panel, does it also give you all of the customization of the interface that 10.04 does?  I really liked that about the gui desktop.  I just don't have any way of checking out the modified 12.04 without installing, and I just am not prepared to do that right now.  Maybe later I will fix one of my old computers and do an install on it to see if it is what I want, but, for now I think I will keep it simple and just do 11.04 that comes with a pleasing interface right up front.

I will look at that SSD information right now, because I am still working some things out about my new system and I knew very little about SSD's before I bought mine.

I am already concerned with how much free space I don't have, already.  I have 256 GB, half for windows, and half for Ubuntu, and The Windows 7 program is taking up 82GB and the only thing left that I can remove are files in my download folder that are from utorrent and I don't seem to be able to change the place that it downloads to.  Moving those will clear 20GB, but, that makes utorrent no longer able to upload those files, unless I can find a way to change destination folders for it.  When I installed it to download the Ubuntu programming I didn't see a choice of download destination.  Still 62GB of operating system and programing seems excessive.  Once I do move the torrent downloads I have nothing else to eliminate.  There is no extra's on my SSD, for obvious reasons.  My first harddrive was only 40GB.  This system wouldn't even fit on that.

Anyway, make sure you do cover the partitioning information I mentioned above, that is the important part. Later.

---

### Post by oldfred on 2012-08-03
Did you say 24GB of RAM. :)

If you have an SSD you will not need hibernation anyway. But you can do just about anything and never run of of RAM and use swap. Maybe if you are editing large videos all in memory might you fill your RAM.

Remember Windows wants two partitions normally, one 100MB boot/repair and the main install. And if dual booting it is better to have another NTFS partition for shared data. The Windows partitions need to be primary which can then change your partitions around.

Someone did say they were able to turn off the hibernation in Windows 8, but I think the hibernation is why many are saying that Windows 8 is really quick booting, even better than Ubuntu. They just do not realize that is what is happening. And for most that probably is ok.

You get most of the configuration but have to add in some things. kansasnoob has documented most of the procedure:

[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
12.04 LTS / Precise Classic (No effects) Tweaks and tricks
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) - kansasnoob
sudo apt-get install gnome-session-fallback
sudo apt-get install gnome-tweak-tool
# this is same as fallback
sudo apt-get install gnome-panel
sudo apt-get install indicator-applet indicator-applet-session
Before you log in, click the gear icon and select GNOME Classic.
gconftool-2 --set "/apps/metacity/global_keybindings/panel_run_dialog" --type string "<Alt>F2"
gsettings set org.gnome.desktop.screensaver lock-enabled false
gsettings set com.ubuntu.update-notifier auto-launch false
gconftool-2 --set "/apps/metacity/general/button_layout" --type string "close,minimize,maximize:"
sudo apt-get install shiki-colors-metacity-theme
gconftool-2 -s --type string /apps/metacity/general/theme Shiki-Colors-Metacity
echo export LIBOVERLAY_SCROLLBAR=0 >> ~/.xprofile
gsettings set org.gnome.desktop.interface menus-have-icons true

---

### Post by E-Tramp on 2012-08-03
You really want me to do the 12.04 fallback system, don't you?

Yes, 24gigs of RAM, and 12 virtual CPU's, I7 970 3.2Ghz, and 1333Mhz on the RAM.  Not to mention dual NVidia GForce GTX560's for two more processors.

I expect to get 10 years out of this machine before it is way behind the curve of speed and efficiency.  I also got it to do 3D vision, because I think that is coming in the next generation in a very big way.

It is very fast.  Now if only my internet connection would keep up.  Unfortunately I can only get 1GB download speed, where I am, unless I want to use satellite and that is just way over priced right now.  I was hoping to get 7GB, but, can't even do that with the overpriced satillite system.

I read some of the stuff you linked me to, on SSD's, and a question I did have is if I should use fdisk for the partitioning?  It seems from what they say I would have a better chance getting the alignment right using it.

---

### Post by oldfred on 2012-08-03
I use gparted for all new gpt drives and used to use it for my MBR drives before. I often downloaded the newest liveCD from gparted, but you can use the version with Ubuntu's liveCD. Do not use an older one. I also download from the repository gdisk to list gpt partitions.

Is this system UEFI? Almost all I7 systems have motherboards that boot UEFI or will boot in BIOS? That adds a bit of complication. If you want UEFI, you have to boot the installer from the UEFI menu and choose the UEFI/efi version. If you boot the BIOS version it will install in BIOS mode. Same for Windows. 

My system is BIOS only but I hope to get a new system soon. So I create an efi partition first on the drive even though I will not use it now. It can be a bit difficult to add an efi partition later and it is not large. Since I have gpt and BIOS I have to also have a bios_grub partition for grub to install correctly with BIOS/gpt.

My SSD is 62GB so I created 2 30GB / (root) partitions. One is for the current install and the other for testing or next version. I also have Ubuntu on every other drive except my old XP drive which since changing to AHCI does boot :) .

```
fred@fred-Precise:~$ sudo gdisk -l /dev/sde
[sudo] password for fred: 
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sde: 117231408 sectors, 55.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 85A657E7-D379-4592-B060-E8EA09953D80
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 117231374
Partitions will be aligned on 2048-sector boundaries
Total free space is 3645 sectors (1.8 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          616447   300.0 MiB   EF00  
   2          616448          618495   1024.0 KiB  EF02  
   3          618496        58925055   27.8 GiB    0700  Precise
   4        58925056       117229743   27.8 GiB    0700  Quantal


```

---

### Post by E-Tramp on 2012-08-04
I found a website on the internet called Linux-Tracker, that is all Linux downloads, and there are several Gparted downloads to choose from.  The most recent was added on August 8th, and is version 0 13 0 3.  Is that the one you suggest I use?

My system isn't UEFI, the motherboard is three years old, and was designed for Gaming so, while it was leading edge when it was made, it is old stuff now.  I didn't know that until I had already bought it.  My mistake.  I made a lot of mistakes on this build because I didn't know all of the recent changes.  I figure I will stay with the ASUS Rampage III Extreme for a year or so, and then upgrade to the Rampage IIII Extreme, which I am pretty sure is UEFI.  Haven't checked it yet, but, it seems logical since it is the most recent issue ASUS has in the ROG market it will be. Before you ask, I am not a gamer, have never even played the games on my Windows system, either of them.  I am just a technophile who wants the latest cutting edge technology to last me for the next ten years before the speed and efficiency curve catches up to me and passes me by.

You will notice that your "whole" SSD won't even hold my Windows 7 program and software.  I don't have any extra stuff, just the stuff I use every day to run the hardware and cleaning and security, and whatever I need for downloads and such.  I usually have FireFox on my system as a second browser, but, I don't know if I should even add anything else that isn't absolutely necessary.  I kind of wish I had gone ahead and gotten the 512MB one now, but, 256 seemed to be a lot just to install an operating system on.  Now, it is looking smaller and smaller.  Maybe I should dump all of the update backup files and get rid of that.  I have never undone an update in Windows yet.

---

### Post by oldfred on 2012-08-04
I like to split operating systems from data. With my old XP it was a bit more difficult as many applications would only write to their specific location. So I just created a .bat file to copy to my data partition so I could backup easier. Firefox & Thunderbird make it easy to move profiles, so I am able to use same profile in every install I have from one partition. Picasa finds all my photos so again I only have photos in one place. Bit easier to backup.

If not using games which can be very large, you should not need more than 50 or 60GB for Windows (I have seen 30 as a suggested minimum although it will install in less) and 25GB for Ubuntu. I actually use about 7GB in a 25GB partition for each /(root) that I install. In Windows you must have something that is large or is it just data?

I use this logic on why I have Ubuntu on every drive.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

I have two main data partitions and a backup partition. One data partition is still NTFS for sharing with XP when I still used it. And now all new data goes into a ext3 (if creating now I would use ext4).

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by E-Tramp on 2013-01-11
1

---

### Post by E-Tramp on 2013-01-11
Sorry I haven't been here in a while Fred, but, I have been really busy.  Now in answer to your question, I have Microsoft Office which is bigger than the operating system to install if my memory serves me right.  I must confess however, that as of yesterday all of my work on my windows system fell apart as a result of Microsoft appearantly blocking my key code.  I am now officially a non-windows person as this is the third time I have bought Windows 7 only to find out I was being ripped off by Microsoft.  If they want to do price fixing then they will do it without me.  I will use linux systems from now on.  I am not going to keep buying from someone who will rip me and a lot of others off to protect there absurd profit margin.

So now, I think I am going to do two things and maybe you can help me do them.  In the old Windows partition I am going to reformat and install a copy of Knoppix(because I really like the interface on knoppix, the only thing that I don't like is the absence of the power down button), and see how it is as an operating system, and I will reinstall the latest Ubuntu on the other partition and use the fallback to convert it to the old interface.

This time I won't stop until the job is done.  I will probably be bugging you a lot till it is. 

So, am I going to have to change my formatts on all of my drives from NTFS
to ext4 or will Linux deal with them alright for now?

---

