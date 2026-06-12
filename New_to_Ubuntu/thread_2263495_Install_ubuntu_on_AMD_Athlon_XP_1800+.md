---
title: "Install ubuntu on AMD Athlon XP 1800+"
date: 2015-02-01
forum: New to Ubuntu
---

### Post by jdbic on 2015-02-01
This is what I have: 
 OS Version: Microsoft Windows XP Professional,, 32 bit
 Processor: AMD Athlon(TM) XP 1800+, x86 Family 6 Model 6 Stepping 2
 Processor Count: 1
 RAM: 1023 Mb
 Graphics Card: 
 Hard Drives: C: Total - 15005 MB, Free - 12348 MB; D: Total - 39205 MB, Free - 5301 MB; E: Total - 39995 MB, Free - 7780 MB; F: Total - 40382 MB, Free - 24772 MB; G: Total - 39393 MB, Free - 7703 MB; H: Total - 38640 MB, Free - 7080 MB;
 Motherboard: ASUSTeK Computer INC., A7V333
 Antivirus: None  
 Will Ubuntu work? There are two hard drives, three partitions each.

---

### Post by Impavidus on 2015-02-01
Instead of simply listing all partitions as if they were drives, could you explain the layout of your partitions and any unallocated disk space over your two drives? A screenshot from a disk partitioning tool will do. And the graphics card is important, as that is one of the most common issues when installing Ubuntu.

That being said, I don't see any reason why Ubuntu wouldn't run, but I recommend installing one of its lighter flavours. Xubuntu should run OK, Lubuntu even faster. If you have two hard drives, it is best to keep windows on one and install Ubuntu on the other, each with their own boot loader. You have to use manual partitioning to get that done.

---

### Post by mörgæs on 2015-02-01
You are going to face problems with SSE2. Please see the link in my signature, especially post 2. Ubuntu will be a  pain but Lubuntu is a good choice.

May I guess, the graphics adapter is Nvidia Geforce 2 or a close relative...?

---

### Post by jdbic on 2015-02-01
Would this be the graphics card? Radeon 8500/ Radeon 8500LE. What is SSE2? I just put 3 partitions on each of the two hard drives because back then it was recommended so if the c: which has xp on it failed I would not loose what was on the other partitions.

---

### Post by grahammechanical on 2015-02-01
According to this link it seems that the Athlon XP1800+ is a 32 bit CPU. So, you will need a 32 bit version of Xubuntu or Lubuntu. We can run the Ubuntu family of Linux distributions as a Live or Try session before we install. In this way we can test out the operating system before we install to hard disk. This is the best thing to do.

