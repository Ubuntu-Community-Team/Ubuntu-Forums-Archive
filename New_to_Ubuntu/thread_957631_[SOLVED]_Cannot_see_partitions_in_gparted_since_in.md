---
title: "[SOLVED] Cannot see partitions in gparted since installing Mandriva One 2009"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by AndrewS on 2008-10-24
Hello

I have a small problem...

I have a PC running XP and Ubuntu 7.10.  The other day I ran gparted and shrunk the XP partition then I installed Mandriva One 2009 (OK, sorry, just wanted to try it!). I've decided I don't like it that much, so I ran gparted again, intending to delete that partition; gparted just shows one unallocated partition of around 230GB.  This can't be right, as I can boot all three OS's, and fdisk -l shows everything as it should be.

I was going to try the following, which I got from another post on here:

[INDENT]boot from a gparted liveCD
open a terminal, and run testdisk
write the partition table to disk (assuming it looked right...)[/INDENT]

Any comments before I try it???

TIA

Andrew

---

### Post by Duck2006 on 2008-10-24
From the terminal do,

sudo fdisk -l

and post the output.

---

### Post by AndrewS on 2008-10-24
Output looks like this:

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xda3b81f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         574     4610623+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *         575       15872   122881185    7  HPFS/NTFS
/dev/sda3           24891       29671    38403382+  83  Linux
/dev/sda4           15873       30515   117619897+   5  Extended
/dev/sda5           15873       16891     8185086   83  Linux
/dev/sda6           30362       30515     1236973+  82  Linux swap / Solaris
/dev/sda7           29672       30361     5542362    b  W95 FAT32
/dev/sda8           16892       17400     4088511   82  Linux swap / Solaris
/dev/sda9           17401       24890    60163393+  83  Linux

Partition table entries are not in disk order


Andrew

---

### Post by AndrewS on 2008-10-25
These are the outputs from testdisk (run under Ubuntu):

Analyze:

Disk /dev/sda - 250 GB / 233 GiB - CHS 30515 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P hid. FAT32 LBA           0   1  1   573 254 63    9221247 [RECOVERY]
 2 * HPFS - NTFS            574   0  1 15871 254 63  245762370 [Windows]
 3 P Linux                24890   0  1 29670 254 63   76806765
 4 E extended             15872   0  1 30514 254 63  235239795
Space conflict between the following two partitions
 4 E extended             15872   0  1 30514 254 63  235239795
 3 P Linux                24890   0  1 29670 254 63   76806765

Proceed:

Disk /dev/sda - 250 GB / 233 GiB - CHS 30515 255 63
     Partition               Start        End    Size in sectors
D FAT32                    0   1  1   573 254 63    9221247 [RECOVERY]
D HPFS - NTFS            574   0  1 15871 254 63  245762370 [Windows]
D Linux                15872   1  1 16890 254 63   16370172
D Linux Swap           16891   1  1 17399 254 63    8177022
D Linux                17400   1  1 24889 254 63  120326787
D Linux                24890   0  1 29670 254 63   76806765
D FAT32 LBA            29671   2  1 30360 254 63   11084724
D Linux Swap           30361   1  1 30514 254 63    2473947





Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
FAT32, 4721 MB / 4502 MiB


Does this help resolve the problem?

TIA

Andrew





*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted

---

### Post by louieb on 2008-10-25
The Mandriva partitioner strikes again (disk drake I think).  Primary partition sda3 is inside extended partition sda4.  look at the start and end blocks in the fdisk listing.  Primary partitions should not be inside an extended partition. 

the pc will still work,  but GParted see the **primary partition **inside the** extended partition**, treats the disk as if it has an invalid partition table (it does)  and won't do anything except treat the disk as unformatted.

One option is to use **Mandriva's partitioner** and delete sda3. After doing that GParted should work.

---

### Post by AndrewS on 2008-10-25
louieb

Thanks for that. Before trying what you suggest (I assume disk drake will be on the Mandriva liveCD?), is it correct to say that sda3 will be the partition that was created for the Mandriva install?  I'd rather not delete the Ubuntu partition!

Andrew

---

### Post by louieb on 2008-10-25
From the output can't say for sure which Linux distro is installed where.  Could be sda3 or sda5 or sda9
To check boot to either Ubuntu or Mandriva and run```

mount
```
that will tell you which partition is the / (root) partition for that distro.

Haven't used Mandriva I've run into Disk Drake using PClinuxOS. You'll just have to look through the menus. 

Believe testdisk can delete the partition. That might be the better way to delete it.

---

### Post by AndrewS on 2008-10-25
OK, running mount in Ubuntu suggests it's on sda3, and in Mandriva it's sda5.  If I delete sda3 I guess I lose Ubuntu?  Is there any alternative?  Gparted ran OK before I installed Mandriva.

Andrew

---

### Post by drakeman007 on 2008-10-25
> **AndrewS said:**
> Hello

I have a small problem...

I have a PC running XP and Ubuntu 7.10.  The other day I ran gparted and shrunk the XP partition then I installed Mandriva One 2009 (OK, sorry, just wanted to try it!). I've decided I don't like it that much, so I ran gparted again, intending to delete that partition; gparted just shows one unallocated partition of around 230GB.  This can't be right, as I can boot all three OS's, and fdisk -l shows everything as it should be.

