---
title: "Aligning partitions on an AFD, WD30EZRS"
date: 2011-09-23
forum: New to Ubuntu
---

### Post by cougar694u on 2011-09-23
I've been doing lots of reading the last few days about the 4k AFD disks and have created and recreated partitions over and over on this disk, trying to get the proper alignment.

The disk is actually for my Linksys NMH-300-series NAS.  It requires three partitions: swap, ext3, and reiserfs (in that order).

The disk is WD30EZRS and I formatted it using ubuntu with the following fdisk commands:


partition 1 = starting at sector 2048, +259M, type = 82
partition 2 = starting at default (forget, but can look it up), +134M, type = 83
partition 3 = starting at default, +1843, type = fd


I then formatted each like this:


mkswap -c /dev/sdb1
mkfs.ext3 -c /dev/sdb2
mkfs.reiserfs /dev/sdb3


When  I did an fdisk -lu, partition 1 starts at 2048, but each partition  states it doesn't end in a cylinder boundary.  For instance, partition 1  ends at say 54, and partition 2 starts at 54 also (not exact, just  using as example).


When you first boot up the NAS, it  says the RAID failed, so you revert to single disk mode and everything  works fine.  I assumed that since the first partition was aligned at  2048, and adding each subsequent partition by size, they would be  aligned properly.  fdisk does pick it up as "Sector size  (logical/physical): 4096 bytes / 4096 bytes&#65279;", so I assumed it was  correct.  Would I be better off reformatting, starting partition 1 at  2048, having it end at a cylinder making it near 271MB, and partition 2  start at the next cylinder?  The starting point of each partition (in sectors) is divisible by 2048  (and obviously 8 ), so I figured it is aligned properly.  I was going to  try to start partition 1 at 64, but it wouldn't let me.  The lowest it  would do was 2048.


It has to be MBR because the NAS doesn't support GPT, thus only 2TB, so essentially wasting 1TB.  Sucks, I know, but it was an RMA WD sent back to me for my WD20EARS.  The WD20 worked out of the box, although partition 1 started at 63.


I posted this in the forum for the linksys NAS, but the brainpower there isn't the same as it is here.

---

### Post by srs5694 on 2011-09-23
> **cougar694u said:**
> The disk is WD30EZRS
...
When  I did an fdisk -lu, partition 1 starts at 2048, but each partition  states it doesn't end in a cylinder boundary.  For instance, partition 1  ends at say 54, and partition 2 starts at 54 also (not exact, just  using as example).

Cylinder boundaries used to be relevant but today they aren't. You can safely ignore any comments about them that fdisk might produce. Likewise, partition end points are irrelevant, except to the extent that they might affect the start point of the next partition when you create partitions.

> fdisk does pick it up as "Sector size  (logical/physical): 4096 bytes / 4096 bytes&#65279;", so I assumed it was  correct.

*That* is surprising, and could be at the root of your problems. The last I heard, all commonly-available internal hard disks had 512-byte logical sector sizes. Advanced Format drives have 4096-sector physical sector sizes, but most of them lie about this, so that fdisk reports both physical and logical sector sizes as 512 bytes. I've seen one or two reports of 512/4096 logical/physical sizes, though, so some drives might not be fibbing any more. Also, some external drives use the 4096/4096 configuration, but a Web search suggests this is an internal drive you're describing.

It's conceivable that you've got a new model that reports its true sector size for both its physical and logical sector size. If so, you should be able to use the whole disk using an MBR partition scheme; but equally, this could be causing your NAS problems, since it might not be coping well with this configuration. OTOH, it could be that there's something wrong with the disk that's causing it to report a 4096-byte sector size, or that you've encountered an obscure bug in fdisk or in the Linux kernel that's causing fdisk to think the disk has a 4096-byte sector size when in fact it doesn't. Such a bug could cause problems because the partition table would be written incorrectly.

One more point: If the disk really does use 4096-byte logical *and* physical sectors, there's no need to be concerned with alignment issues. Those issues are only relevant to disks with a logical sector size that's smaller than the physical sector size, to SSDs, and to some types of RAID arrays.

> Would I be better off reformatting, starting partition 1 at  2048, having it end at a cylinder making it near 271MB, and partition 2  start at the next cylinder?  The starting point of each partition (in sectors) is divisible by 2048  (and obviously 8 ), so I figured it is aligned properly.

If the start points of your partitions (measured in sectors) are divisible by 8, everything's fine in terms of alignment.

