---
title: "How does the Linux filesystem work."
date: 2023-03-20
forum: New to Ubuntu
---

### Post by truij on 2023-03-20
Could someone explain me how the filesystem in Ubuntu works?
And how it works with 2 drives (C: (Windows) and F: (Ubuntu)?

---

### Post by grahammechanical on 2023-03-20
> Could someone explain me how the filesystem in Ubuntu works? And how it works with 2 drives (C: (Windows) and F: (Ubuntu)?

Asking multiple questions in the same thread causes confusion. Forum members who know the answer to this latest question may not go further than your initial question. We are allowed to open new threads for each question. There is no simple reply to this latest question. If it was in its own thread several comments could be given that will build up a more complete answer. 

Linux/Ubuntu identifies drives according to the interface with the motherboard. Such as IDE;Sata and Non Volatile Memory Express (nvme) or Solid Sate Drive (ssd). For example, on my desktop machine I have two sata hard drives. Ubuntu reports them as sda (sata drive a) and sdb (sata drive b). Partitions on each drive are numbered: sda1; sda2; sdb1; sdb2; and so on.

The Non Volatile Memory Express solid state drives on my laptop show up as nvme0n1 = the first drive. I only have one drive. Partitions show up as nvme0n1p1 and nvme0n1p2 and so on. I have not used Windows since Win98. In those days in Windows the first floppy drive was A; the second floppy drive was B and a hard drive was C. Beyond this I cannot go as my minds memory units from those days have be purged and over written by Linux knowledge.

Oh, by the way. There is more to be explained about the Linux file system

Regards

---

### Post by ajgreeny on 2023-03-20
As mentioned by grahammechanical you will  note that I have moved this new subject and question to its own thread.
This will avoid the total confusion that will happen if a thread moves too far away from your original query at [https://ubuntuforums.org/showthread.php?t=2485077](https://ubuntuforums.org/showthread.php?t=2485077)

---

### Post by ne29914 on 2023-03-20
[https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by TheFu on 2023-03-20
> **truij said:**
> Could someone explain me how the filesystem in Ubuntu works?

There isn't 1 file system for Linux. I think there are about 20 that are popular. Each fills a specific role based on specific use cases.  File systems are pretty nerdy topics.  Do you care about caching and atomic writes?  Do you care about volume management facilities?  Do you are about file name charactersets and length limitations?  There's a wikipedia article on file systems which has a few huge tables with the major limits. I can't find it today. Sorry.

For generic knowledge: [https://en.wikipedia.org/wiki/File_system](https://en.wikipedia.org/wiki/File_system) 

Some example local file systems:
[LIST]
[*]NTFS
[*]FAT32
[*]exFAT
[*]EXT2/3/4
[*]XFS
[*]ZFS
[*]ReiserFS
[*]JFS
[*]HPFS+
[*]BTRFS
[*]f2fs
[/LIST]
lots of others.

There are also networked file systems like NFS, CIFS, Plan9, DFS, GlusterFS and a few others. 

Each has pros and cons.  Performance, error correction, journaling, data resilience are all important, but the end-users assume (sometimes wrongly) that a file system won't lose their data as a trade-off with greater performance.

On ubuntu, the default file system tends to be ext4.  It is good, all-around, fast, file system that is journaled and doesn't lose data very often, if ever. It can handle all sorts of different workloads and integrates with other storage tools and volume managers to allow resizing up and down.  ext4 supports long file names, directory paths, and lots and lots of data, beyond what most home users would ever need.

XFS (created by SGI) has been around longer and has many of the same features as ext4. It is often a little faster that ext4, but it doesn't integrate with some other tools and cannot be reduced in size.  XFS is the default for RHEL.

ZFS (created by Sun Microsystems, now Oracle) merges the file system with the volume management and remote replication tools.  Further, ZFS validates what was written to storage actually got there. No other file system does this.  ZFS supports huge file system sizes using a 128-bit address space.  That's similar to IPv6 ... both can address more atoms than there are in our solar system.  Nobody will outgrow ZFS.  ZFS isn't usually the fastest file system, but it does support using fast caching devices to drastically improve performance.  ZFS also includes facilities that other file systems don't, like de-duplication, compression, and encryption. Before selecting ZFS, do your homework.

BTRFS (created by Oracle) was the F/LOSS world's answer to ZFS. It also merges the file system with the volume manager.  For many workloads BTRFS is an excellent choice, but there are caveats.  Before selecting BTRFS, do your homework.

exFAT is an improved FAT32 which is designed to be friendly towards flash storage by limiting the number of writes. It is not journaled, which means it isn't as safe as journaled file systems.  Trade-offs.  exFAT does support much larger flash storage than FAT32 does and it is an industry standard for cameras, smartphones and other portable devices that use flash storage larger than 64GB.  MSFT has patents on exFAT and was demanding payment by camera and smartphone device vendors for using it. IDK the current state, but believe MSFT ended that a few years ago.

f2fs is the F/LOSS answer to exFAT.  It too is not journaled, but it does support UNIX/Posix file and directory permissions. Often, f2fs is faster than ext4, under certain benchmark testing.  It is also free to use by anyone.  Some android devices support f2fs on their microSD data cards, but not the majority. It is always worth asking about this support, since it can make that external microSD card able to store programs, data, parts of the OS on the add-on storage.

NTFS isn't really just 1 file system. Over the decades, MFST has upgraded it silently.  It is a modern, journaled file system and has been since the late 1990s (if not forever).  NTFS isn't suitable for use by Linux systems, except for external data for a number of reasons.  Best to avoid it.

If you don't really care about file systems, but really were interested in what files go where in the file system, there's a wikipedia article about the Linux File System Hierarchy Standard  [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)  Well worth a skim.  I think the table in that article is probably all anyone needs to know.  I'd point out that most Linux distros follow the standard it outlines, mostly.  There are some definite parts that are ignored by all Gnome-based distros and those distros using snap packages.  

You asked another question which I don't understand. Linux doesn't have partition letters.  Microsoft "drive letters" is really "partition letters", BTW.  You've been lied to about that for decades by MSFT.

---

