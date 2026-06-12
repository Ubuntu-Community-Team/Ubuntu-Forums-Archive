---
title: "How do you delete the Windows partition?"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by dj_akasha on 2008-06-11
Hi, I've decided to say bye bye to my Windows partition on my laptop and resize the Ubuntu partition.  I'm struggling to find anything that works from.

I've tried using qtparted and it won't let me do anything.  I then tried gparted and used a live CD, but I've got an ATI graphics card which has problems with drivers and the screen goes black when the GUI is meant to appear.

I don't really want to reformat as it took me ages to get the wireless working, but on the other hand it wouldn't hurt to do it all again as I'd learn more.  I can't find anything that would allow me to create a ghost image either.  

Any help would be greatly appreciated.

---

### Post by Duck2006 on 2008-06-11
You can use partimage to make an image of your OS.

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by sam_delta on 2008-06-11
is your windows partition mounted? you wont be able to do anything to it if it is mounted

sam

---

### Post by Lord Xeb on 2008-06-11
Yes, this is true. On your desktop, if there is a drive that says it is mounted, go and right click, then select "Unmount Volume", then go and try and reformat the partition.

---

### Post by dj_akasha on 2008-06-11
Nope not mounted.  Don't think I can use partimage as it makes an image of the partition as well so it would get me back to where I started.

---

### Post by Duck2006 on 2008-06-11
No it will make an image of the partition that you tell it to make.
Or there are the dd commands, and they will only coppy what you tell it to copy.

