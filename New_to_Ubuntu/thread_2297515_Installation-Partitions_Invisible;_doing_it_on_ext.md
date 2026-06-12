---
title: "Installation-Partitions Invisible; doing it on external HDD. Get GRUB?"
date: 2015-10-04
forum: New to Ubuntu
---

### Post by Salty-san on 2015-10-04
I can't see partitions I make on my external HDD when I boot, after  making changes with GParted and even the installer (from live USB). I've been reading around, and it seems I either need commands from terminal to configure stuff, or instal things on my external HDD? All this UEFI, BIOS, GRUB thing I am not familiar with as I didn't do installs before and I am also a Newbuntu (copywriting that ;p) so terminal commands might as well be dead languages to me. So I could use some guidelines or precise reference material. Booting only shows the Toshiba drive.

This is how I set up my partitions with GParted, with the big chunk of the space wanting to keep it free for stuff and visible in Windows: [http://oi57.tinypic.com/6s70pf.jpg](http://oi57.tinypic.com/6s70pf.jpg) It's a Lubuntu.

And in the install screen I set up the space for Linux as Primary ext4  journaling system with mount point / and the Swap Space as Primary too. I  tried the install both with it mounted and unmounted I believe, neither  worked. [http://oi58.tinypic.com/2ltaxl.jpg](http://oi58.tinypic.com/2ltaxl.jpg)

I want to avoid installing on the laptop drives (full and without working OS). And I want to try and make it an actual install that works from HDD as opposed to just another live medium. I could make do with that for what I need, but I figure I may as well take the opportunity to try doing new things. Help would be appreciated.

---

### Post by Bashing-om on 2015-10-04
Salty-san; Hello. Welcome to the forum.

26 Gigs on device sdc should work .
I work best from terminal. Please boot up the liveDVD(USB) and provide the outputs - between code tags - of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

We count the numbers and make sure all is correct.
Then I can surmise we need to (RE-)install grub ( GRand Unified Bootloader) to the drive containing ubuntu.
Could be all that is required.

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by Salty-san on 2015-10-04
Alright, sounds good. Here's the stats...

```
Disk /dev/loop0: 628.3 MiB, 658841600 bytes, 1286800 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x7c12e647

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048    206847    204800   100M  7 HPFS/NTFS/exFAT
/dev/sda2          206848 317941759 317734912 151.5G  7 HPFS/NTFS/exFAT
/dev/sda3       317941760 625139711 307197952 146.5G  7 HPFS/NTFS/exFAT

Disk /dev/sdb: 15 GiB, 16148070400 bytes, 31539200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00061544

Device     Boot Start      End  Sectors Size Id Type
/dev/sdb1  *     2048 31539199 31537152  15G  c W95 FAT32 (LBA)

Disk /dev/zram0: 963.9 MiB, 1010659328 bytes, 246743 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk /dev/zram1: 963.9 MiB, 1010659328 bytes, 246743 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
lubuntu@lubuntu:~$ sudo parted -l


```

---

### Post by yancek on 2015-10-04
I would suggest that instead of putting the operating system which needs to boot beyond the 968GB point of the usb drive, you put it at the beginning and put the windows partition at the end.  The windows partition is going to be used for data since it is impossible to install it to a USB drive so it's location doesn't matter.

You mention windows but do not indicate whether you actually have windows on an internal drive and if you do which release of windows you have.  If it is 8 or later it will likely be using UEFI and you will have to deal with that.

What software did you use to create the bootable flsh drive with which to install Lubuntu.
You also state that you tried to install but it "didn't work".  That's a little vague.  Exactly what happened.  Did you get to installation type window?  Which installation type option did you select?.

---

### Post by Bashing-om on 2015-10-04
Salty-san; oooppss ..

Totally unexpected configuration.
I have no idea :
> 
Disk /dev/zram0: 963.9 MiB
Disk /dev/zram1: 963.9 MiB

What to advise as I have no experience or knowledge of 'zram'.

Others will have to pick up my slack and advise.

[INDENT][INDENT]sometimes I do not know
[/INDENT][/INDENT]

---

### Post by Salty-san on 2015-10-04
> **yancek said:**
> I would suggest that instead of putting the operating system which needs to boot beyond the 968GB point of the usb drive, you put it at the beginning and put the windows partition at the end.  The windows partition is going to be used for data since it is impossible to install it to a USB drive so it's location doesn't matter.

You mention windows but do not indicate whether you actually have windows on an internal drive and if you do which release of windows you have.  If it is 8 or later it will likely be using UEFI and you will have to deal with that.

Oh yeah I read about the order of partition somewhere. I guess I could try it. I know Windows won't install externally, I just meant in case I will be using the HDD on a different machine, or for the future if I get Windows, would be nice to get full access to that data without needing Linux.

> What software did you use to create the bootable flsh drive with which to install Lubuntu.
You also state that you tried to install but it "didn't work".  That's a  little vague.  Exactly what happened.  Did you get to installation type  window?  Which installation type option did you select?.

Oh, oops..I mean it didn't work to boot into it after it installed. The installation was succesfull, there wasn't even types to choose from afair. It went all the way, said it completed sucesfully and I tried restarting but just won't boot from external. BIOS only sees it as external medium, so one partition.

And honestly I think the problem might be with the way this USB was done. I forget what I used to make it, it was on Win7 but I tried many things for many distros and they wouldn't work so I just stuck to what did. I think it may have been UNetbootin or Rufus but maybe it was something else and obscure. 

But the thing is that it is NOT a permanent changes live USB. I didn't gave it space for that to save on time on the burn. So it just resets everything every time I boot, which is kind of convenient for many things like protection.


> Salty-san; oooppss ..

Totally unexpected configuration.
I have no idea :

What to advise as I have no experience or knowledge of 'zram'.

Others will have to pick up my slack and advise.

[INDENT][INDENT]sometimes I do not know
[/INDENT]
[/INDENT]



Lol it's ok. Like I said above it may be the Live USB itself that is a problem. But at least I know now. What is zram though? 

Thing is, the USB is like 16 GB, but Lubuntu only installed for 1 GB or so on it. The rest of the space is not visible or available. It may have been a burn problem, idk, but then the installation does go through so maybe it is my partitioning. At least I have a more clear view now.

---

### Post by grahammechanical on 2015-10-04
zram? Here you go

[http://askubuntu.com/questions/174579/how-do-i-use-zram](http://askubuntu.com/questions/174579/how-do-i-use-zram)

The fact that 2 zram block devices are showing up indicates that there are two swap partitions around. I have 2 hard drives. They each have a swap partition and I have installed zram and so I get /dev/zram0 & /dev/zram1 showing up in the Disks utility & sudo parted -l

Regards

---

### Post by yancek on 2015-10-04
> I know Windows won't install externally

Correct.  If you try to install windows to an external usb or an IEEE 1394 device, you get the message below.

> windows setup does not support configuration or installation to a disk connected through usb or IEEE 1394 ports

> I just meant in case I will be using the HDD on a different machine, or  for the future if I get Windows, would be nice to get full access to  that data without needing Linux.

You can access multiple ntfs partitions on an external drive, you just can't install.  Your post seems to indicate you are just using it for data putting the ntfs as the second or third partition should not matter.

> So it just resets everything every time I boot
 
That is not an installation.  It is simply putting a bootable Live CD of Lubuntu on a flash drive and that is expected behavior.  You will not be able to save and data on reboot, it is the way it is designed.  It is possible to create a bootable flash drive with persistence but from what you have posted, you did not do that.  You can use unetbootin to do it as well as some other software.

> 
Thing is, the USB is like 16 GB, but Lubuntu only installed for 1 GB or so on it.

That is correct and that is expected behavior for a Live CD on a flash drive.  You can use the rest of the drive on which to store data by shrinking the partition on which you have the Live CD and creating a second partition for data.   I don't think you could do that with windows because windows will only see the first partition on a flash drive.  To be able to use it from the flash drive though, you would need a persistent install which you do not have.

Based on the information in the images you posted in your initial post, it looks to me like you put a Live CD at the end of your 1TB partition rather than doing an actual install.  A full installation of Lubuntu will take up a lot more space than is shown in the image in your first post for the ext4; 564MB.  

It's pretty difficult to know what you've actually done.  Making notes during the process so that you have information to post when something goes wrong would be helpful.  You obviously have another operating system on an internal drive and what that is and how it is installed would or could be part of the problem also.

---

### Post by Salty-san on 2015-10-07
> A full installation of Lubuntu will take up a lot more space than is  shown in the image in your first post for the ext4; 564MB.

Actually that was simply due to formating the partition as ext4. Just takes up that much space for some reason which is weird. The actual install kinda varied just above 3GB and it says it needs minimum of 4.5 free space on drive for install, so maybe it's just in case, but idk what could have went wrong.

Anyway guys, I tried again this time wit ext4 at start, and it's still the same. I also did it without automatic updates on install, still the same. I've been thinking about what it could be, and maybe the BIOS/machine just doesn't recognize ext4 type formating, this is the only thing I can come up with. It might also be that this live USB I have uses grub 1 so maybe that's why, idk...

I just made another live bootable FAT32 partition on the HDD instead...this time it was a higher version of lubuntu by accident, which I notice uses Grub 2 whereas the installer for the one I had said Grub 1, so maybe that was it. Not that it should matter if it is a live disk, but now when I boot the HDD it gives a separate UEFI:Toshiba line in boot options.

I posted to share the conclusion, but I am still kind of interested in knowing what might have been the problem, in case I need to do a full install on external media in the future.  Thanks though.

---

### Post by oldfred on 2015-10-09
You show Windows installed to MBR(msdos) partitioned drives with BIOS boot.
But then you mention UEFI:?

UEFI & BIOS are not compatible, Once you start booting in one mode you cannot switch. Or you cannot dual boot from grub menu with systems installed in different boot modes. You can dual boot if not in same boot mode only from UEFI boot menu. And you may have to turn on/off UEFI or CSM/Legacy/BIOS boot settings.

Since Windows is BIOS boot, better to install Ubuntu in BIOS boot mode to external drive. 
And now you boot install flash drive UEFI or BIOS is then how it will install.

       [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
            Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

            Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by Geoffrey_Arndt on 2015-10-09
Salty . . . instead of all these weird installs via Live images (of who knows what old versions??:confused::confused: ) . . . . why don't you just try a standard full install on a separate partition of your internal hard drive?   Then, learn Linux  . . . take a course or two, read quality publications, etc.    That'll help clear up the cobwebs.

---