I was going to try the following, which I got from another post on here:

[INDENT]boot from a gparted liveCD
open a terminal, and run testdisk
write the partition table to disk (assuming it looked right...)[/INDENT]

Any comments before I try it???

TIA

Andrew

I was a mandriva user too, i thought that mandriva was the most cool os until ubuntu, now i can see the difference, the speed, everything is better in UBUNTU... And the support community is better! :lolflag:

---

### Post by louieb on 2008-10-25
Opps pushed the wrong button. Just wondering whats the end goal? How many partitions do you want and for what use?

The short of it is if you want to save your current Ubuntu setup.  you'll need to use something like partimage to copy sda3 off. Then restore it to another partition sda5 maybe? Then you'll have to fix GRUB and /etc/fstab to point to new location. 

I can help with that but a reinstall might be easier.

---

### Post by AndrewS on 2008-10-25
drakeman007 - I think I agree!  I was a fairly commited Ubuntu user, and just installed Mandriva One 2009 to have a look.  The longer I used it the more little niggles I found, so I decided to wipe it.  Which is where the big problem started (apparent loss of partitions...).

louieb - are you suggesting I re-construct the partition table along the lines you give?  What about plan B - I get rid of all the non-Windows partitions (sda3. 4. 5. 6. 8. 9); will that leave me with a disk that gparted can work with?  I can probably figure what I need to reinstall in Ubuntu, and back up any data files before I do this.

Andrew

---

### Post by louieb on 2008-10-25
> What about plan B - I get rid of all the non-Windows partitions (sda3. 4. 5. 6. 8. 9)
That should work. Before you do Replace Grub in the MBR with the windows boot loader. If you have your install CD boot to its recovery console and run
```
fixmbr
``` 
so at least you can boot widows till you get Ubuntu installed. 
Or just don't delete sda3 and let GRUB keep working. Ubuntu will complain about swap missing. but thats easy to fix. 
Come to think of it before you delete the partitions edit **/etc/fstab**  and comment out the swap line. that will keep Ubuntu from complaining after swap is deleted.

One question does it boot to Mandrivas grub or Ubuntus?

---

### Post by AndrewS on 2008-10-25
Sorry, this is getting a bit confusing...  What I would be happy with is a PC that can boot XP (which is what it defaults to now), retains the small FAT32 partition, and has the rest of the hard drive unallocated.  All with gparted able to see the partitions.

So, I can run fixmbr from XP?  Then boot from the Mandriva liveCD and from the Mandriva Control Centre, "empty" all the non-windows partitions and write the new table to the disk?  I have to admit I find testdisk a bit scary!

Andrew

---

### Post by louieb on 2008-10-25
One more wrinkle going the delete route. can't delete sda4 without deleting sda7.
Its a logical partition and will have to be removed before you can delete sda4 the extended partition.

Just put your fdisk in start order. If you delete sda5, sda8, sda9, and sda3. That will leave you with a large amount of contiguous unallocated space. You will then be able to use GParted to add logical partition(s) back to the unallocated space. So no need to delete sda4 or sda7.

```

/dev/sda1 00001   00574 004610623+ 1c Hidden W95 FAT32 (LBA)
/dev/sda2 *0575   15872 122881185 7 HPFS/NTFS
/dev/sda4 15873   30515 117619897+ 5 Extended
/dev/sda5 15873   16891 008185086 83 Linux
/dev/sda8 16892   17400 004088511 82 Linux swap / Solaris
/dev/sda9 17401   24890 060163393+ 83 Linux
/dev/sda3 24891   29671 038403382+ 83 Linux
/dev/sda7 29672   30361 005542362 b W95 FAT32
/dev/sda6 30362   30515 001236973+ 82 Linux swap / Solaris

```All you have to delete with Mandriva or testdisk is sda3. After that GParted will work.  

 > I can run fixmbr from XP? Not that I'm aware of. but there are other ways  [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

### Post by AndrewS on 2008-10-25
louieb

All working now.  I deleted sda3 and, as you forsaw, gparted worked fine.  So I deleted every non-windows partition, fixed the mbr (I had to use a SuperGrub disc, but got there) and I've installed Ubuntu 8.04.

Very many thanks for your help with this (is there a way to formally do this so it shows up against your details?).  I'll mark the thread as SOLVED.

Thanks again

Andrew

---

### Post by louieb on 2008-10-25
Cool. Wondering what did you delete sda3 with? 
The thanks button is on the lower right corner of each post.

---

### Post by AndrewS on 2008-10-25
I'm afraid I have to be a bit vague about exactly what I did, I've deleted all Mandriva software from the PC, and don't intend to reinstall it in the near future!

As far as I recall, I booted the PC with a Mandriva One 2009 liveCD, and went to "Configure your PC".  There was an option there to manage/partition (cant remember exactly which) hard disks/partitions, and I "Emptied" sda3, then wrote the modified table to the hard drive.  GParted then worked fine, and I used that to delete all the other partitions I didn't want, then installed 8.04; I hope this release has matured a bit snce I first tried it (the day it was released)...

I've formally thanked you by clicking that button.

Andrew

---

