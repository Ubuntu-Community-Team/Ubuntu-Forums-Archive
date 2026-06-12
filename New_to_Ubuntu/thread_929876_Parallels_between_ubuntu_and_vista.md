---
title: "Parallels between ubuntu and vista"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by gasciut on 2008-09-25
ok so i had ubuntu 8.04 and Windows Vista put on a partitioned hard drive.
i would like to have parallels running through ubuntu so i can have a windows while im using ubuntu (its a pain to have to restart anytime).  another thing is i cant see the other drive. by that i mean i cant see the c: drive when im on ubuntu and cant see the d: drive when im on vista.  is there anything i can do to set up parallels through ubuntu and have a windows desktop in ubuntu

---

### Post by shifty_powers on 2008-09-25
does it have to be parallels?

i've always used virtualbox, which is free, open source and generally very good.

oh and it's in the repositories as well :D

some people swear by vmware mind... there are tutorials for vmware which are easy to find...

---

### Post by kansasnoob on 2008-09-25
> **gasciut said:**
> ok so i had ubuntu 8.04 and Windows Vista put on a partitioned hard drive.
i would like to have parallels running through ubuntu so i can have a windows while im using ubuntu (its a pain to have to restart anytime).  another thing is i cant see the other drive. by that i mean i cant see the c: drive when im on ubuntu and cant see the d: drive when im on vista.  is there anything i can do to set up parallels through ubuntu and have a windows desktop in ubuntu

