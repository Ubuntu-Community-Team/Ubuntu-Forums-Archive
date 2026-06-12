---
title: "Setting up a dual boot system"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by DonC69 on 2012-04-27
Hi, I am new to Ubuntu and I have a question concerning dual boot.  I have 3 disks on my computer: disk 0 a 64GB Crucial M4, Disk 1, a raid 0 setup of 2 WD 500GB drives and disk 3 a WD 500 GB drive. Windows 7 Home Premium 64bit is installed on the SSD(C: ). As far as I understand, if I install Ubuntu 12.04 LTS without changing anything in my setup, Ubuntu will overwrite/install the bootloader on the mbr of the first disk, which is the Crucial. I do not want that, I'd rather have Ubuntu install the bootloader on disk 1, where I am going to install Ubuntu on. Is changing the bootsequence in the bios enough, or do I also have to switch the SATA cables in my computer. The SSD is on SATA_0, I believe disk 1 is on SATA1 & 2, but I cannot be sure; there is an enormous videocard blocking my view. I am going to install Ubuntu on D or the unallocated space, not sure yet. I am also asuming, Ubuntu 12.04 LTS, being brand new, won't be having problems with said RAID 0 setup.

Hardware:

AMD 1100T
Gigabyte GA-MA790XT-UD4P (AMD 790x + 750SB)
2x2GB Corsair RAM
MSI HD6950 2GB


[IMG]http://i45.tinypic.com/v41ob9.jpg[/IMG]

---

### Post by anejo on 2012-04-27
In windoze dayz, I would multilboot a localhost XP, a TinyXP and a XP that was joined to a workplace domain.
The first time I installed a distro, I didn't know what to expect... and I was prepared to redo at least the domain XP instance.
So. I was rather surprised to see the grub display take over from boot.ini and display all available options.
This is already well documented... but the key is always to do the Windows installations first and ensure that boot.ini is working for you.
Then you can go ahead and do a Linux install.
It's also a good idea to ensure that a partition is available beforehand but it doesn't have to be formatted to anything...

---

### Post by DonC69 on 2012-04-27
That is not really an answer to my question, although you cannot help it I forgot a questionmark. 

I want to make sure I get the bootloader on Disk 1.

I can google, which I am doing, I just do not know enough about how the bios handles things(and I am insecure), Changing bootorder in the BIOS won't alter the mbr on the SSD, right?

> How does GRUB work?

When a computer boots, the BIOS transfers control to the first boot device, which can be a hard disk, a floppy disk, a CD-ROM, or any other BIOS-recognized device. We'll concentrate on hard disks, for the sake of simplicity.

The first sector on a hard is called the Master Boot Record (MBR). This sector is only 512 bytes long and contains a small piece of code (446 bytes) called the primary boot loader and the partition table (64 bytes) describing the primary and extended partitions.

By default, MBR code looks for the partition marked as active and once such a partition is found, it loads its boot sector into memory and passes control to it.

GRUB replaces the default MBR with its own code.

Furthermore, GRUB works in stages.

Stage 1 is located in the MBR and mainly points to Stage 2, since the MBR is too small to contain all of the needed data.

Stage 2 points to its configuration file, which contains all of the complex user interface and options we are normally familiar with when talking about GRUB. Stage 2 can be located anywhere on the disk. If Stage 2 cannot find its configuration table, GRUB will cease the boot sequence and present the user with a command line for manual configuration.

Stage 1.5 also exists and might be used if the boot information is small enough to fit in the area immediately after MBR.

The Stage architecture allows GRUB to be large (~20-30K) and therefore fairly complex and highly configurable, compared to most bootloaders, which are sparse and simple to fit within the limitations of the Partition Table.

---

### Post by powder on 2012-04-27
During the installation you will have an option to select where to install the bootloader.  You will most likely have the options SDA, SDB, or SDC.  Disk 1 will likely be SDB.

[IMG]http://img684.imageshack.us/img684/7977/mbrpariondemo16.png[/IMG]

---

### Post by oldfred on 2012-04-27
Only if you use manual install or Something Else do you get the screenshot powder shows you. And you want to use manual install.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?

Ubuntu does not have RAID drivers as default in the standard desktop install as that is uncommon. You have to use the alternative installer or server installer. Depending on the type of RAID, you can add the raid drivers. But if installing to a non-RAID drive it does not matter during install.

Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
sudo apt-get install lvm2
sudo apt-get install mdadm

But I do not see your RAID in the Windows partition layout you show.
What does this show? And if you have RAID install mdadm first and installing to liveCD will not install it nor use it during install(I think?):

sudo fdisk -lu

---

### Post by DonC69 on 2012-04-28
Oldfred, I have installed 12.04 LTS before your post and my approach failed for it installed the bootloader on the M4..... Probably should have connected the Raid setup to SATA ports 0 and 1 on my mobo. Everything works, sort off, at least Ubuntu boots. I am happy that the raid setup works,but I am still on the virge of tilt, because I can't get some of my hardwaredevices to work. But that's another story and if I need help with that, I will start new threads.

edit: for some reason the Windows 7 diskmanager does not show RAID, but when I select Disk1 and click on properties, I get the following window. Don't know if you were looking for that, probably not for it doesnt show anything useful, but maybe you wanted to make sure I indeed use RAID. I use the RAID capabilities of the AMD SB750 southbridge.

[IMG]http://i46.tinypic.com/2yvugc8.jpg[/IMG]

---

