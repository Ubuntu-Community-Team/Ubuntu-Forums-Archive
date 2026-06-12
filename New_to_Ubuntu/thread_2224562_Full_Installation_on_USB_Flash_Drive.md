---
title: "Full Installation on USB Flash Drive"
date: 2014-05-16
forum: New to Ubuntu
---

### Post by causeburn on 2014-05-16
Hey Gang,

I have a USB 3.0 64GB flash drive that I want to setup with Ubuntu 14.04 and Tails Linux.

Using YUMI Installer I was able to easily get both ISOs installed on the flash drive, with an easy to use USB bootloader.

I logged into Tails Linux and everything seems perfect, GREAT! but when I log into Ubuntu 14.04 I made lots of changes, added new apps etc, when I shut down and log back in the apps are still there but Ubuntu still acts like I am just a temporary user on the LiveCD, instead of treating the flash drive like a full installed hard drive.

[SIZE=4]**How do I do a full install of Ubuntu 14.04 using YUMI? **[/SIZE]

I did some googling to try to solve the problem but only came across some people recommending I use the alternate Ubuntu ISO and they give instructions from their assuming I am installing linux from a linux machine, which doesn't work for me as my main machine is a Windows 8.1 box.

During the YUMI setup I chose the largest persistent drive size, however with a 64GB flash drive I would love to get that drive size up to 60GB+ for Ubuntu 14.04 (leaving approximately 4GB for Tails Linux).

This is where I am at and I am lost :(

I know this forum is awesome because you have helped me with Ubuntu in the past, so I am throwing myself on the mercy of the Linux gods, I am not worthy but I am willing to listen to your wise, wise words. (Ok enough ass kissing, thanks for the help, honestly :) )

---

### Post by TheFu on 2014-05-16
> 
How do I do a full install of Ubuntu 14.04 using YUMI? 

You can't.  Ubuntu needs a Linux file system, not FAT32 or NTFS.  You'll need to partition whatever device you choose to use and setup grub to control booting of each partition. It would be easier to get another flash drive to install onto.  Yumi doesn't do this. That isn't what it was designed to accomplish.

BTW, flash memory is slow - even when USB3 connected.  USB2 will be almost unbearable (for certain values of unbearable).

---

### Post by oldfred on 2014-05-17
I do not find a USB install to be unbearable, but it is not speedy loading. Once in RAM and cached it runs just as fast. You do have to turn off some settings to reduce writes as writes are very slow.
       
Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

Instructions should be almost identical for 14.04
      Full install - C.S.Cameron post #2
