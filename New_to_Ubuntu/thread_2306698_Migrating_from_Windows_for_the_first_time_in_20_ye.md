---
title: "Migrating from Windows for the first time in 20 years."
date: 2015-12-17
forum: New to Ubuntu
---

### Post by felix39 on 2015-12-17
Hi there, 

I'm about to use Ubuntu with Unity as the main OS on my machine. Mainly because Linux seems to be more terminal oriented then windows, which is good for my purposes to take over the world :D
I will not yet give up entirely on Windows. My plan is to configure a VM for whenever I need a fall back. I have read that Windows runs incredibly well as a virtual machine on Linux via KVM/Qemu. If it works well enough I might continue using MS Office (especially OneNote) and Photoshop like that. Maybe I leave the VM open in a workspace at all times and set up Ubuntu to automatically run it on startup - if possible.

Before I dump my current W7 installation I thought it'd be good to wrap my head around some details.

First thing that bothers me is my unknowingness of the Linux filesystem and its structure. I wouldn't know how to mount my two hard drives. I have got a 256GB SSD which I like to use for the most frequently used files (like System files and current project files) and I have a 1TB HDD which I like to use as some sort of archive for completed projects, images, music, etc.
How or where would you mount the drives? Would it be good to partition them?

If you have any other tip I'd be happy to hear it!

---

### Post by yancek on 2015-12-17
With Ubuntu as well as many other Linux distributions, partitions on your drive are available under the /media or /media/user directory on boot.  Generally speaking, anything outside the /home/user directory requires root privileges so if you want a user to be able to write to the partitions, you would need to change owner.  You can change this by creating a mount point (directory) which is customarily under the /mnt directory and putting an entry in the /etc/fstab file for partitions on drives that are plugged in on boot.

---

### Post by deepakdeshp on 2015-12-17
Hello,

You can try Ubuntu and **Mint 17.3** which is based on Ubuntu. You can make a triple boot along with the existing Windows set up. Please taake care to backup all your data before this exercise.

Mint 17.3 has a look and feel of Windows 7


[https://sites.google.com/site/easylinuxtipsproject/mint-install](https://sites.google.com/site/easylinuxtipsproject/mint-install)
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

Linux has Libre office built in and photoshop equivalent.
[http://news.softpedia.com/news/libreoffice-5-0-and-microsoft-office-2013-full-comparison-489920.shtml](http://news.softpedia.com/news/libreoffice-5-0-and-microsoft-office-2013-full-comparison-489920.shtml)
[http://www.ubuntufree.com/top-5-photoshop-alternatives-on-ubuntu-14-04-and-14-10/](http://www.ubuntufree.com/top-5-photoshop-alternatives-on-ubuntu-14-04-and-14-10/)

---

### Post by sandyd on 2015-12-17
> **felix39 said:**
> Hi there, 

I'm about to use Ubuntu with Unity as the main OS on my machine. Mainly because Linux seems to be more terminal oriented then windows, which is good for my purposes to take over the world :D
I will not yet give up entirely on Windows. My plan is to configure a VM for whenever I need a fall back. I have read that Windows runs incredibly well as a virtual machine on Linux via KVM/Qemu. If it works well enough I might continue using MS Office (especially OneNote) and Photoshop like that. Maybe I leave the VM open in a workspace at all times and set up Ubuntu to automatically run it on startup - if possible.

Before I dump my current W7 installation I thought it'd be good to wrap my head around some details.

First thing that bothers me is my unknowingness of the Linux filesystem and its structure. I wouldn't know how to mount my two hard drives. I have got a 256GB SSD which I like to use for the most frequently used files (like System files and current project files) and I have a 1TB HDD which I like to use as some sort of archive for completed projects, images, music, etc.
How or where would you mount the drives? Would it be good to partition them?

If you have any other tip I'd be happy to hear it!

Welcome to the forums.

Note: Before continuing, I assume that you want to get rid of Windows. You do not need to get rid of Windows to install Ubuntu as they can be installed side by side in a dual boot. This may be better for applications that require high performance, or do not perform well in a virtual machine.

[SIZE=4]Choosing a distro and version[/SIZE]
The first thing to start with is to decide what desktop environment and version of Ubuntu you want to use. There are currently 8 official ubuntu flavors (along with vanilla Ubuntu and Ubuntu Server), and they are as follows:
[LIST]
[*]Ubuntu - Unity desktop
[*]Ubuntu Server - No GUI
[*]Edubuntu - Ubuntu for Education
[*]Ubuntu GNOME - Ubuntu with a pure GNOME desktop
[*]Kubuntu - Ubuntu with the KDE desktop environment
[*]UbuntuKylin - Ubuntu localised for China
[*]Lubuntu - Ubuntu that uses LXDE
[*]Mythbuntu - Designed for creating a home theatre PC with MythTV
[*]Ubuntu Studio - Designed for multimedia editing and creation
[*]Xubuntu - Ubuntu with the XFCE desktop environment
[/LIST]

Removing the specialized flavors of Ubuntu and Ubuntu Server, that leaves us with:
[LIST]
[*][Ubuntu - Unity desktop]("http://www.ubuntu.com/download/desktop/")
[*][Ubuntu GNOME - Ubuntu with a pure GNOME desktop]("https://ubuntugnome.org/")
[*][Kubuntu - Ubuntu with the KDE desktop environment]("http://www.kubuntu.org/")
[*][Lubuntu - Ubuntu that uses LXDE]("http://lubuntu.net/")
[*][Xubuntu - Ubuntu with the XFCE desktop environment]("http://xubuntu.org/")
[/LIST]

Each flavor in the above list has a different desktop environment. If you have a slower or less graphically powerful PC, try Lubuntu or Xubuntu. Otherwise, try Ubuntu/Ubuntu GNOME/Kubuntu. You can test all of the flavors just by downloading the ISO from the flavor and either [burning a DVD disc]("http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows"), or [writing the ISO to USB]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows").

You can then boot from the USB/DVD, and select "Try Ubuntu" to test out Ubuntu. Ubuntu will not be installed to your disk, instead it will run from the DVD/USB and be loaded into your RAM.

As of now, there are currently two versions of Ubuntu: 14.04 and 15.10. 14.04 is a LTS (Long Term Support) release, and will be supported until April 2019. Ubuntu 15.10 is not a LTS release, and will be supported until July 2016. Ubuntu 15.04 is still available, and supported, but I would not recommend installing it because it is only supported until January 2016.

Installing a LTS release (in this case, 14.04), will allow you to use Ubuntu until April 2019 without upgrading, however will generally not have the latest software. Ubuntu 15.10 is the latest release of Ubuntu with the latest software, but you will have to upgrade in July 2016.

[SIZE=4]Partitioning[/SIZE]
The partitioning is really up to you.

To simplify things a bit, by default, all your files are stored in what is called the "home folder". This is similar to the C:\Users\<username> folder in Windows. You can either:

a) Store your home folder on the SSD, and store larger files on the 1TB drive
b) Store entire home folder on 1TB drive

Note that option b) requires that you format the 1TB volume with a linux filesystem.

