---
title: "GParted"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by Elfo33 on 2008-11-13
So, I'm rather new to Ubuntu (one week).  I decided to add a second hard drive to my system, and so I installed GParted from the repositories.  I then managed to set up a primary partition for the entire disk size with GParted, and format into ext3.

Now, when I look at my disk in nautilus, it shows my free space as being 130 GB smaller than the size of the disk!  I'm wondering, where did my extra gigs go and how can I get them back?

PS: this is a slightly used disk, if that makes a difference.  I didn't see anything in lost+found when I finally figured out how to get in there.

---

### Post by mapes12 on 2008-11-13
What is the disk size?

Can you post the output to:

```
sudo fdisk -l
```

What do you need this extra partition to do for you?

---

### Post by Bartender on 2008-11-13
Elfo, you went at the partitioning from the wrong direction.  Download and convert to a bootable disc a GParted LiveCD (GPLCD)

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

This can be done on a Windows PC as long as you know how to convert the .iso to a bootable CD rather than just copying the data.  
Follow the typical rules for converting an .iso.  Use good quality media, don't burn it at maximum speed (4X to 8X for a modern PC is good).

When you're done you'll have a bootable CD that's a stand-alone partitioner.  A wonderful tool!

I don't understand what you mean by "free space as being 130 GB smaller than the size of the disk".  Do you mean you deleted everything?  If not, maybe you should.  Just start over.  Delete all partitions with the GPLCD, format to one big ext3 partition if you just want to let Ubuntu auto-install, then toss in the Ubuntu installer disc and start over again.  I think practicing installing Ubuntu several times is a wonderful confidence-builder!

And don't worry about swap formatting.  If you let Ubuntu auto-install (or even manual install) to a disc that's formatted as ext3 it reformats the swap area to "linuxswap" regardless.  I've manual installed Ubuntu to a disc that I'd set up beforehand, with the swap partition pre-formatted to "linuxswap" file system, and it reformatted that partition anyways!

EDIT:  Wait a minute, I just re-read your post.  You probably don't want to install Ubuntu to this second HDD, do you?  Your intent was just to have extra storage, or maybe install a second Linux distro sometime in the future?  If that's the case, then the advice to make a GPLCD is still good, and you can ignore the second part about installing Ubuntu.  Completely wipe the drive of all partitions so that GPLCD sees one big unallocated partition.  Hopefully you'll see a number close to the stated size.  It's never quite as much but you probly already know that.
Then format to ext3 if it's going to be storage for Ubuntu.

---

### Post by Paqman on 2008-11-13
Bartender: He already had Ubuntu installed. He's just adding a second disk. Also, Gparted is on the LiveCD, so almost everybody will already have a bootable Gparted disk.

---

### Post by Bölvaður on 2008-11-13
> **Elfo33 said:**
> Now, when I look at my disk in nautilus, it shows my free space as being 130 GB smaller than the size of the disk!

This is to be expected when you have 10 tarabyte hard disk.

Harddisk manufacturers often use GB but operating systems usually state the size of the harddisk in GiBi (slightly smaller numbers). Also ext3 takes some space on the harddisk to use for journaling (depends on size of your HD but for me it is 3%.. wait.. no I dont know the number).

So you should expect seeing different numbers from what the label on your HD, what it is in GiBi and what you can actually use of it for your data. (but 130gb is way too much for that explanation)

---

### Post by Elfo33 on 2008-11-13
Ok, I'm away from the computer but I'll run fdisk tonight.

I already have Ubuntu installed my primary harddrive.  I'm attempting to add a second internal hard drive, to the size of 1 TB.  When mounted in Ubuntu, it shows 1000.2 GB.  GParted shows ~931 GB, I'm assuming because of the mathematical difference between base 10 and base 2 systems; and I'm assuming GParted uses base 2 like Microsoft.

Now, when I go into Nautilus, where it show 1000.2 GB on the left, at the bottom of the screen it says "Free Space 870.x GB".

So, I'm wondering where my extra 130 GB went?  Even if it's a base 2 vs base 10 thing I shold only lose about 70 GB.

As far as a live boot partitioner, how would that differ from the partitioner in an Ubuntu install, or the GParted in the repositories?

---

### Post by Elfo33 on 2008-11-15
> **mapes12 said:**
> What is the disk size?

Can you post the output to:

```
sudo fdisk -l
```?

Here ya go:

```
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x81ad0726

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux
```

---

### Post by bumanie on 2008-11-15
> **Elfo33 said:**
> Ok, I'm away from the computer but I'll run fdisk tonight.

I already have Ubuntu installed my primary harddrive.  I'm attempting to add a second internal hard drive, to the size of 1 TB.  When mounted in Ubuntu, it shows 1000.2 GB.  GParted shows ~931 GB, I'm assuming because of the mathematical difference between base 10 and base 2 systems; and I'm assuming GParted uses base 2 like Microsoft.

Now, when I go into Nautilus, where it show 1000.2 GB on the left, at the bottom of the screen it says "Free Space 870.x GB".

So, I'm wondering where my extra 130 GB went?  Even if it's a base 2 vs base 10 thing I shold only lose about 70 GB.

As far as a live boot partitioner, how would that differ from the partitioner in an Ubuntu install, or the GParted in the repositories?

That's probably true, but there is also 5% of the drive put aside for addressing, once the drive has a filesystem on it.

---

