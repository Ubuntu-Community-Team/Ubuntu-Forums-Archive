---
title: "Defragment W95 FAT32 (LBA)"
date: 2021-11-03
forum: New to Ubuntu
---

### Post by nginmu on 2021-11-03
I have a conventional (spinning) external USB3 HDD connected directly via my laptop's own USB3 port (not via a hub etc)

WD Elements SE 25FE (1021)
500 GB — 392 GB free (21.5% full)
/dev/sdc1
One partition - W95 FAT32 (LBA) mounted at /media/me/xxxx-xxxx
2.1MB free space outside the partition.

It contains directories and files which are share between Lubuntu and Windows 11 on a dual-boot setup

It mounts and unmounts reliably

What would be the best and safest way to defragment the drive from Lubuntu?

---

### Post by TheFu on 2021-11-03
Defrag is a Windows thing. I think you should use Windows to do that.

Further, it would be smart to not use FAT32 unless required - that is only required today for the EFI partition share between Linux and Windows and every other UEFI booting OS on a system.  For a spinning HDD, NTFS would be a much better choice for data to be shared between Windows and Linux.  For flash storage, use exFAT if Windows and Linux are involved.  exFAT solves a number of issues with FAT32.

If you want to defrag on Linux ... considering there isn't any defrag too, you'll want to copy all the data off, format the partition clean (please don't use FAT32!!!), then copy all the data back. This will put the data back in contiguous blocks for each file - that is effectively de-fragmenting.

But really don't use FAT32 on spinning HDDs.  That's just a bad idea.

---

### Post by grahammechanical on 2021-11-03
I only use Linux but I do accept the rule that Windows file systems (hard drives, partitions) should be managed by Windows tools. If the drive needs defragging do it from Windows 11.

Regards

---

### Post by ActionParsnip on 2021-11-03
You can defrag FAT32 in Linux. FAT32 is an open source standard. Not sure about tools though. If the data is stored on flash memory then it won't make any difference

---

### Post by nginmu on 2021-11-03
I went ahead & allowed Windows 11 to perform a defrag on the drive whilst everything was still FAT32, it went ok, and the data's remained accessible in Linux.

It wouldn't be any problem to copy the data off, reformat the drive as NTFS, and load it back on.. so I'll do that if Lubuntu won't have any problems accessing it. I'd been avoiding using NTFS thinking it to be something Linux couldn't deal with properly.

Thanks :)

---

### Post by yancek on 2021-11-04
Defragging and running chkdsk on windows should always be done with windows tools, common sense,  Similar to running gsck (filesystem checks on Linux should be done from Linux.

All major Linux systems have been able to read/write to ntfs for a decade so that isn't a problem, the tools used for each OS should be those designed for that OS.

---

### Post by mastablasta on 2021-11-05
you can do it from windows system rescue disk, there are specialised software and i believe freeDOS defrag also works for fat32.

---

### Post by LokiScarlet on 2021-11-24
Like the others mentioned, converting to NTFS is a better way to handle that drive, being compatible with both Windows and Ubuntu, and more resilient to fragmentation than FAT. As a plus, whether it's FAT, NTFS, or EXT, you can rest assured the files you wrote or edited in Linux will most likely not be fragmented, as Linux has a different way of writing to these filesystems than Windows does. Additionally, NTFS is a journaled filesystem, so it'll perform better than FAT with the same amount of fragmentation.

That being said, while there isn't a safe, reliable way to defragment FAT/NTFS from Linux, you can still check the filesystem with fsck. If it has to make any repairs to the filesystem, some fragmented files might get repaired and thus defragmented. If the drive is less than half full, you could also copy everything to a subfolder of that drive, delete the original folders, then copy everything back and delete the subfolder (empty the trash if you're using the GUI to do this). As you can probably tell, that's tedious and not very effective, but it at least can take advantage of the fact that Linux will shuffle data around to try to make files contiguous when it writes them, even on Windows filesystems.

---

### Post by TheFu on 2021-11-24
NTFS is a journalled file system.
FAT32, exFAT are not.

Most Native Linux file systems are journalled too - ext3, ext4, jfs, xfs, zfs, btrfs, and probably 50 others.  However, there are 2 non-journalled native Linux file systems - f2fs and ext2.  

Journaling is safer. It is like how a DBMS supports transactions or it doesn't.  If something bad happens before the journal is completely updated, then it is incomplete and not applied. It is about "atomic" storage transactions.  Before we had journalled file systems, fsck would have to walk then entire file system tree to check for issues. That could take hours - sometimes - days.  On a journalled file system, the fsck only checks the top level structure and any incomplete journals, which takes seconds.  

Journaling is a good thing in a file system, but it does cause more writes which is why flash storage typically uses non-journalled exFAT or f2fs. Keep the writes down, with a slight increase in risk.
[https://en.wikipedia.org/wiki/Journalled_file_system](https://en.wikipedia.org/wiki/Journalled_file_system) has more details.

---

