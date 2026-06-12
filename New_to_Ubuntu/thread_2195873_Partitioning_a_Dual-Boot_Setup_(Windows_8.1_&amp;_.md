---
title: "Partitioning a Dual-Boot Setup (Windows 8.1 &amp; Ubuntu 13.04)"
date: 2013-12-26
forum: New to Ubuntu
---

### Post by siliconknight86 on 2013-12-26
So basically I need some help partitioning my HDD for installing Ubuntu 13.04 alongside Windows 8.1 which is already installed. I'm still relatively new to using Linux & it's various Distro's. Ubuntu being my favorite thus far out of 2 I've tried (I know, I've barely scratched the surface on the flavors of Linux out there) I've installed Ubuntu twice now, the first Time had no Idea what I was doing since I have never dual-booted anything, except for using Multi-ROM on Android to dual-boot various ROMs, namely Ubuntu-Touch on my Nexus 4...can't wait for the Nexus 5 version. I ended up just using the Wubi installer from inside windows, for Ubuntu 12.04, but it ran like crap cause it wasn't setup/optimized Properly. The 2nd time, I partitioned my drive myself following a couple guides. Ran pretty good, but from what I read afterwards, I still coulda done a better job, and missed of the stuff from the guides, just cause I was an idiot and didn't wanna ask for help.
 
Both those times were with Windows 7 as my Secondary OS, but now I have upgraded to Windows 8.1 and I got a copy of Ubuntu 13.04, and I wanna dual-boot as I said. I have been getting into Programming & Development (Mostly Android Apps, ROMs, Kernels, etc etc, but also have been messing around with PC Game design) so I was hoping that someone could point me in the direction of a good guide for setting up my partitions. I am doing this on my Laptop which has the following Specs - 

AMD Phenom II Triple Core @ 2.6Ghz
OCZ 8GB DDR3 1333Mhz
WD 1TB SATA (6GB/s) HDD
AMD/ATi Radeon Mobility 5870HD
blah blah blah

So that's what I need to optimize my install for. Not that great, but good for my purpose of Development, and gaming on the go. Just thought I would give as much info as possible. Been awhile since I've had to be a newb lol I've been building Custom PC's since i was 15 (27 now) but never really got into Linux until this year. Feel like a dumbass for what I've been missing out on.

---

### Post by oldfred on 2013-12-26
How is drive currently partitioned. BIOS/MBR(msdos) or gpt with UEFI boot?
sudo parted -l

Standard default install is just / (root) & swap, but often better to have separate /home or better still separate data partition(s). But each adds a bit of complexity in installing.

With Windows 8 you do have to turn off the always on hibernation or fast boot. And you need good backups and a Windows repair flash drive.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)


 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by siliconknight86 on 2013-12-27
Sorry new there was a bit of Info I forgot to add. This laptop has a Standard BIOS. Right now it's partitioned as 350MB System Reserved, and 218GB for Windows Programs, and Storage (I use external HDD's for most my storage because I am a Musician and Audio Engineer/Producer, so I bring projects over to other studios, jam spots , etc etc, so i need portability. I have 246GB of un-allocated and un-formatted space saved for Ubuntu and for a shared partition. Which from what I was told, I want to format all the Linux partitions to ext3, except the shared partition which I wanna put in NTFS (since FAT32 has limitations that are just not doable for me) Last time I set it up like you first mentioned, like /, Swap, Shared. But I've heard the same thing you mentioned about it being better to have separate [COLOR=#000000]data partitions. But as I only have 500GB and am still learning I don't wanna make it too complex just yet. [/COLOR]

[COLOR=#000000]So yea, thanks for the advice and the links. Didn't realize how late it was, and I got get up early for a show we are playing tomorrow night, so I will give it a go in the morning before I take off for the day, and will post my results back here. [/COLOR]

[COLOR=#000000]Any other advice, links, are welcome, I like to absorb as much information as Possible. [/COLOR]

---

### Post by Bucky Ball on 2013-12-27
EXT4, actually. You must have looked at older info. You can use EXT3 but newer releases default to EXT4 unless you tell them otherwise. ;)

As for the partitions, if you are storing your personal data elsewhere the /partition only really needs to be 20Gb or so. The rest (480Gb or whatever you have) can be used for /home (EXT4) and /shared (ntfs) with a 2Gb /swap at the end of all that.

/ = 20Gb
/home = large as you like
/shared = as above
/swap = 2Gb

Just one of many possibilities. You can also create symlinks to any existing partitions which currently contain data you'd like to access in Ubuntu.

---

### Post by siliconknight86 on 2013-12-31
sorry it's taken so long to reply, i went on a surprise vacation my GF put together for me....Anyways, my final question is; Obviously / needs to be Primary, but /home, /Shared and /Swap can be Logical partitions correct ? And what is the /Home partition used for ? I was just gonna follow the partition setup that "Bucky Ball" suggested.

here's how I have windows currently partitioned and it shows the free-space I have left at the bottom, which I want to use for Ubuntu and a /shared partition. 
[[IMG]http://imagizer.imageshack.us/v2/640x480q90/856/tgsg.png[/IMG]](https://imageshack.com/i/nstgsgp)

---

### Post by JeQhdMD on 2014-01-01
Here's more info from a short but clear thread re partitions - it should clarify some things for your consideration:   [http://ubuntuforums.org/showthread.php?t=2169981](http://ubuntuforums.org/showthread.php?t=2169981)

---

### Post by JeQhdMD on 2014-01-01
It's best, after using windows tools to defrag and shrink windows, to then use linux tools to repartition and setup the default file system.  Also recommend ext4 re stability.    I like using gparted to do the repartitioning.  It should be on ubuntu or xubuntu live media (dvd/cd or usb flashstick).   You can also use a good live linux CD like parted magic to handle these tasks.  Do not recommend using windows tools to do repartitioning.  Finally, it's better to install Ubuntu or Kubuntu 13.10 vs 13.04 . . . re future updates and ease of upgrade to 14.04 (the next LTS (Long Term Support) version of the "Buntus)).

Here's more info from a short but clear thread re partitions - it should clarify some things for your consideration:   [http://ubuntuforums.org/showthread.php?t=2169981](http://ubuntuforums.org/showthread.php?t=2169981)

---

### Post by Bucky Ball on 2014-01-01
Actually, / doesn't need to be a primary. Ubuntu will exist happily inside an extended partition. ;)

---