For option a), disconnect the 1TB HDD (you don't want Ubuntu to accidentally blow it away :P) while computer is off and choose "Erase disk and install". You can choose to encrypt the installation if desired.

Some users have found it easier to have a separate partition for their home folder as this allows them to reinstall without losing any data. 
If you want to create a separate partition, choose "Something Else". Delete all the partitions (If you have a partition named EFI, do not delete it, it is required for UEFI computers), and create three partitions:

Partition 1: This will be for the OS, choose the size wisely, it should be formatted to ext4 and have a mount point of '/'
Partition 2: This will be for your home folder, it should be formatted to ext4 and have a mount point of '/home'
Partition 3: This will be for the swap partition, it has the same purpose as the paging file on Windows. If you want to be able to hibernate, the swap partition must be larger or equal size to your RAM.

After the installation, reconnect the 1TB drive before booting and you will find the 1TB drive in your file manager.

For option b), choose "Something Else". Delete all partitions on the 1TB drive, and create a new partition spanning the whole drive. You can then follow the instructions above for having a seperate home folder.

If using the "Something Else" option, be sure that the boot loader is set to be installed on the SSD, not the HDD.

---

### Post by bab1 on 2015-12-18
> **felix39 said:**
> ...
First thing that bothers me is my unknowingness of the Linux filesystem and its structure. I wouldn't know how to mount my two hard drives. 

I have got a 256GB SSD which I like to use for the most frequently used files (like System files and current project files) and I have a 1TB HDD which I like to use as some sort of archive for completed projects, images, music, etc.
How or where would you mount the drives? Would it be good to partition them?

To mount a partition file system you use (either directly or indirectly) the mount command.  the root user is the only user that can mount the partition unless you configure it otherwise.  Ubuntu uses sudo to execute root only commands.  The command would be something like this from the terminal```

sudo mount <UUID=<UUID of the partititon>  <mount point in file system>  -o <mount options> 

```
You can mount the partition at boot time by configuring it via the /etc/fstab file.  The /etc/fstab file can only be edited as the root user (using sudo)

For partitions that are to be used by Ubuntu only I would use format the partitions for the ext4 file system.  Remember that the file system choice is relative to the local host's OS.  Even if you are storing files for a Windows machine there is no need to format the partition with the NTFS file system.

