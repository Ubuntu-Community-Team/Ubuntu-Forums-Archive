---
title: "dual boot ubuntu xp grub loader problem"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by SANDKON on 2008-10-23
I a absolutely new to ubuntu. I have XP. I tried ubuntu + liked it so i installed ubuntu on my external hard drive. made the fatal error of not checking where grub loader would be installed. After message grub loader error 5. Used live cd to install again in correct drive but still cannot boot either xp or ubuntu from drives. message 
grub loader stage 1.5
error 5

with live cd can see xp drive and files. please help

---

### Post by caljohnsmith on 2008-10-23
That's not a good sign, because a Grub error 5 is:
> **Error 5** : Partition table invalid or corrupt
This error is returned if the sanity checks on the integrity of the partition table fail. This is a bad sign.
Sounds like your partition table might need fixing. But first, if you want to be able to boot Windows, boot your Windows Install CD, go to the "recovery console", and run:
```
fixmbr
```
Or if you don't have your Windows Install CD, you can download [Super Grub Disk]("http://www.supergrubdisk.org"), and it will give you an option to install a Windows MBR (syslinux is what they actually use). 

Next, from your Live CD, please open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -l
```
Also, enable all your repositories in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen and we can work from there. :)

---

### Post by alphaniner on 2008-10-23
I think it's possible that what you are seeing is caused by the fact that you installed Ubuntu on the external HD.  You will now need it plugged in whether you want to boot Ubuntu or Windows, because the MBR now points to a file on your Ubuntu partition.

---

### Post by SANDKON on 2008-10-23
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ace39a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         480     3855568+  1b  Hidden W95 FAT32
/dev/sda2   *         481        9732    74316658+   7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a336e8d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      121413   975249891   83  Linux
/dev/sdb2          121414      121601     1510110    5  Extended
/dev/sdb5          121414      121601     1510078+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by SANDKON on 2008-10-23
> **caljohnsmith said:**
> That's not a good sign, because a Grub error 5 is:

Sounds like your partition table might need fixing. But first, if you want to be able to boot Windows, boot your Windows Install CD, go to the "recovery console", and run:
```
fixmbr
```
Or if you don't have your Windows Install CD, you can download [Super Grub Disk]("http://www.supergrubdisk.org"), and it will give you an option to install a Windows MBR (syslinux is what they actually use). 

Next, from your Live CD, please open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -l
```
Also, enable all your repositories in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen and we can work from there. :)
Disk /dev/sda - 80 GB / 74 GiB - CHS 9733 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P hid. FAT32               0   1  1   479 254 63    7711137 [HP_RECOVERY]
 2 * HPFS - NTFS            480   1  1  9731 254 63  148633317 [HP_PAVILION]

disk 2
Disk /dev/sdb - 1000 GB / 931 GiB - CHS 121601 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * Linux                    0   1  1 121412 254 63 1950499782
 2 E extended             121413   0  1 121600 254 63    3020220
 5 L Linux Swap           121413   1  1 121600 254 63    3020157
Disk /dev/sdb - 1000 GB / 931 GiB - CHS 121601 255 63
     Partition               Start        End    Size in sectors
* Linux                    0   1  1 121412 254 63 1950499782
L Linux Swap           121413   1  1 121600 254 63    3020157











Structure: Ok.

---