[http://ubuntuforums.org/showthread.php?t=2116798](http://ubuntuforums.org/showthread.php?t=2116798)
Full install of 12.04 to 64GB USB device C.S.Cameron post #3
[http://ubuntuforums.org/showthread.php?t=2092077](http://ubuntuforums.org/showthread.php?t=2092077)

I use gpt partitioning and configure like sudodus' post above even though I do not yet have UEFI, just BIOS.
I use ext4 but turn off journal to reduce writes, partition is smaller so journal does not add much but recovery after corruption may be slow or impossible. I also use noatime setting in fstab.

sudo tune2fs -O ^has_journal /dev/sdb1

Speed on flash drives varies a lot. I do find the inexpensive Microcenter USB3 flash drives are still 10% faster in my USB2 ports.
      
 pendrive speed tests USB2 & USB3 various brands - user sudodus
[http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085](http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085)
Includes links to speed tests and lists some that do not work well.
[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

---

### Post by causeburn on 2014-05-17
That's some good information, thanks Oldfred!

---

### Post by causeburn on 2014-05-17
Is there a linux version that would install easily on a usb flash drive?

---

### Post by monkeybrain20122 on 2014-05-17
> **causeburn said:**
> Is there a linux version that would install easily on a usb flash drive?

All Linux distros as far as I know can be fully installed on a flash drive provided you partition and format your flash drive properly, not with things like YUMI which creates a  multiboot live usb. It just may be kind of slow as already noted.

Basically you partition the live usb with gparted, created ext4 partitions and install like you would in the internal drive, but install the bootloader into the device rather than the default internal drive. See oldfred's links. If it is a multiboot only one distro should be in charge of grub, so for the others either don't install bootloader at all if the option exists (e.g Fedora) or if the option doesn't exist install bootloader in the partition rather than the drive (e.g *buntu), that means for example install bootloader in /dev/sdc5 instead of /dev/sdc.

---

### Post by sudodus on 2014-05-18
All linux versions install easily on USB drives. They are mass storage devices like internal hard disk drives, and are treated in the same way by the system.

But USB is slower than SATA, and particularly the flash memory of pendrives is much slower than hard disk drives and SSDs. There are some exceptions, some USB 3 drives are quite fast, and should be used to get a fast operating system from USB. It is described in one of the [links]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085"), that oldfred posted earlier in this thread.

-o-

So it is worthwhile to select a linux distro with a light or ultra light desktop environment and maybe also light application programs. This makes it fast in spite of the slow USB connection and flash memory.

- Xubuntu with the medium light desktop environment XFCE
- Lubuntu with the ultra light desktop environment LXDE
- some light or ultra light re-spin of Ubuntu 12.04 LTS, for example Bento, Bodhi or LXLE.

You should also consider if you intend to use the pendrive in one computer or to have a portable system, to be used in several computers. Furthermore, you should consider if you need to run it in old 32-bit computers or in new UEFI computers. The same system will not work everywhere, so select either a 32-bit system for 32-bit and 64-bit BIOS computers or a 64-bit system for 64-bit computers with BIOS or UEFI.

Or use more than one pendrive.

-o-

There might be a complication, if you want a full install of Ubuntu (or some other flavour of the Ubuntu family) and at the same time Tails. I think Tails is made to run live. Many distros can boot live from the iso file via grub, but I am not sure Tails is one of them. An alternative is to install Tails in a virtual machine inside Ubuntu, but it would be slower, much slower or impossible if you must run it in an old computer.

*Edit*: I searched the ***linux tails grub and iso*** and found these links, so it seems possible to boot Tails live from the iso file via grub, at least in BIOS mode.

[https://mailman.boum.org/pipermail/tails-dev/2011-July/000429.html](https://mailman.boum.org/pipermail/tails-dev/2011-July/000429.html)
[https://mailman.boum.org/pipermail/tails-dev/2013-December/004538.html](https://mailman.boum.org/pipermail/tails-dev/2013-December/004538.html)

[https://revoltingworld.net/blog/2012/12/12/multi-partition-usb-key-with-bootable-iso-tails/](https://revoltingworld.net/blog/2012/12/12/multi-partition-usb-key-with-bootable-iso-tails/)

---

### Post by causeburn on 2014-05-18
Interesting, I am learning a lot here.

Now to find a linux machine to install linux on the flash drive, hmmm

---

### Post by sudodus on 2014-05-19
> **causeburn said:**
> Interesting, I am learning a lot here.

Now to find a linux machine to install linux on the flash drive, hmmm

You can create an Ubuntu [family] install CD/DVD/USB drive in a computer with Windows. Today it is quite popular to use USB pendrives. I like Unetbootin. See this link for more details

[https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_a_bootable_Ubuntu_USB_flash_drive_from_Windows](https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_a_bootable_Ubuntu_USB_flash_drive_from_Windows)

---

### Post by mastablasta on 2014-05-19
or just use Yumi...

some good info here. i was thinkign of running NAS server from USB (2.0). i guess that won't be a speed problem, since it would use RAM and be on fo rmost of the time. The RaspberyPi does it quite well with SD card. I mean if you use externla USB for data. It could be a write problme though. or not... since i guess data is mostly read and log files could be moved to hard disk.

---

