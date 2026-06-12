---
title: "[SOLVED] Can't detect my external HDD"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by baldurpet on 2008-10-22
I just got Ubuntu a month ago and it's been working like a dream with the exception that Ubuntu doesn't seem to detect my external USB HDD.

I have another HDD and Ubuntu can open and explore that one just fine but it can't even detect the first one. It's not broken since Windows can detect it just fine. 

Someone told me that it might be that my HDD has an NTFS file system (I don't know the file system quite frankly) but shouldn't Ubuntu be able to at least *detect* it??

I hope that Ubuntu can eventually connect to my HDD as I can't stand Windows. Could formatting the HDD into EXT2 or EXT3 help? If so, wouldn't I have to format it using Windows and what program should I use?

Help would be greatly appreciated. :)

---

### Post by D3M0L1$H3® on 2008-10-22
yes, reformatting it *would* help a little. use ext3. GPartEd (GNOME Partition Editor) is included on the livecd, but you will have to install it to use in without the disc. (apt-get install gparted?)
there may be troubles with the usb port or something if none works.

---

### Post by baldurpet on 2008-10-22
No, there aren't any troubles with the USB port. Before I installed Ubuntu on my computer Windows detected it just fine. And also like I said, Ubuntu does detect my other HDD using the exact same USB port. 

I'm currently copying all my data off of the HDD (I'm using an old computer with Windows and USB 1.0 so moving 180 GB takes almost forever), but after that I'll try the suggestions posted here.

---

### Post by baldurpet on 2008-10-23
I connected my HDD to my computer and it detects it now but says that it's unable to mount it. 

The error message says that "mount is denied because NTFS is marked to be in use.
1. If you have Windows then disconnect the external devices by clicking safely remove hardware. 
2. If you do not have Windows use the force option...etc.etc."

Wtf? Does this mean that Ubuntu can't mount the HDD because I hadn't clicked 'safely remove hardware'??

**Edit:** I tried opening it with Windows and selecting 'safely remove hardware' and now Ubuntu (again) doesn't detect it! What on earth is going on?

---

### Post by bobpur on 2008-10-23
Are you having the drive plugged in as you boot up the computer or do you plug it in after the computer is powered up? I have a Maxtor One-Touch 120gb external drive that gives Ubuntu fits sometimes. 

I wouldn't think that being formatted to NTFS would be a problem. I dualboot with WinXP and it detects my external drive (most times) as well as the Windows partition on the same drive as Ubuntu is on.

This is just theory, but mine came pre-loaded with some windows programs that try to start on boot causing the "can't mount" errors. At least, that's what I think is happening.

Sometimes, right click to "open" and left click on "open" doesn't work but "double clicking" with the left mouse button will work. (laptop mouse) I'm a "lefty" so I have to ponder my mouse to figure out how you "other" people do it. :) I think I got the buttons translated right. (er, yeah)

Good Luck.

---

### Post by robalcorn on 2008-10-23
install ntfs configuration tool from add/remove and you may have to or not  reboot for it to be read and written too,

---

### Post by bsharp on 2008-10-23
Post the output of:

```
sudo fdisk -l
```

---

### Post by baldurpet on 2008-10-24
```

baldur@baldur-laptop:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcba1b13a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris

```
This is what I get, it's just my laptop's hdd. 

The hdd I'm trying to have Ubuntu detect/mount is around 233-300 GBs. It seems, sadly, that Ubuntu simply cannot find it while Windows has **no problem** detecting it, mounting it, and reading stuff off of it- which is sad because I like(ed) to think and tell people that Ubuntu was superior to Windows in almost every way.

Do you suppose formatting it on Windows, and then trying to read it again with Ubuntu is going to do any good? And if so, why should I use EXT3? Is it better than EXT2?

---

### Post by boof1988 on 2008-10-27
Hi baldurpet,

Were you able to get your external drive working?

I want to use my external HDD (haven't hooked it up yet) and am looking for any help in case I have any problems.

Hope your drives working.

---

### Post by Keen101 on 2008-10-27
even if it had NTFS before... ubuntu still should have detected it. 

You external HDD isn't one of those wierd ones with a "one click backup" button does it? It it does, there is probably some wierd firmware on the external electronics... If that is the case... i'd get a new enclosure for it.

I'm running ubuntu off my external HDD right now. Of course I built it myself, so i knew i wouldn't have any problems with those "one button backup" external HDD's. I just bought a laptop HDD and bought a usb enclosure for it on newegg.

---

### Post by baldurpet on 2008-10-28
No, it's not one of those one click backup HDDs. It's just a run of the mill external HDD. My friend says that it's possible that NTFS hasn't got anything to do with it, and my mom's boyfriend says that it isn't smart formatting HDDs to one of the EXT formats, since Windows can't detect it (he says that computer drives running Linux should have EXT2 or 3 and HDDs should have NTFS). 

I think it might be better to simply buy a new case

---

### Post by sacauntos on 2008-10-28
Hi baldurpet,

I was having a similar issue. I've been using a 160 GB USB external HDD (previously formatted in windows in the ntfs filesystem) for a while without any problems in ubuntu. Suddenly it started to behave weird and it ended up not being detected. Following some forums' threads I tried to manually mount it without success. 

Once, plugging the HDD while ubuntu was already running, an error message popped up telling me to do chkdsk /f in windows and reboot twice, emphasizing the use the parameter /f and the number of times I had to reboot. I did it and now the HDD is working again.

It is what kept it working for me, but I'm by no means an expert. Maybe someone could give a more formal explanation...

Cheers

---

### Post by baldurpet on 2008-10-29
Huh.. that's odd. I'll try that when I get my hands on another Windows machine (it still sucks that I have to have Windows machines in order to run Ubuntu, maybe Ubuntu isn't ready for showtime).

Another thing.. I installed Debian on my (ex)windows machine and, surprise! It detects the hdd in 2 seconds and is able to read from it too! Perfectly!

This problem must be in Ubuntu, now mustn't it?

---

### Post by baldurpet on 2008-11-10
It's working now. :)
I had to go to the BIOS at startup and set the ***Large Disk Access Mode***, which was formerly set to DOS, to other.

I don't know how I was supposed to figure this out on my own, and I only found it with luck. How could the common user figure this out on his own.. well I guess this one is solved then. 

(p.s. how do you mark your thread as solved?) 
(p.s.2. oh.. under "thread tools", nvm)

---

