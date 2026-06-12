---
title: "gparted info? unused file system or disk space?"
date: 2012-09-12
forum: New to Ubuntu
---

### Post by Sonoran Desert Rat on 2012-09-12
Here is my info from gparted:

/dev/sda1
ntfs
27.95 GiB
6.86 GiB used
21.09 GiB unused
Flags: boot

Help me understand? Is it showing me free disk space or the unused part of the ntsf file system?

---

### Post by Ubunterrific on 2012-09-12
> **Sonoran Desert Rat said:**
> Here is my info from gparted:

/dev/sda1
ntfs
27.95 GiB
6.86 GiB used
21.09 GiB unused
Flags: boot

Help me understand? Is it showing me free disk space or the unused part of the ntsf file system?

27.95 = 6.86 + 21.09

Therefore, the 21.09 ununsed is the unused part of the ntfs FS.

---

### Post by Sonoran Desert Rat on 2012-09-12
> **Ubunterrific said:**
> 27.95 = 6.86 + 21.09

Therefore, the 21.09 ununsed is the unused part of the ntfs FS.

**Is it showing me all the disk space I have?** Here's what I got from windows:

Total Physical Memory 512.00 MB
Available Physical Memory 124.52 MB
Total Virtual Memory 2.00 GB
Available Virtual Memory 1.96 GB
Page File Space 1.13 GB
Page File DELETED

**I don't think I can dual boot XP and Lubuntu. Can I?**

---

### Post by Ubunterrific on 2012-09-12
> **Sonoran Desert Rat said:**
> Is it showing me all the disk space I have?

Run
```
 sudo fdisk -lu 
```
in a terminal, to clarify things please. Surely you don't have ~30GB HDD?
That ~28GB partition is NTFS, so it's Windows, and 7GB of that is used up, the other 21GB is allocated for windows at the moment.

---

### Post by Ubunterrific on 2012-09-12
> **Sonoran Desert Rat said:**
> **Is it showing me all the disk space I have?** Here's what I got from windows:

Total Physical Memory 512.00 MB
Available Physical Memory 124.52 MB
Total Virtual Memory 2.00 GB
Available Virtual Memory 1.96 GB
Page File Space 1.13 GB
Page File DELETED

**I don't think I can dual boot XP and Lubuntu. Can I?**

On the contrary, even that much RAM should be enough for duelbooting lubuntu and windows xp. You can encroach on that 21GB which is currently NTFS; it *shouldn't *destroy any data to use some of it (e.g. 10GB) and allocate that for lubuntu when installing (as ext4 for example). Just make sure not to touch the 7GB which windows is currently using for your data.
These should be different colours to help you see.

---

### Post by Sonoran Desert Rat on 2012-09-12
> **Ubunterrific said:**
> Run
```
 sudo fdisk -lu 
```
in a terminal, to clarify things please. Surely you don't have ~30GB HDD?
That ~28GB partition is NTFS, so it's Windows, and 7GB of that is used up, the other 21GB is allocated for windows at the moment.

lubuntu@lubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4a104a10

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    58605119    29302528+   7  HPFS/NTFS/exFAT
lubuntu@lubuntu:~$

---

### Post by Sonoran Desert Rat on 2012-09-12
> **Ubunterrific said:**
> On the contrary, even that much RAM should be enough for duelbooting lubuntu and windows xp. You can encroach on that 21GB which is currently NTFS; it *shouldn't *destroy any data to use some of it (e.g. 10GB) and allocate that for lubuntu when installing (as ext4 for example). Just make sure not to touch the 7GB which windows is currently using for your data.
These should be different colours to help you see.

Note: I only want to be able to move windows XP files to Lubuntu. I really don't want windows at all. If there's a better, faster or easier way to do this I am definitely open to suggestions!

---

### Post by Ubunterrific on 2012-09-12
> **Sonoran Desert Rat said:**
> Note: I only want to be able to move windows XP files to Lubuntu. I really don't want windows at all. If there's a better, faster or easier way to do this I am definitely open to suggestions!

Now that i've seen that output, it all makes sense lol (You do indeed have a 30GB HDD)
You don't want windows at all? Well then, first job is to grab everything you want from windows and put it on a separate usb flash drive (pen/stick/whatever you like to call it lol) or a disk or some sort of storage device.