You do not need to mount these disks at /media, but if you do nothing they will be mounted there if at all possible.  The rub is that they may not always be mounted at the same location.  If you want consistency you should manage the mounting process either by a script or by configuring the /etc/fstab file.

The convention for temporary auto mounting of USB devices is /media.  The convention for temporary mounting of partitions with data is /mnt.  If the mount is to be persistent (once again, via script or fstab) you can mount the partition anywhere in the file system.  This could be something like /data but you can really mount it anywhere below / (the root of the file system hierarchy).   Linux has a file system hierarchy convention but nothing is hammered in stone.  I mount my storage devices under /srv which is the convention for data that is managed via various servers (i.e. http, SMB or NFS etc.)  See [**here**]("https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") for more information.

---

### Post by HermanAB on 2015-12-18
Note that with Linux you are free to do things any which way you want.  There is no Linux police that will come and toss you in the brig for not following the Linux Standards Base.

So if the disk and the machine is yours only, then you can mount the portable disks under your home directory if you want and you don't need to partition them either.  You could use the whole disk for a Linux file system, unpartitioned.  Windows doesn't like it when a disk is not partitioned, but it cannot read Linux file systems anyway, so hoo cares?

If you want to know the gory details, google for fdisk and mkfs and read the man pages.  If you are disinclined, then use gparted.

---

### Post by SeijiSensei on 2015-12-18
> **felix39 said:**
> First thing that bothers me is my unknowingness of the Linux filesystem and its structure.

A good overview is here: [http://tldp.org/LDP/intro-linux/html/sect_03_01.html](http://tldp.org/LDP/intro-linux/html/sect_03_01.html)

> I wouldn't know how to mount my two hard drives. I have got a 256GB SSD which I like to use for the most frequently used files (like System files and current project files) and I have a 1TB HDD which I like to use as some sort of archive for completed projects, images, music, etc. How or where would you mount the drives? Would it be good to partition them?

During installation choose "something else."  You can then specify the SSD for /, the "root" of the filesystem.  If you are intending to preserve Windows in a "dual-boot" arrangement, you'd need to first run the defragmenter utility in Windows then repartition the drive to make space for the Linux filesystem.  If you don't care about keeping Windows, you can use all of the SSD for the root filesystem.

You can mount the HDD under /mnt or /media, but you might want to consider mounting it as /home.  That's where all the user files are stored.  Again you can choose to do this during installation.  You can also create an arbitrary mount point like "/data" and mount the HDD there.

If you want to keep Windows around, and you have a copy of the installation media for Windows, you could consider installing [VirtualBox](https://www.virtualbox.org), then creating a "virtual machine" and installing Windows into that. You might want to consider the opposite arrangement while you're getting used to Linux.  Install the Windows version of VirtualBox on your current OS, then download an image file containing Ubuntu and install that into a virtual machine.  

I usually download images from [http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/) which contains all the various "flavors" of Ubuntu.  The one for vanilla Ubuntu with Unity is here: [http://cdimage.ubuntu.com/releases/14.04.3/release/ubuntu-14.04.3-desktop-amd64+mac.iso](http://cdimage.ubuntu.com/releases/14.04.3/release/ubuntu-14.04.3-desktop-amd64+mac.iso).  If you have an older, 32-bit machine use this: [http://releases.ubuntu.com/14.04/ubuntu-14.04.3-desktop-i386.iso](http://releases.ubuntu.com/14.04/ubuntu-14.04.3-desktop-i386.iso)

---

### Post by felix39 on 2016-01-19
Thanks for all the good information! I dug through it and became very busy setting up the new environment. Now 4 weeks have passed and I got a lot of things done and wrapped my head around a lot, though I'm still in the process..
I ended up deleting Windows entirely from the disk and put it into a VM. As a distro I chose Mint 17.3 and installed it on the SSD Drive. The 1TB HDD is encrypted with TrueCrypt. I wrote a script to decrypt the drive and mount it to /data with certain permissions for my user. To my surprise I found replacements for almost every app that I ran in Windows, even for OneNote. I use [Zim Wiki]("http://zim-wiki.org/") as an replacement and I'm still in the process of moving several hundred pages from OneNote to Zim which is an awful task that can not be automated in a way that makes sense (thanks to MS lock-in).. It is the third day in a row now that I move pages about 8 hours a night ^.^ But it feels good to have all the documents out of the MS cage in an freer and more private and flexible environment. The last thing that I have left for the Windows VM now is the Adobe Create Suite. I tried Gimp and I liked it! I'm very excited about future releases, but for now I have to stick to the Create Suite work wise. Next on the list is Python. I started learning it instead of Bash for writing OS scripts and if I get some air I might use it to write some Plugins for Zim (Zim has some features missing, that I liked in OneNote).
Not much longer and I have the OS ready.  I'm so excited and so happy that I switched to Linux! :D

---

