---
title: "How 2 Reformat a USB Flash &quot;U2&quot; Drive??"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by GregA on 2008-04-22
Hello All,

I have a Sandisk cruzer USB 4gb flash stick - - that is very annoying to use on Windows machines.  The problem is that 2 drive letters are assigned by Windows when using a U2 type drive, versus the standard 1 (causing all kinds of directory mgmt issues).  

Anyway, I want to see if I can use Ubuntu, to reformat the drive totally wiping out the current data, and assign the standard FAT32 file type to it.
(I can't use my XP machine because I don't have admin rights (at work)).

IF I were using it only on Linux, I would choose either Rieser or Ext3, but I need to use it in both OS's.

So, what would be the command in Linux (or gui if available) to reformat the whole 4gb flash drive and install FAT32??

Thanks much.

---

### Post by abhiroopb on 2008-04-22
Easiest thing to do:

On Gutsy:

System>Administration>Partition Editor

On the top right there should be an option to change disk (usually the current one is selected, i.e. you're ubuntu partition), change it to the usb stick (you can tell its the USB stick because of the size.

Then click on the partition(s) of the usb drive and click on delete.

Then right click and select Format, and select FAT32

Then when you are happy with everything click Apply.

Thats it!

---

### Post by GregA on 2008-04-22
Thanks, using Partition Editor sounds exactly like what I'm needing, but unfortunately, I don't have that option via "System>Administration" or via "System>Preferences".

Is Partition Manager an application I can get in Synaptic?  Or I could probably use a Live CD (don't have the Ubuntu Live with me) - but do have Mepis 7 which as gParted . . . ?

---

### Post by abhiroopb on 2008-04-22
Sorry I assumed you had Ubuntu Gutsy. Partition manager is basically gparted.

If you open a terminal and type in gparted it will run it.

Good luck!

---

### Post by tyroeternal on 2008-04-22
Partition Editor IS gparted.  So just install gparted and you will be good to go :)

---

### Post by GregA on 2008-04-22
Thanks Guys! . . . your advice worked perfect.  I searched for gparted in Synaptic, installed it, and it took less than a minute to reformat the flash drive and create a new fat32 partition. . (ain't Linux great, or what. . ).

Greg

---

### Post by lswest on 2008-04-22
you can run ```
sudo apt-get install gparted
``` and then that option will be there.  Woops, too slow - damn you multi-tasking!!! *shakes fist at the sky* :P

---

### Post by GregA on 2008-04-22
Well, let me report back that the overall mission (to remove the dreaded U2 data (programs) from the drive was not successful, even after using gParted to reformat the drive.

It seems that these flash drives that have the U2 applications installed, somehow bypass the main partition of the drive, and either use a small hidden partition, or maybe the file has something like a MBR where these apps are stored.

So, when I use the drive in XP, it still is assigned to F and G, with F being the U2 system apps & launcher.  Even deleting the folders and "LaunchU3.exe" didn't remove these either.

But I know these drives can be "cleansed" of this commercial techno-crud, but I don't how how yet.   I wonder if there is some type of "low level" reformat command in Linux that will "see" and "wipe" ALL data from the Flash stick?

Any other tips appreciated.  Thanks.

---

### Post by abhiroopb on 2008-04-22
I'm quite surprised because I had a 4gb corsair, and it erased everything. Make sure you delete ALL partitions in gparted before creating a new fat32. As in there should only be one line of partitions.

---

### Post by GregA on 2008-04-22
There's about 9.3 megs of data on the drive "somewhere".  gParted is only showing 1 partition of something like 3.89 gigs . . . let me try it again, or maybe I'll also try Qparted on the Mepis Live CD and see if it sees the hidden partition. . .

---

### Post by billgoldberg on 2008-04-22
> **GregA said:**
> There's about 9.3 megs of data on the drive "somewhere".  gParted is only showing 1 partition of something like 3.89 gigs . . . let me try it again, or maybe I'll also try Qparted on the Mepis Live CD and see if it sees the hidden partition. . .

That sounds right. Gparted will list all partitions, including partitions hidden in windows.

The reason it says 3.89 is because of the 1gb= 1024 or 1000mb. So while the disk says 4gb, it's actually only 3.89gb. 

The same with my external hdd, it says 500gb but is actually only 465,67gb and my internal hard drive.

---

### Post by abhiroopb on 2008-04-22
Thats right a 4gb disk would only show about that much. Try formatting to something different (e.g. ext2) and install the ext2 drivers for windows. See if that works.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Tom Mann on 2008-04-22
Sadly these "U2"/"U3" drives are a pain. I remember that the U2/U3 software is on a 'virtual cd' section of the key - you will always have a read-only drive with the software with one of these USB keys. Sorry. :(

Link: [http://en.wikipedia.org/wiki/U3]("http://en.wikipedia.org/wiki/U3")

---

### Post by mike555 on 2008-04-22
If you need to, you could get the U3 uninstaller from the Sandisk site and run it on a Windows machine , that will get rid of it .......

---

### Post by ace007 on 2008-04-22
For future reference, or to all those who are wondering, the U2 and U3 versions of the Cruzer USB drive have an option to uninstall itself from the cruzer.

When that annoying U3 menu pops up in the taskbar in Windows, if you access it and go to settings/configuration there is an option to uninstall, much easier than using gparted.

---

### Post by GregA on 2008-04-22
Ace007,

Yes, you're right - - I finally got rid of the U2 files by calling Sandisk tech support (they have great service imho).  Anyway, they advised how to find and run the uninstall routine (and it has to be done via Windows).

So, formatting these disks won't rid users of U2, because the files are placed such that the Windows sees the flash stick as two devices, and the U2 files show up as a DVD/CDRom . . . . read only.

If you only use these sticks in Linux, no problems - - but in Windows they can be more of a pain than a plus . . .

---

