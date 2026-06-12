---
title: "Help with Win7 Installer issue (driver not found)"
date: 2012-03-19
forum: New to Ubuntu
---

### Post by kyonist1 on 2012-03-19
Hello,

First want to say I'm enjoying Ubuntu 11.10, it is really user friendly.
That being said, I'm having some issues with reformatting my HD.
I am installing Win7 through a DVD. I installed Ubuntu through USB, and I have 1 spare USB drive that can hold drivers, etc.

I have 1 hard drive, at time of virgin installation I did not partition properly so Ubuntu 11.10 was installed in the boot drive, in ext4 system.
Looking at GParted:
/dev/sda
  /dev/sda1 ext4 927.59GB
  /dev/sda2 extended 3.92GB
       /dev/sda5 linux-swap 3.92GB

Basically... I regret not partitioning (had trouble with first install, then got lazy and didn't try to figure out how to solve some issues thus did straight install 0 partitions.

Now I want to create a dualboot, by installing win7 first then ubuntu on a separate partition. Problem as you can see is that I'm having trouble getting Win7 to install. Reading some similar problems I've come across two main issues:
1. After booting from the win7 dvd, the installer informs me I do not have proper DVD drivers, my hardware is Asus 24B1ST, I've grabbed the firmware provided from Asus, which came in form of ASUSDOS.EXE and ASUSWIN.EXE. I placed these on a clean usb drive and tried going through with installation, the Windows installer does not recognize these files as the proper drivers. Installation cannot proceed further.

2. Because I failed to partition properly, I worry that even after solving the driver issue (current issue) that Windows would not recognize the HDD format (ext4) and it may not let me install. I have not run into this problem yet but since all the signs point to this occurring (only 1 partition, in ext4) I may need some help here as well...

Thanks for your time, your help is greatly appreciated.

PS.
I tried to "reinstall" ubuntu using the same USB drive and creating the right partitions that way but it will not give me the "boot options"... If I choose boot order to flashdd it simply loads the "trial" OS, it doesn't give me installer options. (was trying to test my RAM using mem86 that came with the original "Grub"?)

---

### Post by oldfred on 2012-03-19
Windows requires a primary NTFS partition with the boot flag or active partition in Windows. 

You can either have unallocated space (usually just a blank drive) with available primary partitions, so the Windows installer can create it,  or create a primary NTFS partition with the boot flag.

A few have had issues with a primary partition after the extended partition. Windows is just happy with sda1 or first partition. Not sure if it is a consistent issue or not. Also some had to reformat a NTFS partition again with the installer even when it was created in advance.

If you let Windows create partitions it will create 2. One is a 100MB hidden boot/repair partition and the main install is the other. But if created in advance it can install to one partition.

---

### Post by kyonist1 on 2012-03-19
Thanks for a quick reply. Yea NTFS is what I believe I lack, but because my primary drive is essentially my ONLY drive (/... boot flag) it will not let me repartition it using gpartition & such. Therefore as a last resport I am not opposed to reformatting the entire drive, however before I can do so with Win7 DVD it tells me I lack the drivers to use my DVDRW drive, which I think is bogus but it still halts operation...
 
Is there a way to "completely uninstall" or "re-install" ubuntu 11.10 using the original USB boot disk, because after trying repeatedly it warps me to what I think is a virtual box which is not what I want, and doesn't go through the entire install process where it first lets me partition drives. (i.e. it only lets me install a 2nd ubuntu OS apparently on the same partition)
 
Thanks

---

### Post by Miljet on 2012-03-19
You cannot edit a partition that is in use. The proper way is to use a live CD, or in your case, the live USB. Just boot into "Try Ubuntu" and try Gparted from there. Be aware that it will trash your Ubuntu installation, but you are going to re-install anyway. Be sure to back up any important data before beginning.

---

### Post by kyonist1 on 2012-03-19
that's the thing! If I try to boot using my USB boot drive, it looks right, loads OS (quite a bit slower than if not) and automatically jumps to the OS (I'm assuming is virtual i.e. try out ubuntu).
 
It never shows the (i believe is) Grub menu where it asks which OS you want to run or memtest86 etc...
 
 
 
And trying to instal ubuntu using the USB drive within the "OS" it simply starts installing, no option to format or partition or whatever... which I thought was very odd so I cancelled it. 
Are you suggest I try installing via this method and see what happens? Won't I have 2 Ubuntu's on the same partition?

---

### Post by oldfred on 2012-03-19
The installer version on a liveUSB does not use grub but syslinux. But you should get a menu of install or run liveCd. And once booted one of the choices should be install. Did you do a full install to the USB flash drive and not an installer?

Often with liveCds you still have to click swap off in gparted. LiveCD/USB use swap if found on hard drive to speed (relatively) things up. So you have to often have to swap-off to edit partitions.