As far as I know the answer is no. You might prefer a virtual machine like VMWare or Virtual Box, I hate it:(

However you can access your Windows files from Ubuntu using ntfs-config or ntfsprogs, but **you can also break the hell out of things if you're not careful!**

A bit here about ntfs-config:

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

And ntfsprogs here:

[http://www.linux-ntfs.org/doku.php](http://www.linux-ntfs.org/doku.php)

Both are available in Synaptic, but be forewarned: Neither will enable you to run Windows programs from Ubuntu, in fact unless you absolutely know what you're doing you are likely to really break things!

---

### Post by kansasnoob on 2008-09-25
> **shifty_powers said:**
> does it have to be parallels?

i've always used virtualbox, which is free, open source and generally very good.

oh and it's in the repositories as well :D

some people swear by vmware mind... there are tutorials for vmware which are easy to find...

Shifty, My comment about hating virtual machines is just a personal opinion. I realize some people prefer it and that's great:)

That's the beauty of Linux: so many choices and options - so little time:)

---

### Post by gasciut on 2008-09-25
so with virtual box i will be able to run ubuntu as the main os and have vista running at the same time in one of the multiple windows you can have in ubunutu?

---

### Post by gasciut on 2008-09-25
I just put Virtual Box on ubuntu.  only problem is i cant find my vista os to run it on. it wants me to make a new virtual box but i want to set it up to the vista that i have on the partioned drive, except i cant see the drive...is there anything i can do?

---

### Post by shifty_powers on 2008-09-25
it will not be one of the desktop's as such, but you can have vista running in a window within ubuntu, certainly.

so basically, ubuntu would be your main os and vista would be a window like firefox and any other program, being easily switchable between the two.

if you want vista to run as an acutal desktop, almost like a wallpaper ina a way, i think it can be done but i'd have to look it up... (heh, didn't explain that last bit very well but nvm)

---

### Post by cariboo on 2008-09-25
Canonical does offer Parallels, but you have to pay for it to use it. See here:

[http://shop.canonical.com/index.php?cPath=19&osCsid=4642e7206b28f9a460acaa335f0e2e1c](http://shop.canonical.com/index.php?cPath=19&osCsid=4642e7206b28f9a460acaa335f0e2e1c)

Jim

---

### Post by squaregoldfish on 2008-09-25
> **gasciut said:**
> I just put Virtual Box on ubuntu.  only problem is i cant find my vista os to run it on. it wants me to make a new virtual box but i want to set it up to the vista that i have on the partioned drive, except i cant see the drive...is there anything i can do?

It's not officially an option in VirtualBox yet, but apparently some people have managed it. If you do a quick Google search for 'virtualbox partition', you should be able to find something. Never done it myself, so I can't help you directly :(

Steve.

---

### Post by shifty_powers on 2008-09-25
realistically you would have to do a new install of vista. using an existing install of vista from parallels would be a pain in the ***. not even sure if it would be possible..

---

### Post by gasciut on 2008-09-25
But with virtual box or any other software, how would i even be able to access the already partioned hard drive...thats what i cant figure out

---

### Post by shifty_powers on 2008-09-25
already partitioned hd?

do you mean a drive image you've created previously using parallels or an actual hd partition.

they are not both the same thing...

---

### Post by jerome1232 on 2008-09-25
I have a feeling if you do get virtual box to boot that real drive, vista will throw a hissy fit due to the massive hardware changes it will see (Virtual machines emulate certain hardware)

As far as accessing your existing ntfs partition can you post the output of these commands and we can help you with mounting it. The first command lists all currently mounted disks and the second lists all drives seen by Ubuntu, mounted or not.

```
mount
sudo fdisk -l
```

---

### Post by squaregoldfish on 2008-09-25
If you run a partition manager (gparted, for example), you'll be able to see all the partitions on your disk, including the Vista partition. It will have been given a label (eg /dev/hda1 or /dev/sda1 - or another number). When you set up VirtualBox to access your Vista partition, you'll have to give it this label, and it should work from there.

Steve.

---

### Post by gasciut on 2008-09-25
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcfae7682

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14024   112640000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           14025       19457    43640572+   5  Extended
/dev/sda5           14025       19229    41809131   83  Linux
/dev/sda6           19230       19457     1831378+  82  Linux swap / Solaris



thats what i got after doing the mount, and sudo fdisk -l...so is the drive with vista on it the /dev/sda1? and if so how can i get virtual box to read that and try and access it??

---

### Post by kansasnoob on 2008-09-25
I don't know about Virtual Box but I have converted an existing Win OS (it was XP Home) to run in VMware following this guide:

[http://www.howtoforge.com/vmware_converter_windows_linux](http://www.howtoforge.com/vmware_converter_windows_linux)

I then used this guide (towards the end of the page) to get it running on 8.04:

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron-p5](http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron-p5)

It did work, but as I said before - I hated it!

---

### Post by gasciut on 2008-09-25
why did you hate it?

---

### Post by kansasnoob on 2008-09-25
I simply prefer a dual boot! I found the Windows system to be even less responsive than Win usually is.

I use ntfsprogs so I can read and write files in windows, it doesn't allow me to run win programs, but also I use external drives almost exclusively for data storage and they're all formatted either FAT32 or NTFS.

It's really a matter of personal choice. Some people consider dual booting a primitive practice.

---

### Post by Paqman on 2008-09-25
> **gasciut said:**
> i cant see the c: drive when im on ubuntu and cant see the d: drive when im on vista.

You should be able to see your Windows partition from Ubuntu. Check the Places menu, it should be in there. If you partitioned manually though, you might have forgotten to set a mount point for the Windows partition.

Either way, if you're still struggling, try installing this: [ntfs-config](apt:ntfs-config) and see if that helps find and mount your NTFS partition.

To have Windows find Ubuntu you'll need to install [ext2ifs](http://www.fs-driver.org/) in Windows.

---

### Post by kansasnoob on 2008-09-25
> **Paqman said:**
> You should be able to see your Windows partition from Ubuntu. Check the Places menu, it should be in there. If you partitioned manually though, you might have forgotten to set a mount point for the Windows partition.

Either way, if you're still struggling, try installing this: [ntfs-config](apt:ntfs-config) and see if that helps find and mount your NTFS partition.

To have Windows find Ubuntu you'll need to install [ext2ifs](http://www.fs-driver.org/) in Windows.

I think the OP wants be be able to actually run both desktops on the "cube" at the same time, or at least be able to access both systems without restarting.

---

### Post by squaregoldfish on 2008-09-25
> **gasciut said:**
> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcfae7682

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14024   112640000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           14025       19457    43640572+   5  Extended
/dev/sda5           14025       19229    41809131   83  Linux
/dev/sda6           19230       19457     1831378+  82  Linux swap / Solaris



thats what i got after doing the mount, and sudo fdisk -l...so is the drive with vista on it the /dev/sda1? and if so how can i get virtual box to read that and try and access it??

You're right. /dev/sda1 is your Windows partition. As I said in #9, I don't know how to get VirtualBox to see it - if no-one here can help you, a Google search should move you forward.

I think the reason things get unresponsive with VirtualBox and the like is that you need a shed load of RAM to make it work effectively, since you're running both OSes at the same time. I've got 2Gb in my machine, and it's just barely enough to make it work. Any less than that and you'll struggle. Still, it's always worth slapping extra RAM in your machine :)

Steve.

---

### Post by Paqman on 2008-09-25
> **kansasnoob said:**
> I think the OP wants be be able to actually run both desktops on the "cube" at the same time, or at least be able to access both systems without restarting.

From the way he's worded it in his OP, I think he wants both.

---

### Post by gasciut on 2008-09-25
ya. my goal is to be able to run windows through ubuntu on the "cube" or what not, but its looking like thats gonna be easier said then done. the whole thing i guess would be finding the right software that would be able to find the hidden vista drive and then link it to ubuntu, but with so many different options out there on different ways that "might" work, well i really dont even know what to do.  its such a pain having to restart everytime to run a differnt os, but i guess this is just over my head with all the ntfs and what not...

---

### Post by tuxxy on 2008-09-25
To boot a physical partition in Virtual box you would need to create .vmdk file, [heres a guide]("http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/") to get you started

Also be sure you download the PUEL version of[VirtualBox 2.0]("http://www.virtualbox.org/wiki/Downloads")

---

### Post by gasciut on 2008-09-26
so i found vista stuff while searching for a hd on virtual box. what file in vista would i look for to add vista as a hard disk image

---