[http://www.cpu-world.com/CPUs/K7/AMD-Athlon%20XP%201800+%20-%20AX1800DMT3C.html](http://www.cpu-world.com/CPUs/K7/AMD-Athlon%20XP%201800+%20-%20AX1800DMT3C.html)

Regards.

---

### Post by jdbic on 2015-02-01
Ok, I downloaded the lubuntu LTS version, 14.04.1. It has torrent after iso in the file name. My burn software doesn't work with that extension. It does iso though. What program burns that file to dvd? Is that a compressed file?

---

### Post by jdbic on 2015-02-01
I figured out how to do the torrent file.

---

### Post by mörgæs on 2015-02-01
> **jdbic said:**
> Would this be the graphics card? Radeon 8500/ Radeon 8500LE.


OK, I was too self-confident there. Anyway the card should only run the lightest of environments, for example Lubuntu.

---

### Post by jdbic on 2015-02-01
I burned the lubuntu iso to dvd and booted  up the machine. It took a while . Finally a box shows up asks for user name and pass word. I have no idea what to enter . Thought it meant create one, but that didn't work. Did I forget something?

---

### Post by mastablasta on 2015-02-02
> **jdbic said:**
> I burned the lubuntu iso to dvd and booted  up the machine. It took a while . Finally a box shows up asks for user name and pass word. I have no idea what to enter . Thought it meant create one, but that didn't work. Did I forget something?

that shouldn't happen.
if you downloaded with torrent, then the download is good. however your iso is maybe badly burnt. here is how you do it: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

you can check if iso is burnt ok or not. there should be an option like test disk for errors or something like that when you boot.
also try xubuntu. Lubuntu is good and light but it might not be so new user friendly. the desktop is not that mature. anyway just try & see what you like best.

---

### Post by jdbic on 2015-02-02
The burn was not good, I burned another and it worked. It is slow I guess because it is running from the disk. 
As mentioned above, I have two hard drives , 3 partitions each. If I install lubuntu will I be able to pick which drive and will the partitions stay?

---

### Post by mörgæs on 2015-02-02
Please post the output from ```
sudo fdisk -l
``` in CODE tags.

---

### Post by Impavidus on 2015-02-02
You can pick the drive to install Ubuntu (or Lubuntu, installation process is the same) on and leave the other untouched. It will be necessary to format some partitions though, so there's little point in keeping them exactly the same. The safest thing to do is moving all files from the drive that will get Ubuntu to the one with Windows (the one with the C partition). To be really sure you can then physically disconnect that Windows drive and reconnect it after installing Ubuntu to the other. It may help if we know the exact current partitioning. For that, run Mörgæs's command from the live disk and post the output. If it asks for a password, just hit enter.

As for SSE2: [http://en.wikipedia.org/wiki/SSE2](http://en.wikipedia.org/wiki/SSE2). Without SSE2 the flash player is not going to work (except for some really old versions). There may be other software affected too.

---

### Post by jdbic on 2015-02-02
How/where do I run that code? What are code tags? I'm doing a lot of reading but didn't come to that yet.

---

### Post by Bashing-om on 2015-02-02
jdbicjdbic; hello;

> **jdbic said:**
> How/where do I run that code? What are code tags? I'm doing a lot of reading but didn't come to that yet.

Boot the liveDVD "try ubuntu" mode to the desk top . key combo ctl+alt+t will get you a terminal interface. At this terminal execute terminal command:
```

sudo fdisk -l

```
Place that out put between code tags:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Then we know what we are working with and can advise better.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by jdbic on 2015-02-02
I tried the code and this is what I get:
 lubuntu@lubuntu:~$ ```
sudo fdisk -l
```
```
sudo: command not found

lubuntu@lubuntu:~$ [code] sudo fdisk -l 
```
[code]: command not found
lubuntu@lubuntu:~$ 
tried it twice ,second time with spaces

---

### Post by Bashing-om on 2015-02-02
jdbic; UMph !

Making The transition for gaining elevated privileges from "sudo" (gkso) to that of 'pkexe. 'gksu' is depreciated,
Try:
```

pkexe fdisk -l

```

I an not versed in 'pxec', - I still rely on 'gksu' -; see how that runs.

[INDENT][INDENT]in a changing world
 [/INDENT][/INDENT]

---

### Post by Impavidus on 2015-02-02
No, [noparse]```
:[/noparse] was not part of the command. Just use **sudo fdisk -l**

Use the [noparse][code]code tags
```[/noparse] when posting the output on the forum.

---

### Post by jdbic on 2015-02-03
OK, got it:
```
lubuntu@lubuntu:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcac0cac0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    30732344    15366141    7  HPFS/NTFS/exFAT
/dev/sda2        30732345   195366464    82317060    f  W95 Ext'd (LBA)
/dev/sda5        30732408   112663844    40965718+   b  W95 FAT32
/dev/sda6       112663908   195366464    41351278+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x931431f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    18158078     9079008    7  HPFS/NTFS/exFAT
/dev/sdb2        18159614   240107489   110973938    f  W95 Ext'd (LBA)
/dev/sdb5        80292933   160971299    40339183+   7  HPFS/NTFS/exFAT
/dev/sdb6       160971363   240107489    39568063+   7  HPFS/NTFS/exFAT
/dev/sdb7        46303232    78196735    15946752   83  Linux
/dev/sdb8        78198784    80291839     1046528   82  Linux swap / Solaris
/dev/sdb9        18159616    46301183    14070784   83  Linux

Partition table entries are not in disk order
lubuntu@lubuntu:~$ 
```

---

### Post by Bashing-om on 2015-02-03
jdbic; Et al ....Hummm ...

do not know so much as this is good (??)
> 
Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x931431f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    18158078     9079008    7  HPFS/NTFS/exFAT
/dev/sdb2        18159614   240107489   110973938    [color=red]f  W95 Ext'd (LBA)[/color]
/dev/sdb5        80292933   160971299    40339183+   7  HPFS/NTFS/exFAT
/dev/sdb6       160971363   240107489    39568063+   7  HPFS/NTFS/exFAT
/dev/sdb7        46303232    78196735    15946752   83  Linux
/dev/sdb8        78198784    80291839     1046528   82  Linux s


try'n to run Ubuntu from within a Windows' extended partition. Do not hardly think so, but, I have been wrong before.

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by jdbic on 2015-02-03
Well, I don't know what all that info means that is in the boxes. In windows the partitions are listed as c:,d:,and so on. How do I know which /dev/sda and so on ,corresponds to the drives in windows?

---

### Post by Bashing-om on 2015-02-03
jdbic; Hey;

While awaiting a consensus on my opinion. Taking a cause for the pause;
> 
Well, I don't know what all that info means that is in the boxes.

What Window's calls a drive is actually a 'partition' on a hard drive .
Generally speaking Windows sees c: as the partition that it's operating system is installed onto ; ubuntu sees that 'partition' as sda1.

Here is how that works;
the first (s)erial (d)device that the system when booting up recognizes is 'a' -> sda
the 2nd device is sd(b) -> sdb
the 3rd might be sd(c) -> sdc
Those - sda, sdb, sdc - are all hard drives . These hard drives are sliced up in usable portions, called partitions. A partition in ubuntu is identified by number.
sda1 = 1st hard drive, 1st partition
sda3 = 1st hard drive, 3rd partition
sdb5 = 2nd hard drive 5th partition
sdc8 = 2nd hard drive 8th partition
-----------------

OK, what we have in your case is ubuntu sees "sdb2" as a Windows Extended partition, now this 'extended' partition is a "container" that holds 'logical' partitions. Here we have:
sdb7 holding the ubuntu install ( that I seriously doubt that the grub can find ) Edit: With out some help -> chainloading ?
sdb8 is the ubuntu swap partition.
---------------
aside:
We can surmise that Windows is installed on the 1st hard drive, designated by ubuntu as 'sda' and encompasses all the partitions.

and as well, Windows 'might' be installed onto the second hard drive - sdb1 , sdb2 - and then dual booting from 'sdb' OR this could be 'data' partitions to support Windows on the 1st hard drive, To ubuntu will make no difference; all it will see is used partitions.

The question here is do we RE-partition such that ubuntu is installed on it's own partition outside of the Windows' extended partition ? I am not Windows literate, and I reserve my further advise, 'til those who are knowledgeable render their advise.

My path to an end may be different
[INDENT][INDENT][INDENT]we will get there
[/INDENT][/INDENT][/INDENT]

---

### Post by jdbic on 2015-02-03
Alright, I sucked in that info. So if I repartition what are the consequences ? I have been taking files off the partitions. Windows xp is going down the drain anyway. What if I format the one called sdb. Can Ubuntu be told to go there?

---

### Post by Bashing-om on 2015-02-03
jdbic; Sure !

If you have all you want off of that sdb drive, installing ubuntu as the sole operating system on that 2nd hard drive is great.
Depending on your experience level, and level of want to, might make up partitions before hand, and make up a NTFS data partition to share files with Windows ? Worth think'n about .
Make sure grub is installed to 'sdb' - Windows on 'sda' will not be touched.
Then if the second hard drive has boot priority in bios, you have the choice of which operating system to boot.
If the 1st hard drive is the 1st boot priority in bios, Windows will boot, irrespective of ubuntu.
I know of no cons, and all pros with this arrangement.

To Windows there is no other operating system in the world;
ubuntu will pick up Windows boot code and chainload it onto it's boot menu .

[INDENT][INDENT]where there is a will
[INDENT][INDENT][INDENT][INDENT]there is a way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jdbic on 2015-02-03
Yea, I think I can do this. I'll read three times then proceed, can't go wrong. How do I make up partitions before hand, and make up a NTFS data partition to share files with Windows ? What is grub? ( I know it's not a meal) I guess I would get into the bios from the start up screen when I turn on the machine.

---

### Post by Bashing-om on 2015-02-03
jdbic; Hey;

I have these others that delay my responses.

OK, partitioning:
have a read:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

and grub is GRand Unified Bootloader. Touted as the best bootloader around.

and yeah, " I guess I would get into the bios from the start up screen when I turn on the machine" in bios select the hard drive for bios to hand off to where the boot code is located (the device ).

Now, if one is careful and exercise caution and watching what they are doing, one can install to the desired hard drive. If one is uncertain, remove the hard drive that you do not want written to. Then there is no room for an error.  When the install is completed hook that drive (here sda) back up. -> some fuss but no muss. Just make sure that grub gets installed to the hard drive that ubuntu is installed onto.

ANYTHING that you are uncertain about, or have questions, ask before proceeding . 

To err is human, to really mess up a system takes a partitioner . -> observance of the results of the fdisk and parted commands helps bunches.

[INDENT][INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT][/INDENT]

---

### Post by jdbic on 2015-02-03
OK, I'll read the links tonight and start the process tomorrow. I'm looking foreword to this working.

---

### Post by Bashing-om on 2015-02-03
jdbic; Hey ;

> **jdbic said:**
> OK, I'll read the links tonight and start the process tomorrow. I'm looking foreword to this working.

We will make it work
[INDENT][INDENT][INDENT]a little help from your friends
[/INDENT][/INDENT][/INDENT]

---

### Post by jdbic on 2015-02-04
I'm still studying and learning. But sometime I end up with more ques.
In the partitioning guide it is mentioned to delete files and then defrag. What is the program called in Ubuntu and where is it? I checked the icons at the bottom of the screen but can't seem to find it. 
 What if I reformat the sdb. Will the partitions stay? If not wouldn't it be easy just to make new ones?

---

### Post by Bashing-om on 2015-02-04
jdbic; YeaH ;

That is in the process of learning, leads to more questions the more you know.

OK, here is what is pertaining to your particular situation.
Defrag is a Windows' thing. linux (ubuntu) is a journal file system as fragmentation generally - house keeping observed -  does not occur .( I use 90 % capacity as my guide). I have yet to ever come even close to that ceiling .

> 
In the partitioning guide it is mentioned to delete files and then defrag.

In your planning stage **IF** you were to keep Windows on the same hard drive as you intend to install ubuntu, then yes: one would defrag the Windows File system twice, resize the Windows partitions to accommodate  making up ubuntu's partitions, and also in windows run the Windows' check disk utility twice. This makes sure that Window's partition table is in order.

> 
What if I reformat the sdb. Will the partitions stay? If not wouldn't it be easy just to make new ones?

A reformat wipes out everything .
As to making up new ones -> ubuntu's preferred GUI tool is GParted. IF you presently have no concern how ubuntu is installed then you need not even be concerned with partitioning. ubuntu's install wizard will do all that for you and set up the default partitions and sizes .
If you select the option " erase disk and install ubuntu" choose the correct drive 'sdb' the wizard will do just that. BUT, pay close atttention to where grub ( GRand Unified Bootloader) will be installed. IN the case of 'sda' as Windows, and 'sdb' to be ubuntu, you want grub installed to 'sdb' !
Make sure you do not replace Window's boot code on 'sda' .
Along with this thought, it is strongly advised to  have the system connected to a wired internet connection. Wireless drivers may not be present in the install or after the install completes.

OK, say that you desire to set up your partitions yourself for your particular use case - there are a couple of options (as always it is linux --- options !)

As Mentioned there is GParted to set the partitions up before hand.
In the installer choosing the option "something else" one can either point the installer to the partitions you have made up OR with a bit of prior planning use the installer's partitioner to make up the partitions on the fly.

This is a learning process, making mistakes is OK, one can always wipe the disk and start all over to get exactly what you want.

As a reference, what is generally recommended for partitioning
'/' as 30 gigs
/home as 40 gigs - IF you intend to install many additional applications make it bigger
swap partition .. how much ram is installed ? IF you have 8 Gigs AND do not ever hibernate then do not even bother, will never be used ( unless you are doing some real heavy number crunching) IF less than 8 Gigs ... make the swap partition slightly larger in size than the amount of memory (ram) that is installed.
/data - NTFS partiton so Windows can also access/share these files ..  depending on your usage, say 20 Gigs.

These are but "rough' guides. I run lean and mean and I do with much much less !
> 
sysop@1404mini:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       4.7G  3.2G  1.4G  71% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           2.0G   12K  2.0G   1% /tmp
tmpfs           396M  740K  395M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G   23M  2.0G   2% /run/shm
none            100M   12K  100M   1% /run/user
/dev/sda2       9.5G  2.4G  6.7G  27% /home
/dev/sda8       4.7G  1.4G  3.1G  32% /var
sysop@1404mini:~$sysop@1404mini:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       4.7G  3.2G  1.4G  71% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           2.0G   12K  2.0G   1% /tmp
tmpfs           396M  740K  395M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G   23M  2.0G   2% /run/shm
none            100M   12K  100M   1% /run/user
/dev/sda2       9.5G  2.4G  6.7G  27% /home
/dev/sda8       4.7G  1.4G  3.1G  32% /var
sysop@1404mini:~$


Remember. if you do not like it .. it is but a matter of minutes to do a redo - once you know what you are doing. If you want to get your feet wet real quick and start using ubuntu -> choose the "erase disk and install ubuntu" and it is all done.

a lot of info, but
[INDENT][INDENT][INDENT]it just is not that tough
[/INDENT][/INDENT][/INDENT]

---

### Post by Omo on 2015-02-04
I've done a few installs of Ubuntu on old boards like yours (said boards had been accumulated long ago for a dual-boot setup of Linux and Windows 98) and there are going to be some performance issues you will just have to accept. The previously mentioned SSE2 refers to a set of CPU instructions that will be needed to run the current version of Flash. The good news is that a lot of the Athlon XP CPUs seem to have this capability, as my experiments running Ubuntu on these old boards only turned up one CPU without SSE2, and it was worked around by installing the older Flash 10

The ability to run videos will be somewhat borderline, and will be affected by what file format they exist in. In short, you will want an .avi file instead of an .mkv file. Processor speed figures into this. The A7V333X mainboard takes up to a [3000+ Athlon or Sempron]("http://www.cpu-upgrade.com/mb-ASUS/A7V333-X.html") - your board version will figure into the CPU capabilities

 By far the biggest annoyance you will encounter comes when you try to burn a DVD - hardware acceleration is turned off by default and you will not be able to turn it on, even if you tried an install of Ubuntu 12.04 LTS instead of the current Ubuntu 14 - a DVD burn will take the better part of an hour, during which, you won't be wanting to do much else with the computer, lest you create a coaster, and waste all the burning time

---

### Post by jdbic on 2015-02-04
Well, I took the easy way and did the erase disk and install Ubuntu, chose the correct drive 'sdb'. Didn't see where to make sure where the grub goes. So on went the install , It was successful. But I don't see windows as a boot option. I guess I blinked. Still learning and I'm not upset either. Been reading posts etc. on this forum. So I have already downloaded Hino for video capture from my old Sony camcorder.


Nice info Omo, I'll look into see if I can get a faster cpu for real cheap and think if I really want to open the case and do surgery.

---

### Post by Bashing-om on 2015-02-04
jdbic; Great .

Making good progress ..
OK:
> 
 But I don't see windows as a boot option

Again, lets take the easy way out:
boot ubuntu to the desk top. Key combo ctl+alt+t to get a Command Line Interface - 
execute terminal command:
```

sudo update-grub

```
I expect this command to pick up and chainload Windows as a boot option on ubuntu's grub boot menu.

Reboot to see the effect.

[INDENT][INDENT]many paths to 1 end
[/INDENT][/INDENT]

---

### Post by jdbic on 2015-02-04
tryed that  sudo update-grub
[sudo] password for bic:  Get this and cannot get  response from key board

---

### Post by Bashing-om on 2015-02-04
jdbicl : Right ..

Normal that you see nothing when the password is entered, 
at " [sudo] password for bic: " blindly enter your password and hit the enter key.
No response is a security measure .

[INDENT][INDENT]and just keep on keep'n on
[/INDENT][/INDENT]

---

### Post by Omo on 2015-02-04
> **jdbic said:**
> I'll look into see if I can get a faster cpu for real cheap and think if I really want to open the case and do surgery.The fastest fits-anywhere CPU won't be real cheap, (about $20) on account of other folks having the same idea, but if you do have the 2.01 version of the board, then you might pay half for an upgrade just as good. What you are going to end up with is a basic computer that can perform basic computer functions. It would make a usable backup web-surfing machine, once you upgrade. The video issues were enough for me to abandon any more efforts to work with the old Socket A boards, especially as a modern desktop machine can be put together for cheap, with no need to buy a video card.

---

### Post by jdbic on 2015-02-05
sudo update-grub didn't  work. Rebooted went to ubunto.

---

### Post by Bashing-om on 2015-02-05
jdbic; Well !

Let's look and see what the system sees for booting:
```

sudo debconf-show grub-pc
sudo grub-probe -t device /boot/grub
sudo fdisk -lu
sudo parted -l
sudo blkid

```

Which hard drive have you got set for the higher boot priority ?

[INDENT][INDENT][INDENT]maybe it is a Windows' things
[/INDENT][/INDENT][/INDENT]

---

### Post by jdbic on 2015-02-05
Let me guess,  the higher boot priority setting is in the bios page. Here's what I have for the codes [bic@BICKY-JET:~$ sudo debconf-show grub-pc
[sudo] password for bic: 
  grub-pc/install_devices_failed: false
  grub-pc/install_devices_empty: false
  grub2/linux_cmdline:
* grub-pc/install_devices: /dev/disk/by-id/ata-WDC_WD1000BB-00CAA1_WD-WMA8C2133050
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/hidden_timeout: true
  grub-pc/disk_description:
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/kopt_extracted: false
  grub-pc/install_devices_disks_changed:
  grub-pc/timeout: 10
  grub-pc/chainload_from_menu.lst: true
  grub2/kfreebsd_cmdline_default: quiet splash
  grub-pc/mixed_legacy_and_grub2: true
  grub2/device_map_regenerated:
  grub2/kfreebsd_cmdline:
  grub2/linux_cmdline_default: quiet splash
  grub-pc/partition_description:
bic@BICKY-JET:~$ sudo grub-probe -t device /boot/grub
/dev/sdb1
bic@BICKY-JET:~$ sudo fdisk -lu

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcac0cac0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    30732344    15366141    7  HPFS/NTFS/exFAT
/dev/sda2        30732345   195366464    82317060    f  W95 Ext'd (LBA)
/dev/sda5        30732408   112663844    40965718+   b  W95 FAT32
/dev/sda6       112663908   195366464    41351278+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009f428

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   238024703   119011328   83  Linux
/dev/sdb2       238026750   240119807     1046529    5  Extended
/dev/sdb5       238026752   240119807     1046528   82  Linux swap / Solaris
bic@BICKY-JET:~$ sudo parted -l
Model: ATA WDC WD1000BB-00C (scsi)
Disk /dev/sda: 100GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  15.7GB  15.7GB  primary   ntfs         boot
 2      15.7GB  100GB   84.3GB  extended               lba
 5      15.7GB  57.7GB  41.9GB  logical   fat32
 6      57.7GB  100GB   42.3GB  logical   ntfs


Model: ATA Maxtor 6Y120P0 (scsi)
Disk /dev/sdb: 123GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  122GB  122GB   primary   ext4
 2      122GB   123GB  1072MB  extended
 5      122GB   123GB  1072MB  logical   linux-swap(v1)


bic@BICKY-JET:~$ sudo blkid
/dev/sda1: UUID="3C340AB3340A7066" TYPE="ntfs" 
/dev/sda5: LABEL="AUDIOVIDEOS" UUID="0A5B-10D2" TYPE="vfat" 
/dev/sda6: LABEL="video" UUID="06342B3C342B2DDD" TYPE="ntfs" 
/dev/sdb1: UUID="b119c294-1eb9-4604-9c42-ab52a6c94cc5" TYPE="ext4" 
/dev/sdb5: UUID="00710348-3fce-4eee-a639-dec5b35c593e" TYPE="swap" 
bic@BICKY-JET:~$ 
]

---

### Post by Bashing-om on 2015-02-05
jdbic; Yukkie ;

OK, here is what transpired; grub installed to sda and overwrote Windows boot code on that hard drive.

What to do:
Install grub to sdb, 'cuase it is not there at this time:
Work from the liveDVD booted to "try ubuntu" mode.
At the desk top key combo ctl+alt+t will get a command line interface; Execute terminal commands:
```

sudo mount /dev/sdb1 /mnt
sudo grub-install --boot-directory=/mnt /dev/sdb
sudo umount /mnt

```

OK, grub is now installed to sdb - the drive that contains ubuntu ->
Reboot to bios and set the 2nd hard drive as first boot priority such that you are now booting up from the boot code located on the 2nd hard drive.
Boot into ubuntu and gain terminal access ( as above) .. now execute terminal command:
```

sudo update-grub

```

Now it is unknown what the condition of Window's boot code is, Maybe there is something there to pick up , possible not ...
in any event we need to repair Windows' boot code. That I can not help with directly, except advise to use Windows 'fixmbr' tool to (RE-)install Windows boot code to the 'sda' drive.

If Windows boot-code is replaced on 'sda' ubuntu's grub will have to be updated once more to reflect the change in booting code.
once more - once Window's boot code is in place, run:
```

sudo update-grub

```

Booting, once all is straight:
ubuntu or Windows, bios boot priority is set to the 2nd hard drive sdb ;
Windows only, then set bios boot priority to the 1st hard drive 'sda'.

[INDENT][INDENT]really
[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jdbic on 2015-02-05
Did the first three codes, shut down, went to bios changed the order. tried second code and get this [lubuntu@lubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: failed to get canonical path of `/cow'.
lubuntu@lubuntu:~$]

---

### Post by Bashing-om on 2015-02-05
jdbic; Sorry,

 perhaps I should have been the more explicit, as:
> 
 error: failed to get canonical path of `/cow'.

Makes me think that you still tried the commands as if you were in the liveDVD .

I expect that you can now boot ubuntu on 'sdb' with the boot code installed to 'sdb' once you have reset in bios the boot priority to that 2nd hard drive.

OK now booted into the ubuntu install on the hard disk. What results from terminal command:
```

sudo update-grub

```
- The use of Code Tags makes the output much more the readable, and retains formatting:
 code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by jdbic on 2015-02-05
I did the commands in live dvd. Now with the dvd out of the dvd drive I turn on the 'puter and this is what I get now.
Top of the page- ```
 GNU GRUB version 2.02 Beta 2-9 Ubuntu1
```
And this in the middle-```
 Minimal Bash -like line editing is supported. For thee first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions. 
```
and this- grub>_ the low dash is blinking.

Edit: I read the link on code tags but I guess I need to read it again. I am trying to get things right.

---

### Post by Bashing-om on 2015-02-05
jdbic; Hey;

2 things that can cause that condition.
a) The 2nd hard drive is not selected in bios as the 1st boot priority.
b) IF the ''sdb' drive is selected in bios, then the boot code did not install properly, and we will have to go deeper. 

Remember, I think grub is installed to both hard drives and until the Windows' boot code is replaced  on 'sda' either boot code should boot ubuntu. So I must ask you if you are certain of your procedure to change the boot priority in bios to that of the hard drives ?

Code tags: Yeah, ya got it, looks good and readable.

Bios -> grub -> kernel -> initamfs starts the operating system.

[INDENT][INDENT][INDENT]all in the process
[/INDENT][/INDENT][/INDENT]

---

### Post by jdbic on 2015-02-06
I went too the bios, then to boot, then changed to the second hard drive which is the Maxtor, saved then exit. What if I do the code sequence again, in case the boot code did not install right?
 I also found this link```
 [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
``` Think I should try it for xp?

---

### Post by Bashing-om on 2015-02-06
jdbic; Good morning .

Yes that link for restoring XP's boot code is a good one. Keep on mind that Windows(7 ??) is installed onto the 1st hard drive (sda).

If with the boot priority set to the 2nd hard drive, still does not boot, then yeah, will not hurt to reset boot priority, boot the liveDVD and try and (RE-)install grub to 'sdb' .
IF and I stress IF there is still a problem booting from 'sdb' we go a step deeper and rebuild the control files (from that liveDVD). But I can not imagine there is a problem to make this step necessary . But, we can go there .

Mind ya, can redo the boot code as may times as needed, all we are messing with is the code installed to the MBR of the hard drives. Not actually even touching the respective operating systems.

[INDENT][INDENT]no step for a stepper
[/INDENT][/INDENT]

---

### Post by jdbic on 2015-02-07
I tried the link I showed you about the xp fix, but it didn't work. I'm going to try a repair reinstall of xp which doesn't affect any files but the windows files needed to run xp. Still can't get ubunto to boot yet from sdb. 
 Getting back to making sure grub goes to sdb, How do you make sure?

---

### Post by Bashing-om on 2015-02-07
jdbic; Hey hey ;

The quickest/best way I can advise is just to re-install grub, see what errors the system reports:
```

sudo fdisk -lu
sudo mount /dev/sdb1 /mnt
sudo grub-install --boot-directory=/mnt /dev/sdb
sudo umount /mnt

```
where the output of 'fdisk' shows 'sdb' as containing 'ext4' file system. Then you know for sure that 'sdb' is the drive you are working with to install grub to.

Where you are installing ubuntu's grub to the 2nd hard drive 'sdb' AND Windows is installed to the 1st hard drive 'sda' .

It should not be all this trying just to install boot code, but the procedure is precise. Got to address the correct drive(s) at the correct time.


round and around we go
[INDENT][INDENT][INDENT]we are going to stop, somewhere
[/INDENT][/INDENT][/INDENT]

---

### Post by jdbic on 2015-02-07
Did the four codes, here's what I come up with-
```
lubuntu@lubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcac0cac0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    30732344    15366141    7  HPFS/NTFS/exFAT
/dev/sda2        30732345   195366464    82317060    f  W95 Ext'd (LBA)
/dev/sda5        30732408   112663844    40965718+   b  W95 FAT32
/dev/sda6       112663908   195366464    41351278+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009f428

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   238024703   119011328   83  Linux
/dev/sdb2       238026750   240119807     1046529    5  Extended
/dev/sdb5       238026752   240119807     1046528   82  Linux swap / Solaris
lubuntu@lubuntu:~$ sudo mount /dev/sdb1 /mnt
lubuntu@lubuntu:~$ sudo grub-install --boot-directory=/mnt /dev/sdb
Installing for i386-pc platform.
Installation finished. No error reported.
lubuntu@lubuntu:~$ sudo umount /mnt
```
Did this from the live dvd.

---

### Post by jdbic on 2015-02-07
After the last post I rebooted and still get the same page I posted in post #43.
 Oh yea the xp repair didn't work either.
  What if I reinstalled Ubuntu with the second hard drive being set to first priority? The first time the first drive was priority.

---

### Post by Bashing-om on 2015-02-07
jdbic; Hummmm ...

Looks good to me I see no error ... should workie,, So, why does it not !
What is set in the File System TABle ?
```

cat /etc/fstab
sudo blkid

```

And yes, no biggy to (RE-)install, but the boot priority will not be relevant as you will set in bios to boot the install medium. In the installer will direct where to install the operating system.

Maybe try and CHroot into the install from the liveDVD and (re-)configure all of grub ?

[INDENT][INDENT]got to be a stop somewhere
[/INDENT][/INDENT]

---

### Post by jdbic on 2015-02-07
I don't understand- Maybe try and CHroot into the install from the liveDVD and (re-)configure all of grub ?

---

### Post by Bashing-om on 2015-02-07
jdbic; Hello:

Sorry to be ambiguous. Try'n to focus on what ifs.
> 
I don't understand- Maybe try and CHroot into the install from the liveDVD and (re-)configure all of grub ?

If I can come up with no better means to see what the problem is, I am going to suggest we employ this means to RE-configure grub.
Presently I am interested in what the File System TABle directs:
```

cat /etc/fstab
sudo blkid

```
Try'n to understand
[INDENT][INDENT]what is not going on here
[/INDENT][/INDENT]

---

### Post by jdbic on 2015-02-07
Here's what the code says-```
lubuntu@lubuntu:~$ cat /etc/fstab
overlayfs / overlayfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb5 swap swap defaults 0 0
lubuntu@lubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="3C340AB3340A7066" TYPE="ntfs" 
/dev/sda5: LABEL="AUDIOVIDEOS" UUID="0A5B-10D2" TYPE="vfat" 
/dev/sda6: LABEL="video" UUID="06342B3C342B2DDD" TYPE="ntfs" 
/dev/sdb1: UUID="b119c294-1eb9-4604-9c42-ab52a6c94cc5" TYPE="ext4" 
/dev/sdb5: UUID="00710348-3fce-4eee-a639-dec5b35c593e" TYPE="swap" 
/dev/sr1: LABEL="Lubuntu 14.04.1 LTS i386" TYPE="iso9660" 
/dev/zram0: UUID="0c3a5622-1de8-4266-b3f6-0d3029929941" TYPE="swap" 
lubuntu@lubuntu:~$
```

---

### Post by Bashing-om on 2015-02-07
jdbic; My bad, scatter brained:

To get the install's fstab .. gotta mount the install partition ... doh !
From the liveDVD:
```

sudo mkdir /mnt/test
sudo mount /dev/sdb1 /mnt/test
cat /mnt/test/etc/fstab
sudo umount /mnt/test

```

So far though, looks good, see if fstab agrees.

[INDENT][INDENT]still out in left field, somewhere
[/INDENT][/INDENT]

---

### Post by jdbic on 2015-02-08
When booting I still get the page I listed in post #43. We're probably missing some thing that is staring right at us.

---

### Post by Bashing-om on 2015-02-08
jdbic; Hummm...

As we are dealing with 'old hardware" confirm that what you have for an install disk is in fact:
(L)ubuntu 32 bit version -> 
> 
Lubuntu is a faster, more lightweight and energy saving variant of Ubuntu using LXDE, the Lightweight X11 Desktop Environment. It is targeted at "normal" PC and laptop users running on low-spec hardware.

You can confirm that from the liveDVD of Lubuntu you can operate the system - albeit the response is quite slow ?
Were you not at one time booting 'buntu and the problem was that could not boot Window's on 'sda' ?
Please re-affirm my think'n if I am in error .

If indeed you have (L)ubuntu 32 bit and as we have attempted to install grub to the MBR of 'sdb' twice, and still no joy, I do think that next thing is to attempt to install/configure l grub from the liveDVD of Lubuntu in a full CHange Root envionment.

As to fixing Windows boot code on 'sda' I know of no better way than from a Windows' repair CD and running 'fixmbr' . With the caveat that I am not Windows literate.

I still hold this is but a matter of getting the respective boot codes installed properly . Just a matter of how.

We will continue to fight this and find out the reason why 'buntu does not boot. and what it takes to boot Windows.

I still say
[INDENT][INDENT][INDENT]it is all in the process
[/INDENT][/INDENT][/INDENT]

---

### Post by jdbic on 2015-02-08
Yes, the system runs from the live dvd,( this response is using it).
At post #32 it booted to ubuntu but there was nothing on boot up showing to choose which to boot. After post #40 no more boot, would have to use the live dvd.
This is the name in the file properties box from the install icon on the desktop Install- Lubuntu 14.04.1 LTS. I'm sure I downloaded the 32 bit version, but I can't find where it tells me the version.
 I'm ready if you are for the next step ```
to attempt to install/configure l grub from the liveDVD of Lubuntu in a full CHange Root envionment.
```

---

### Post by Bashing-om on 2015-02-08
jdbic; Yeah , let's try :

boot the liveDVD, same same release/version as the (L)ubuntu release that is installed onto :
Now we are going to CHange Root into the install from that liveDVD:
```

sudo mount /dev/sdb1 /mnt/
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount --bind /run /mnt/run
sudo chroot /mnt/ /bin/bash

```
Notice that the prompt is changed and you have '#' in that prompt. It reminds one that they are "root" with supreme authority. Exercise extreme caution and care ! Before executing any command, double check that the command and syntax is exactly as you want . The system is going to do what you tell it to do - no matter the result.

OK, we are in the FULL CHRoot environment.
MAke sure that we have internet connection:
```

ping -c3 ubuntu.com

```
IF you get a response similar to this:
> 
--- ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 162.347/163.413/165.096/1.204 ms

We proceed, ELSE quit and back out of the CHRoot ( as below) ---

We have established the CHRoot, and we have internet connectivity ... here goes:
```

dpkg-reconfigure grub-pc

```
Which launches a install wizard. At the screen to select where to install grub, install grub to 'sdb'. 
space-bar to select drive- 'sdb'-, tab to OK, enter to accept.

When the install wizard has completed, and you are returned to prompt:
Back out of the CHRoot:
```

exit
sudo umount /mnt/run 
sudo umount /mnt/dev/pts
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt

```

Reboot, setting in bios to boot the 2nd hard drive as the 1st boot priority.

It is foreseeable that in this instance that ubuntu has not seen or picked up Windows, will require getting grub's attention IF you want to see the boot menu.
IF ubuntu does not boot and we want to see that boot menu; reboot and as soon as the bios screen clears, depress and hold the right -shift- key.

Do you boot, and/or do you get the ubuntu boot menu ?

[INDENT][INDENT]I do expect ubuntu to be happy happy happy
[/INDENT][/INDENT]

---

### Post by jdbic on 2015-02-08
Words you don't want to read. Still does not boot. I booted with the live dvd. started up firefox so I could copy and paste all of you code. Every thing went as you described. One page in the wizard had configuring etc at the top of the page . There was a list of options. I chose the one that was highlighted that said -keep the local version currently installed. When holding the right shift key down- grub booting- comes on the screen then goes away.
This is one stubborn install.

---

### Post by Bashing-om on 2015-02-08
jdbic; Yuk !

It is a puzzle for sure, look at the brighter side though, this puzzle beats doing jig-saw puzzles.

My memory is somewhat hazy, however we want  NEW config files.
I do think we want to go through the full CHRoot routine again, and install grub.
> 
I chose the one that was highlighted that said -keep the local version currently installed

Let's not go there ..The install wizard will build the config files.

[INDENT][INDENT]that's what I think
[/INDENT][/INDENT]

---

### Post by jdbic on 2015-02-08
This post is before I do the reboot so you can see the results of the codes. Next post will be results of reboot by clicking the power button in the lower right and then reboot in the box that comes up
```
lubuntu@lubuntu:~$ sudo mount /dev/sdb1 /mnt/
lubuntu@lubuntu:~$ sudo mount --bind /dev /mnt/dev
lubuntu@lubuntu:~$ sudo mount --bind /proc /mnt/proc
lubuntu@lubuntu:~$ sudo mount --bind /sys /mnt/sys
lubuntu@lubuntu:~$ sudo mount --bind /dev/pts /mnt/dev/pts
lubuntu@lubuntu:~$ sudo mount --bind /run /mnt/run
lubuntu@lubuntu:~$ sudo chroot /mnt/ /bin/bash
root@lubuntu:/# ping -c3 ubuntu.com
PING ubuntu.com (91.189.94.40) 56(84) bytes of data.
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=1 ttl=53 time=81.8 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=2 ttl=53 time=82.0 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=3 ttl=53 time=80.9 ms

--- ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 80.941/81.636/82.072/0.496 ms
root@lubuntu:/# dpkg-reconfigure grub-pc
Installing for i386-pc platform.
Installation finished. No error reported.
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
root@lubuntu:/# exit
exit
lubuntu@lubuntu:~$ sudo umount /mnt/run 
lubuntu@lubuntu:~$ sudo umount /mnt/dev/pts
lubuntu@lubuntu:~$ sudo umount /mnt/sys
lubuntu@lubuntu:~$ sudo umount /mnt/proc
lubuntu@lubuntu:~$ sudo umount /mnt/dev
lubuntu@lubuntu:~$ sudo umount /mnt
lubuntu@lubuntu:~$ 
```

---

### Post by Bashing-om on 2015-02-08
jdbic; Looks most excellent to me !
> 
Found Microsoft Windows XP Professional on /dev/sda1

even found the Windows XP on 'sda1" !

Awaiting what the boot condition is now .

[INDENT][INDENT]hey, it could happen
[/INDENT][/INDENT]

---

### Post by jdbic on 2015-02-08
Same ,no boot. On the first page of the wiz, Linux command line blank ,push OK. 
2nd page default command line says Quiet Splash. ok
4th was the choice of drive took sdb, there was another option- sdb1.

---

### Post by Bashing-om on 2015-02-08
jdbic; HUmmmm///

Totally not what I wanted to hear !

The 'sdb' option is the one we want, for sure for sure .

I am getting stumped as to what is taking place here ! Let's try and get some more info:
can you boot to grub ?
Try and advise result:
Reboot the machine to boot from 'sdb' ;
As soon as bios screen clears, depress and hold the right -shift- key , do you here get the grub boot menu ?
If yes we continue next to try and boot ubuntu.
In that manual process get some additional guidance from the system.

[INDENT][INDENT]'times I do wonder
[/INDENT][/INDENT]

---

### Post by jdbic on 2015-02-09
When I boot up the motherboard page comes up, when it goes away, I push and hold the right shift key. Prompt pops up at the bottom left of the screen says  grub booting  then goes away. Then I release the shift key. Now nothing is happening except the floating box on the screen that says resolution not optimized.

---

### Post by jdbic on 2015-02-09
Got some good news. I went and did the boot up again, held the shift key, let go when grub booting disappeared. Waited a few seconds. Well you know when nothing is happening people start pushing all the buttons. I didn't, I just pushed the enter key a couple of times. Noticed the hard drive light was blinking. Seconds later ubuntu boots up!

---

### Post by Bashing-om on 2015-02-09
jdbic; Wow !

Now that is something entirely different in my experience - even on older hardware !
I was loosing sleep over this - what in the world was going on .

OK, lubuntu is booted ...
run terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo update-grub

```
this updates the system package management database and syncs with your mirror, installs any updates ( dist-upgrade installs new kernels), and last but not least is grub.

once these are done, reboot and let's see XP able to boot also !

[INDENT][INDENT]just goes to show
[INDENT][INDENT][INDENT]never can tell
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jdbic on 2015-02-09
There is nothing pointing toward a boot for xp. After reboot all updates were installed.
I no longer hold down the shift key.

---

### Post by Bashing-om on 2015-02-09
jdbic; Shucks;

In that case we are back where we were.
In my non-literacy, best I can advise is a Windows XP recovery disk, and fixmbr. But, sure begs the question "Found Microsoft Windows XP Professional on /dev/sda1" and not found now ?
Re-install Windows boot code to 'sda'
set bios to boot 'sdb' and once booted to ubuntu 'update-grub' to pick up and chainload Windows boot code onto ubuntu's boot menu.

[INDENT][INDENT]if I knew better
[/INDENT][/INDENT]

---

### Post by jdbic on 2015-02-09
I was doing good for a while ,but now...   How do install the windows boot code to sda or how do I find it. I'll do the mbr from the recovery console on the windows disk and see what happens.

---

### Post by jdbic on 2015-02-09
Ok, I went to the recovery console and ran fixboot. I was going to run fix mbr but a message said it could damage all partitions on the drive. I didn't want to risk doing all this work again, do you? If you do I'll run it and see what happens . Otherwise I'll let it sit the way it is for a while. I can take all the files I need off of the c: drive usihg ubuntu. If ubuntu can write to the c: I'll use it as is.
 I switched the the drives for the fixboot and when I exit to see if xp boots , ubuntu does. 
 Being that xp didn'y boot I didn't do 'update-grub', should I?

---

### Post by Bashing-om on 2015-02-09
jdbic; Sorry;

Hate to disappoint you, I still am not Windows literate. I can not tell you how or what to expect when repairing Windows boot .
Hang loose, others here on the forum do possess that knowledge and experience.

As XP is no longer supported, and is a big security risk to use it; perhaps better left alone (??).
And YES, ubuntu can get your personal files off the Windows system. And as well read and write to the NTFS file system of Windows.

As to 'grub-update' If nothing is re-written there will be no need to update grub . But, can not hurt to do so IF the ubuntu system is intact.

Until such time that the Windows boot code has been confirmed, there is not much else that can be done. I see no point in looking for something ( 30_os-prober ) that is not there.

[INDENT][INDENT]another one of those
[INDENT][INDENT][INDENT][INDENT]a job only Windows can do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jdbic on 2015-02-09
So, on that note, I thank you very much for your time, effort and especially your patience. I think this puzzle has been solved. Do you agree?

---

### Post by Bashing-om on 2015-02-09
jdbic; Hey, no;


We know the solution to this puzzle ;
The final solution is to get XP to boot. - even though it is not an 'buntu problem; We are here to help, just because you choose to use 'buntu and XP is a part of your operating system. 

I work hard because I am a member of this community, and I want you as a member also. The more the merrier !
Never can tell too, what I might learn in the process.

These threads are under surveillance , and I am sure someone will advise on a means to (re-)install XP's boot code to 'sda' .

Not done, 'till it is done .
[INDENT][INDENT]we aim to please
[/INDENT][/INDENT]

---

### Post by jdbic on 2015-02-09
Alright then, we shall continue on.

---

### Post by Mark Phelps on 2015-02-12
Use the details in the link to restore the Windows boot loader: [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader]("https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader")

---

### Post by Bashing-om on 2015-02-15
jdbic; Hello;

> **jdbic said:**
> Alright then, we shall continue on.

Long time no hear. If this matter is now at an end,
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]'till our next adventure
[/INDENT][/INDENT]

---

### Post by Topsiho on 2015-02-16
I think that this very old processor is way too slow now.
The link Grahammechanical gives 2001 as the year this processor appeared on the market, but I seem to remember that I bought my computer, with exactly that processor, in the previous millennium. This computer is extinct for years now :)
I computed thousands of seti observations using this computer, for a number of years, without a hitch, until 2002 (I think).

Topsiho

---

### Post by jdbic on 2015-02-16
I apologize for the laps in time since my last post . I was away. I tried to repair xp with the install disk but got no where. Tried fixboot and fixmbr. Ubuntu is working so far. I'm trying a program called Kino to capture video from my old Sony camcorder. 
 When a thread is marked solved can it still be posted to? If not for the xp part, I think the thread is solved. I haven't reformatted the c: drive yet incase I figure something out. After all many have said I'm using a dinosaur. I do thank all for their help.

---

### Post by Bashing-om on 2015-02-16
jdbic; Nope;

Leave the thread open 'till the situation is resolved.
About that 'dinosaur'. do not count it out. May not jump as high as  current innovations in infrastructure and hardware to meet that would want, but it still jumps.

I too run an old, obsolete system ..  more than meets my needs -> even after all these years.

[INDENT][INDENT][INDENT]does it's job;
[INDENT][INDENT][INDENT][INDENT]good 'nuf
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