### Post by mapes12 on 2008-11-15
Your HDD's should commence alphabetically with your first device "a", as in "sda". Then your second device should be "b", as in "sdb" and so on. Your fdisk output is reporting one device as sdb. It should look like something like this. See how the two drives are reported as sda and sdb:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7f247f24

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1        1657    13309821   83  Linux
/dev/sda3            1658        9325    61593210   83  Linux
/dev/sda4            9326        9729     3245130   82  Linux swap / Solaris

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1bfd1bfc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            5007       10011    40202662+  83  Linux
/dev/sdb2               1        5006    40210663+   7  HPFS/NTFS
```N.B. sda1 was a NTFS partiton - now deleted.

Elfo 33 - Did you cut and paste ALL the output?

---

### Post by Bartender on 2008-11-15
> **Elfo33 said:**
> As far as a live boot partitioner, how would that differ from the partitioner in an Ubuntu install, or the GParted in the repositories?

Partitioning from a bootable GParted LiveCD is NOT the same as trying to partition from within Ubuntu after adding the Gnome Partitioner from the repos.

If you're trying to partition a second drive, it might work OK.  But if you're trying to partition the same drive that Ubuntu's installed to, you run into trouble due to the fact that Ubuntu's mounted.  You can't modify a mounted partition.

So many people have reported better results with the GParted LiveCD that I just recommend that automatically, but I wasn't thinking through exactly what you're doing.  In your case, where you're partitioning a separate disk, I will admit that it can't be said for sure that GPLCD will work better.

I'd still do it anyway.  Having GPLCD on a bootable CD is a handy tool for yourself, for friends, for when you volunteer to help some poor sap who's screwed up their computer...

---

### Post by Elfo33 on 2008-11-15
Nope, I only pasted the portion for sdb, and left sda off.  How would the boot disk affect the lost space on the second drive.

And yes, I realize there is a drive index, from what I can tell in GParted that takes up a little over 14 MB.  Hardly worth talking about when I'm worried about 130 GB.

---

### Post by mgphl52 on 2008-11-15
> **Bartender said:**
> 

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

When I try to download this ISO, it stops at 13.2 MB without posting any errors! Is there another location recommended for this file?
[COLOR="Red"]Never mind the alternate location, I'm fetching System Rescue CD with wget -c now...[/COLOR]

Also, can this disc be used to shrink an existing ext2/ext3 partition without data loss?
[COLOR="Red"]Oops... just found the answer, Yes! Sorry for the newbie question...[/COLOR]

Many Thanks!

   -michael

---

### Post by Neostar on 2008-11-15
I'm not sure but you could also give Parted Magic a try. It's only a tiny download and it runs from RAM, so you can take the CD out. I have used Parted Magic myself and have also resized NTFS partitions with it. I have yet to try resizing an ext3 partition but it might work.

[http://partedmagic.com/](http://partedmagic.com/) <<-- Currently down but will be back soon.

You can find pictures from the older versions here
[http://www.thecodingstudio.com/opensource/linux/screenshots/index.php?os=partedmagic](http://www.thecodingstudio.com/opensource/linux/screenshots/index.php?os=partedmagic)

Parted Magic 3.1 CD (47.2MB)
[http://exo.enarel.eu/mirror/partedmagic/pmagic-3.1.iso.zip](http://exo.enarel.eu/mirror/partedmagic/pmagic-3.1.iso.zip)

Parted Magic 3.1 USB version (47.2MB)
[http://www.digitalincursion.net/partedmagic/pmagic-usb-3.1.zip](http://www.digitalincursion.net/partedmagic/pmagic-usb-3.1.zip)

---

### Post by mgphl52 on 2008-11-15
Neostar,  Thanks!

---

### Post by Col-1023 on 2008-12-25
I'm having similar problems with partitioning external hard drives.

I bought 3 WD 1TB drives, all formated with FAT32.  Nautilus reports them as haveing 931.3 GB wich is about right for real GB.

When I formated one of the drives using gparted downloaded from synaptic, Gparted reports the drive as 931.5 GB, but with 7.5 GB used, so the drive has 923 GB free.

However when I start nautilus and right click the drive and check properties, it shows 877 GB free with 46 GB used.

I used Gparted's check function to check the file system for errors, but this had no effect.

When I clicked on the drive there was 1 directory called 'lost+found" that supposedly had 7 items, though it was unreadable.

I also can't write to the drive because it is owned by root.

How can I fix this so that the 46 GB are recovered and I can use the drive as a normal user?

Should I try to reformat it as FAT32?

---

### Post by Bartender on 2008-12-25
col, you should start your own thread.
I recently posted regarding an external
[http://ubuntuforums.org/showthread.php?t=1016710](http://ubuntuforums.org/showthread.php?t=1016710)
Maybe that will help you.

All this stuff about permissions and owners confuses the hell out of me.  I think the level of complexity has a lot to do with Linux's Unix background, where the system is protected from users gaining access to devices they're not supposed to mess with.

Do you want to put Windows data on those externals?  If not, I'd format them to ext3.

---

### Post by Col-1023 on 2008-12-26
Thanks Bartender, the chown command helped.

I can now format the drive to ext3 and after using the chown command I can read and write to the drive.

From what I've read around the forums, I can't change the name of the drive without modifying the fstab file so the drive will mount automatically when plugged in, I don't want to do this, so I'll leave it with the ubuntu assigned name of (Disk, or 1000.2 GB Media).

I still haven't found out why EXT3 uses the 46.8 GB of disk space more than FAT32 when formatted.

When the drive is formatted in FAT32, is has 931 GB available, however when it is formatted in EXT3 it has 877 GB Available.


I just found this post [http://ubuntuforums.org/showthread.php?t=1020389&highlight=drive+change](http://ubuntuforums.org/showthread.php?t=1020389&highlight=drive+change) which discusses programs to use to change the labels of external drives.


A Little more digging found me this thread [http://ubuntuforums.org/showthread.php?t=794607](http://ubuntuforums.org/showthread.php?t=794607) which explains that EXT3 allocates 5% of disk space (which equals the 46 GB I said went missing) to root for journaling the file system and you have to use the tune2fs command if you want to change it.

---