[http://www.brunolinux.com/02-The_Terminal/The_dd_command.html](http://www.brunolinux.com/02-The_Terminal/The_dd_command.html)

---

### Post by tinny on 2008-06-11
Ive used BootIT to do exactly what you are talking about. (delete a windows partition and resize linux partitions)

[http://www.terabyteunlimited.com/bootit-next-generation.htm]("http://www.terabyteunlimited.com/bootit-next-generation.htm")

I think you can use this utility without buying it. (at least you used to be able too).

---

### Post by logos34 on 2008-06-11
> **dj_akasha said:**
> I then tried gparted and used a live CD, but I've got an ATI graphics card which has problems with drivers and the screen goes black when the GUI is meant to appear.

try gparted on the Parted Magic rescue cd.  Select the 'XVesa' driver--should work for just about anything.  (if the screen goes black hit ctl+alt+delete).
Root cannot be mounted while resizing, so you'll have to work from cd.

---

### Post by kansasnoob on 2008-06-11
Maybe I'm wrong but since you have Ubuntu configured to use your ATI graphics card, and your Win partition unmounted, you should be able to use gparted from your Ubuntu installation (in 8.04 it's in synaptic) and delete any unmounted partition.

If so, you could then format that partition as an ext 3 data partition for storage. Not quite what you're looking to do but easy. It's too bad we can't get gparted to expand a mounted partition ....... sigh!

---

### Post by logos34 on 2008-06-11
> **kansasnoob said:**
> It's too bad we can't get gparted to expand a mounted partition ....... sigh!

exactly, which is why he'll have to work from live cd, otherwise he could simply unmount windows and delete it as you say.

Maybe someday gparted will introduce online partition resizing. Vista has it (we'll sort of--it finishes it when you restart), so how hard can it be?

---

### Post by regomodo on 2008-06-11
`

---

### Post by stchman on 2008-06-11
> **dj_akasha said:**
> Hi, I've decided to say bye bye to my Windows partition on my laptop and resize the Ubuntu partition.  I'm struggling to find anything that works from.

I've tried using qtparted and it won't let me do anything.  I then tried gparted and used a live CD, but I've got an ATI graphics card which has problems with drivers and the screen goes black when the GUI is meant to appear.

I don't really want to reformat as it took me ages to get the wireless working, but on the other hand it wouldn't hurt to do it all again as I'd learn more.  I can't find anything that would allow me to create a ghost image either.  

Any help would be greatly appreciated.

Install gparted in Ubuntu.

```
sudo apt-get install gparted
```

Fire it up and select unmount if mounted.  Next Right click on all unwanted Windows Partitions and select delete.  Next hit apply.

You will have free space you can right click on the free space and select format to EXT3.  After that is done you will need to mount the partition.

---

### Post by logos34 on 2008-06-11
> **stchman said:**
> You will have free space you can right click on the free space and select format to EXT3.  After that is done you will need to mount the partition.

Yeah, but dj_akasha says he wants to **resize/expand** Ubuntu.  So he'll have to use the livecd (root cannot be mounted when expanding).

On the other hand, reformatting the windows partition as ext3 may not be a bad idea after all--he could make it a separate /home.

dj_akasha,

what about it, a [separate /home]("http://www.psychocats.net/ubuntu/separatehome")?

post your 

**sudo fdisk -l**

Also, as Duck said above, you'll need to take out the windows line from fstab and possibly update root entries there and in menu.lst, and possibly reinstall grub to mbr--if it changes, that is, which it may not.  (Root may remain sda2 or whatever even after deleting windows)

---

### Post by Duck2006 on 2008-06-11
"regomodo" posted that as a add on to my post.

---

### Post by logos34 on 2008-06-11
> **Duck2006 said:**
> "regomodo" posted that as a add on to my post.

oops, yes, I see now

---

### Post by dj_akasha on 2008-06-12
> **logos34 said:**
> try gparted on the Parted Magic rescue cd.  Select the 'XVesa' driver--should work for just about anything.  (if the screen goes black hit ctl+alt+delete).
Root cannot be mounted while resizing, so you'll have to work from cd.

Thanks that worked.  Only problem is that I wasn't able to resize the partition with Ubuntu.  Have reformatted the one with windows to ext3.  Need to decide if I can live with that or if I want just the one drive then will probably be looking at re-installing.

---

### Post by dj_akasha on 2008-06-12
> **logos34 said:**
> Yeah, but dj_akasha says he wants to **resize/expand** Ubuntu.  So he'll have to use the livecd (root cannot be mounted when expanding).

On the other hand, reformatting the windows partition as ext3 may not be a bad idea after all--he could make it a separate /home.

dj_akasha,

what about it, a [separate /home]("http://www.psychocats.net/ubuntu/separatehome")?

post your 

**sudo fdisk -l**

Also, as Duck said above, you'll need to take out the windows line from fstab and possibly update root entries there and in menu.lst, and possibly reinstall grub to mbr--if it changes, that is, which it may not.  (Root may remain sda2 or whatever even after deleting windows)

fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

Having trouble accessing psychocats website so not sure about the separate home thing.  Will try check it out from work tomorrow.  What does the fdisk show?  Sorry am a bit of a newbie.

By the way have no idea what you mean about the fstab and root stuff a menu.1st etc.

---

### Post by Duck2006 on 2008-06-12
sudo fdisk -l

Will show your partitions and what file type there are.

ie my sudo dfisk -l

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xfccafcca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10337    78147688+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x381e7b4d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sdb2            6375        9612    26009235   83  Linux
/dev/sdb3            9613        9729      939802+  82  Linux swap / Solaris

---

### Post by powerpleb on 2008-06-12
For this sort of thing I usually use [SystemRescueCd]("http://www.sysresccd.org/Main_Page") live CD as it has gParted and it will just load generic video drivers.
You can delete, make and resize partitions all you want with it.

---

### Post by rzrgenesys187 on 2008-06-12
> **dj_akasha said:**
> fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

Having trouble accessing psychocats website so not sure about the separate home thing.  Will try check it out from work tomorrow.  What does the fdisk show?  Sorry am a bit of a newbie.

By the way have no idea what you mean about the fstab and root stuff a menu.1st etc.

fstab (/etc/fstab) is a file containing mounting information about various partitions and drives in your computer.

menu.lst (/boot/grub/menu.lst) contains booting information (the menu that comes up when you select which os you want to boot into)

---

### Post by logos34 on 2008-06-12
> **dj_akasha said:**
> Thanks that worked.  Only problem is that I wasn't able to resize the partition with Ubuntu.  Have reformatted the one with windows to ext3.  Need to decide if I can live with that or if I want just the one drive then will probably be looking at re-installing.

So it wouldn't let you expand root to the left into the unallocated space formally occupied by windows? The version of Gparted on Parted Magic has that feature, I'm positive (i.e. resizing a partition's left border).  

Will it allow you to *shrink *root (move left border rightwards)? If you decide on a separate /home, that's what you'll probably want to do.

Reinstalling would certainly simplify things, but you have to back up personal files and settings.  And reinstall all your apps afterward.

---

### Post by dj_akasha on 2008-06-14
Thanks to everyone.  Ended up doing a complete re-install as I just couldn't get rid of the partitioning and it was annoying me.  It seems that the re-install has fixed another problem I was having which is great.  But may I say that getting the drivers for the wireless and the ati card was incredibly frustrating and a right pain in the bum. But I have learned a lot and have made notes (this time) so that I may help others in the same position.

---