Next, grab a lubuntu .iso (i'd go for 32bit if i were you) and use a program to write the iso to another USB pen or disk.  Unetbootin is a great program for this, but there are others. The program will wipe everything on the usb pen and make it a bootable device with an operating system on it.
Then, you switch the pc off and stick the usb pen into the USB port. 
Power on the machine and press whatever key loads you to the BIOS (F2 or F12 or something, i think it varies) - select to boot from USB rather than from your harddrive (HDD). Now this is the installation of linux - rather than select how much of the HDD you want for windows and how much for linux, just go ahead and select to use the entire HDD for lubuntu.
Then it will install the kernel and packages and walk you through until there's only lubuntu on your pc.

I'd recommend you at least try running lubuntu on it live (as practice) to see if the wireless drivers etc work out of the box, otherwise you might have to get ndiswrapper + downloaded drivers brought to it to help. An internet connection of any description makes life easier because it can update while it's installing and kill 2 birds with 1 stone :D

---

### Post by oldos2er on 2012-09-12
> **Sonoran Desert Rat said:**
> Is it showing me all the disk space I have?

Total Physical Memory 512.00 MB
Available Physical Memory 124.52 MB
Total Virtual Memory 2.00 GB
Available Virtual Memory 1.96 GB
Page File Space 1.13 GB
Page File DELETED


RAM (or physical memory) and hard disk space are two very different things:

[http://en.wikipedia.org/wiki/Random-access_memory](http://en.wikipedia.org/wiki/Random-access_memory)

[http://en.wikipedia.org/wiki/Hard_disk](http://en.wikipedia.org/wiki/Hard_disk)

---

### Post by Sonoran Desert Rat on 2012-09-12
> **Ubunterrific said:**
> Now that i've seen that output, it all makes sense lol (You do indeed have a 30GB HDD)
You don't want windows at all? Well then, first job is to grab everything you want from windows and put it on a separate usb flash drive (pen/stick/whatever you like to call it lol) or a disk or some sort of storage device.

Next, grab a lubuntu .iso (i'd go for 32bit if i were you) and use a program to write the iso to another USB pen or disk.  Unetbootin is a great program for this, but there are others. The program will wipe everything on the usb pen and make it a bootable device with an operating system on it.
Then, you switch the pc off and stick the usb pen into the USB port. 
Power on the machine and press whatever key loads you to the BIOS (F2 or F12 or something, i think it varies) - select to boot from USB rather than from your harddrive (HDD). Now this is the installation of linux - rather than select how much of the HDD you want for windows and how much for linux, just go ahead and select to use the entire HDD for lubuntu.
Then it will install the kernel and packages and walk you through until there's only lubuntu on your pc.

I'd recommend you at least try running lubuntu on it live (as practice) to see if the wireless drivers etc work out of the box, otherwise you might have to get ndiswrapper + downloaded drivers brought to it to help. An internet connection of any description makes life easier because it can update while it's installing and kill 2 birds with 1 stone :D

I have already made a Live CD (32 bit Lubuntu) and am running on it now. :D I assume, from what you said above, that means I already know it will run my PC, CD, and internet connection?

I will back up my files to a USB then! :D

---

### Post by Sonoran Desert Rat on 2012-09-12
> **oldos2er said:**
> RAM (or physical memory) and hard disk space are two very different things:

[http://en.wikipedia.org/wiki/Random-access_memory](http://en.wikipedia.org/wiki/Random-access_memory)

[http://en.wikipedia.org/wiki/Hard_disk](http://en.wikipedia.org/wiki/Hard_disk)

That's extremely helpful! Thanks!!:D

---

### Post by Ubunterrific on 2012-09-12
Excellent, sounds like it's all go then :popcorn:

---

### Post by Sonoran Desert Rat on 2012-09-12
> **Ubunterrific said:**
> Excellent, sounds like it's all go then :popcorn:

I'll post when I'm done. :D

Thank you!

:KS Ubunterrific :KS

---

### Post by Ubunterrific on 2012-09-12
> **Sonoran Desert Rat said:**
> I'll post when I'm done. :D

Thank you!

:KS Ubunterrific :KS

Here's hoping for a successful outcome :p

---

### Post by Sonoran Desert Rat on 2012-09-12
> **Ubunterrific said:**
> Here's hoping for a successful outcome :p

Semi-successful, lol. I am getting errors (will post those later, don't have too much time at the moment) when I boot into it. Also before it boots Lubuntu, I get the Intel boot agent telling me something's not found (will post that later too). 


lubuntu@lubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ad113

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    57591807    28794880   83  Linux
/dev/sda2        57593854    58603519      504833    5  Extended
/dev/sda5        57593856    58603519      504832   82  Linux swap / Solaris
lubuntu@lubuntu:~$ 

GParted doesn't recognize /dev/sda5?

I will get the other info and post that too a bit later.

EDIT: I ah...logged in as a guest...:-\"  I logged in a second time to write down the errors and everything is running great so far! Yay! Thanks so much for the help. My next step is to get the NTSF or FAT32 (not sure what they are) off my USB. :D

---

### Post by Ubunterrific on 2012-09-12
> **Sonoran Desert Rat said:**
> Semi-successful, lol. I am getting errors (will post those later, don't have too much time at the moment) when I boot into it. Also before it boots Lubuntu, I get the Intel boot agent telling me something's not found (will post that later too). 


lubuntu@lubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ad113

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    57591807    28794880   83  Linux
/dev/sda2        57593854    58603519      504833    5  Extended
/dev/sda5        57593856    58603519      504832   82  Linux swap / Solaris
lubuntu@lubuntu:~$ 

GParted doesn't recognize /dev/sda5?

I will get the other info and post that too a bit later.

EDIT: I ah...logged in as a guest...:-\"  I logged in a second time to write down the errors and everything is running great so far! Yay! Thanks so much for the help. My next step is to get the NTSF or FAT32 (not sure what they are) off my USB. :D

sda5 is allocated as swap space - if i remember correctly, it's basically part of your hard drive allocated to be used if you run out of available memory (data gets 'swapped' between RAM and the HDD. Perfectly typical.

Word of advice about filesystem for USB - i'd suggest ext2 if you're opting for a change on them, but bear in mind that if you want your usb pen to work on a windows pc, they will have to have installed this: [http://www.fs-driver.org/](http://www.fs-driver.org/)  which allows windows to use the ext2 format.
Reason for ext2 over something else is that it doesn't 'journal' like ext 3(?) and ext4. Ext4 is great for your main HDD (which is why it's the default filesystem) but for a flash drive, it just means unnecessary extra writes everytime data gets copied to and from it, thus shortening the usb pen's lifespan if you will. To combat this further, you can go into mounting usb pens with 'noatime' etc Look into it if you're interested.

Fat32 is the typical filesystem for USB pens (it works out of the box on all operating systems), it's just not as good at ext2 but there are far better explanations for WHY online. NTFS is the windows filesystem, though if i remember correctly, microsoft made a new one for windows 7 or *ARE MAKING ONE *for windows 8, i can't recall :P

Everything looks good :D

---

### Post by egeezer on 2012-09-12
Quick note: in the Ubuntu-based distros, if you type in the terminal:     -------sudo parted /dev/sda print-------     You will get the partition sizes in MB/GB form instead of cylinders and sectors and all.  Makes it a little more clear - to a dummy like me, anyway!

---

### Post by Sonoran Desert Rat on 2012-09-12
> **Ubunterrific said:**
> sda5 is allocated as swap space - if i remember correctly, it's basically part of your hard drive allocated to be used if you run out of available memory (data gets 'swapped' between RAM and the HDD. Perfectly typical.

Word of advice about filesystem for USB - i'd suggest ext2 if you're opting for a change on them, but bear in mind that if you want your usb pen to work on a windows pc, they will have to have installed this: [http://www.fs-driver.org/](http://www.fs-driver.org/)  which allows windows to use the ext2 format.
Reason for ext2 over something else is that it doesn't 'journal' like ext 3(?) and ext4. Ext4 is great for your main HDD (which is why it's the default filesystem) but for a flash drive, it just means unnecessary extra writes everytime data gets copied to and from it, thus shortening the usb pen's lifespan if you will. To combat this further, you can go into mounting usb pens with 'noatime' etc Look into it if you're interested.

Fat32 is the typical filesystem for USB pens (it works out of the box on all operating systems), it's just not as good at ext2 but there are far better explanations for WHY online. NTFS is the windows filesystem, though if i remember correctly, microsoft made a new one for windows 7 or *ARE MAKING ONE *for windows 8, i can't recall :P

Everything looks good :D

I backed up my data and completely overwrote windows. GParted seems to be gone and I have something called Disk Utility? I installed Lubuntu 32 bit, does it come with firefox and gparted, etc., or do I need to install them? My bookmarks are gone (oops) and I can make bookmarks but haven't figured out how to get to them when I want one yet. :/ I'm surfing so far to no avail. :D

EDIT: Almost forgot, When I boot from hard drive I get:

Client Mac Address: (big number here)
DHCP_ _ _ _<cursor>

PXE-E53 No Boot filename recieved

PXE-M0F Exiting Intel Boot Agent

then Lubuntu loads and everything's fine.

Is this normal?

---

### Post by Sonoran Desert Rat on 2012-09-12
> **egeezer said:**
> Quick note: in the Ubuntu-based distros, if you type in the terminal:     -------sudo parted /dev/sda print-------     You will get the partition sizes in MB/GB form instead of cylinders and sectors and all.  Makes it a little more clear - to a dummy like me, anyway!

Nice! Thank you! :D



DELETED-Portable-PC:~$ sudo parted /dev/sda print
Model: ATA HITACHI_DK23CA-3 (scsi)
Disk /dev/sda: 30.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  29.5GB  29.5GB  primary   ext4         boot
 2      29.5GB  30.0GB  517MB   extended
 5      29.5GB  30.0GB  517MB   logical

no swap?

---

### Post by Ubunterrific on 2012-09-13
'swap space' (sda5) is in 'extended' which you had as sda2 lol don't worry about it.

Those error messages (PXE related) at bootup LOOK to me like the stuff you get when you have 'boot from network' enabled in the bios but not set up. I imagined it was a feature to boot from another computer over a LAN or the internet etc
If you go into your BIOS and have a look at boot options, feel free to set the HDD to be the first thing to boot from again, and have a look for 'boot from network' or otherwise and take it off as an option. 
With any luck, that should remove those messages. (There'll be other methods, but this is method i know works and i myself NEVER used nor intend to use 'Boot from network' :p No need when there's a pretty operating system sitting on your harddrive that's working lol

---

### Post by Sonoran Desert Rat on 2012-09-13
Oh! I forgot about the boot menu, lol. I think I'll read up better on Linux partitions and how they work too. I'm currently working my way through the terminal tutorial, I only have Chromium on here and I want firefox. :) 

Thank you so much! :D

---