At this point, I'd be more concerned with the sector size question. You might want to check what parted thinks about this, to see if it agrees with fdisk on the matter. If possible, checking it in another OS might also be worthwhile.

> It has to be MBR because the NAS doesn't support GPT, thus only 2TB, so essentially wasting 1TB.  Sucks, I know, but it was an RMA WD sent back to me for my WD20EARS.  The WD20 worked out of the box, although partition 1 started at 63.

The WD20EARS uses Advanced Format, IIRC, so if you had it partitioned with its first sector starting at 63, you were suffering from impaired performance.

---

### Post by cougar694u on 2011-09-23
> **srs5694 said:**
> The last I heard, all commonly-available internal hard disks had 512-byte logical sector sizes. Advanced Format drives have 4096-sector physical sector sizes, but most of them lie about this, so that fdisk reports both physical and logical sector sizes as 512 bytes. I've seen one or two reports of 512/4096 logical/physical sizes, though, so some drives might not be fibbing any more. Also, some external drives use the 4096/4096 configuration, but a Web search suggests this is an internal drive you're describing.

That 4k/4k was a c&p prior to when I put it in the NAS and let the NAS reformat to 'single disk mode'.  I popped the disk out, put it back in my linux box and got this:

```
fdisk -l
Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          35      272384   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sdb2              35          53      144384   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sdb3              53      240641  1932531040   fd  Linux raid autodetect
Partition 3 does not end on cylinder boundary.

``````
fdisk -lu
Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048      546815      272384   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sdb2          546816      835583      144384   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sdb3          835584  3865897663  1932531040   fd  Linux raid autodetect
Partition 3 does not end on cylinder boundary.

```Maybe after looking at the fdisk screen for hours on end (doing this over and over), I just missed it and saw IO size, not sure.

I believe you're right about the performance issue with the wd20ears starting at 63, the NAS did run slower with the 2TB disks.  I got an RMA on the second disk because after the NAS was powered off for a few days (took it with me on vacation), the disk showed as NEW, and thus the RAID-1 was degraded.

The NAS functions fine, shows the volume as green, but I haven't tested performance yet.

As far as parted, here's what I get:
```
(parted) print                                                            
Warning: /dev/sdb contains GPT signatures, indicating that it has a GPT table.  However, it does not have a valid fake msdos partition table, as it should.  Perhaps it was corrupted -- possibly by a program
that doesn't understand GPT partition tables.  Or perhaps you deleted the GPT table, and are now using an msdos partition table.  Is this a GPT partition table?
Yes/No? yes                                                               
Model: ATA WDC WD30EZRS-00J (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags

(parted)                                                                  

```Telling it No when asked if it's GPT exits with no info.  The GUI disk utility (system > administration > disk utility) shows the partitions correctly, as well as the 1TB of wasted space.  Obviously, gparted shows it as blank, too.  Like I said, though, the NAS functions fine.

I really appreciate the info, you've more than answered my question(s).

---

### Post by srs5694 on 2011-09-24
The parted output indicates that you've got GPT data on the disk, perhaps from a former partitioning attempt -- or maybe the disk came from the factory with GPT data on it. It's puzzling that fdisk didn't squawk about this, unless perhaps you've got GNU fdisk installed (it uses libparted and so it behaves differently in the face of such problems) or a very old version of Linux fdisk. Typing "fdisk -v" should reveal version information.

In any event, you should get rid of the stray GPT data. This is most easily accomplished with my [FixParts](http://www.rodsbooks.com/fixparts/) program. Consult its Web page for details of how to get rid of GPT data. It's quite simple, really -- just launch it on the disk and answer "Y" when you're asked if you want to delete the old GPT data. You can then quit by typing "q" at the main menu and it should be fixed.

I can't promise that getting rid of the stray GPT data will fix your underlying problem, but it might. Even if it doesn't solve the problem, leaving old GPT data in place could create more problems down the road, so it's best to get rid of it now.

---

### Post by cougar694u on 2011-09-24
ran fixparts and all looks well
```
GNU Parted 2.3
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) p                                                                
Model: ATA WDC WD30EZRS-00J (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  273MB   272MB   primary  linux-swap(v1)
 2      273MB   413MB   141MB   primary  ext3
 3      413MB   1998GB  1997GB  primary                  raid

(parted)
```

fdisk -v gives fdisk (util-linux-ng 2.17.2)

Thanks again for all the help!

---