from terminal post

```
sudo fdisk -lu
```

---

### Post by kyonist1 on 2012-03-19
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00007d07

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1945305087   972651520   83  Linux
/dev/sda2      1945307134  1953523711     4108289    5  Extended
/dev/sda5      1945307136  1953523711     4108288    b  W95 FAT32


SDA 1 is the main partition,
sda2 and sda5 are mystery drives...
I manually reformatted sda5 with the win7DVD's DOS command
fdisk c:
seems utterly useless


I'm now near giving up... should I be looking at nuking the disk using a cd or usb boot?
If it's possible from USB could anyone point to a software that can do it? wipe the entire drive clean? this is seriously frustrating... didn't think using default install would be so problematic...

you're right about GRUB, appears I used something called UniversalUSB Installer 1.8.8.8 
right now if I boot (boot order is 1. Flashdd 2. cd/dvd 3. HDD
if I boot using the LiveUSB it goes straight into desktop, no questions just goes
LOADING OPERATING SYSTEM
. . . . . . . . . . . . . . . . . . . . . . . . .
and bam, desktop.


So to reiterate the problem:
I want to install Win7 first, creating 3 entire partitions.
1 - Win OS 2. Ubuntu OS 3. Data
I'm on a 1TB drive, I'm thinking 
60/20/900

but using the Win7DVD to install it stops before installation giving me an error telling me I'm missing a DVD/CD disk Driver. I've tried using the drivers CD with my mobo but the only driver that's available will not install properly. Cannot proceed further.

Using the LiveUSB does not give me option to install or partition or choose OS. Opening the USB contents within Ubuntu desktop (wubi.exe) attempts to install ubuntu on C (only shows 878gb) or Z (878gb ... don't know what this is) but also fails to finish installation citing an error.

Again, thanks for your help... right now a disk wiper that can operate from a USB would probably be easiest... is there one?

---

### Post by oldfred on 2012-03-19
If you have nothing to save just use gparted from your liveUSB. You may have to swapoff.

The extended partition is a container for logical partitions and your swap is a logical partition taking up the entire extended partition. If you are planning more than 4 partition some will have to be logical. Windows boot partition is the only one that has to be primary.

[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20Windows%20Vista%20/%207%20Partitions](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20Windows%20Vista%20/%207%20Partitions)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Install 11.10 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by kyonist1 on 2012-03-21
thanks for sticking around oldfred,
 
now apparently it's not a hard drive partition issue. I've used Tuxboot to create a gparted boot drive on another USB and repartitioned the HDD to 80GB NTFS 60GB ext4 and 800GB FAT32.
 
It still runs into the problems described before, booting from a Win7 DVD it stops me and tells me there's a ..." CD/DVD device driver is missing... insert disk ... install driver...etc"
 
I'm beginning to suspect there may be some files missing from my DVD. It is an ISO file I grabbed from digitalrivercontent, it's supposed to be their official online distributor... I have a legitimate key for Ult 64bit but installation never got that far.
 
Before repartitioning it into the 80/60/800 I have now, I left it blank (wiped clean) but same error. (then boot up with LiveUSB and repartitioned to what it is now)
still no luck...
 
Following instruction from other boards, I've tried setting different SATA control modes (IDE/RAID/AHCI), did not help.
I've tried my motherboard utility disk to see if any drivers were there... nothing.
 
Thanks for your help, perhaps it's the ISO's fault... to test it I'd probably need either another ISO file or wait for the real DVD to ship... (late April-early May, which is why I opted to try an ISO early)

---

### Post by oldfred on 2012-03-21
Do not create a 800GB FAT partition. FAT cannot store a file over 4GB and has no journal. If you have issues a chkdsk literally may take days. NTFS is much better if you want to use for both Windows and Ubuntu.

---

### Post by Mark Phelps on 2012-03-22
DigitalRiver is the "official" supplier of MS products for download.  

So, downloading from there, unless you got some kind of data streaming problem in the process, IS going to yield a file that will have everything in it.

It won't have drivers for everything, as there are tens of thousands of devices, but it should have drivers for all the well-known SATA controllers, which will then "see" your drives.

---

### Post by kyonist1 on 2012-03-24
Hello,

Thanks for the continued support, this community is really something special.

Regarding my problem, I found out that apparently I had downloaded the "Media Refresh" version, which is often confused when following links, as digitalrivercontent doesn't appear to have a full page.

Nevertheless, I downloaded a new one and it installed perfectly. Sorry to have wasted your time on this silly issue.

For those who experience the same problems (i.e. Prior to installation, win7 tells you you're missing a CD/DVD device driver... etc) Please do check to make sure you have the correct version burned. 
Correct version: 
X17-24395.iso

---