### Post by caljohnsmith on 2008-10-23
It looks like your partition structure on the sdb drive is OK. Can you set your BIOS to boot the sdb Linux drive on start up? If so, follow these steps to make sure Grub is properly installed to that drive:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```
And then see if you can boot the sdb drive on start up. Let me know what errors it gives if any.

---

### Post by SANDKON on 2008-10-23
> **caljohnsmith said:**
> It looks like your partition structure on the sdb drive is OK. Can you set your BIOS to boot the sdb Linux drive on start up? If so, follow these steps to make sure Grub is properly installed to that drive:
```
sudo grub
grub> (hd1,0)
grub> setup (hd1)
grub> quit
```
And then see if you can boot the sdb drive on start up. Let me know what errors it gives if any.
On the BIOS boot menu there are 2 drives marked as USB.

USB-zip 
USB-FDD 5 I think- Havent tried yet 
also has floppy, LAN, hard disk

Any helpM

---

### Post by SANDKON on 2008-10-23
> **SANDKON said:**
> On the BIOS boot menu there are 2 drives marked as USB.

USB-zip 
USB-FDD 5 I think- Havent tried yet 
also has floppy, LAN, hard disk

Any helpM
In terminal when I input the second command line:
grub> (hd1,0)

Error 27: Unrecognized command

---

### Post by caljohnsmith on 2008-10-23
See my previous post, I corrected the mistake.

---

### Post by SANDKON on 2008-10-23
> **caljohnsmith said:**
> See my previous post, I corrected the mistake.
terminal said success and
Probing devices to guess BIOS drives. This may take a long time.
Should I try to boot now or do I have to wait for the terminal screen to tell me something new?
I did say I was totally new!! Please forgive the stupid questions!

PS Am still doing all this via LIVE CD

---

### Post by caljohnsmith on 2008-10-23
Yes, you can go ahead and reboot, but on startup, you need to select your external drive to boot first. Is your external drive USB or SATA?

---

### Post by SANDKON on 2008-10-23
> **caljohnsmith said:**
> See my previous post, I corrected the mistake.
Edited grub file as suggsted and rebooted 
still getting Grub error message
BIOS is configured to boot
USB-FDD
CDROM
HARD DISK
USB-ZIP
Floppy

Bios has Primary Master as the internal hard disk
and shows as Secondary master something which looks to me like a CDrom drive ( could this be possible?)

Also tried to boot with SuperGrub disk ( written to disk via ubuntu) but nothing happens just grub error

---

### Post by SANDKON on 2008-10-23
> **caljohnsmith said:**
> Yes, you can go ahead and reboot, but on startup, you need to select your external drive to boot first. Is your external drive USB or SATA?
external hard drive is SATA connected by usb

---

### Post by SANDKON on 2008-10-24
> **caljohnsmith said:**
> That's not a good sign, because a Grub error 5 is:

Sounds like your partition table might need fixing. But first, if you want to be able to boot Windows, boot your Windows Install CD, go to the "recovery console", and run:
```
fixmbr
```
Or if you don't have your Windows Install CD, you can download [Super Grub Disk]("http://www.supergrubdisk.org"), and it will give you an option to install a Windows MBR (syslinux is what they actually use). 

Next, from your Live CD, please open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -l
```
Also, enable all your repositories in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen and we can work from there. :)
Used supergrub and on bott menu it gives 3 choices:
Windows XP Professional 5I don't have this only Home edition)
Windows recovery
Ubuntu

When I enter Ubuntu it brings up grub screen
What do I input?

Could the problem be that bios doesn't recognise the external hard drive?

---

### Post by SANDKON on 2008-10-24
Managed to boot into UBUNTU on external HDD!!!! Although GRUb does take some time to boot (is this normal?) 
Now the question is how do I boot into my XP Home on the internal HDD? Boot menu shows XP Professional!

---

### Post by myscam on 2008-10-24
THis may or may not be helpful, but this is what I did.  I had Windows XP already installed on one HD. I have a programme called Acronis Disk Director which also has an OS Selector function, installed via Windows on the first HD. I attached a second HD, then disconnected the first HD (with XP) by physically removing the connector to the motherboard.  I then did a clean install on to the second HD from the Ubuntu 8.04 install cd.  After reconnecting the first HD, the OS Selector software now recognises the Ubuntu OS as one of the options for booting.  Running Ubuntu it will recognise the first HD and I can access the contents.  BUT it will not work the other way round ie while running XP the second HD does not appear at all (in "my computer").  Possibly if I had first partitioned the second HD using XP and then installed Ubuntu onto one of those partitions this problem might have been avoided?

In case you are wondering why, I wanted to have Ubuntu on a completely separate HD so that in case of problems later on the original XP installation would not be affected. This was in the light of some earlier experience that did not go well using Linspire.

I also did a clean install of Ubuntu 8.04 on my laptop  an IBM Thinkpad T42, now four years old.  Everything worked beautifully right from the start, including the wireless card ; there is almost nothing that I need to do that cannot be done using Ubuntu on the laptop.  Hats off and thanks to the Ubuntu team.

---

