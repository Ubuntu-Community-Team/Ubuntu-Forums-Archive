---
title: "Getting An External Hard Drive to Work With 3 Different OSes"
date: 2020-12-28
forum: Philippine Team
---

### Post by randytan on 2020-12-28
Hi All!

I got a 2TB external drive to safely back up my files from my current laptop, a legacy unit MBP (office issued), and I would like to format it so that I can use it with windows, MacOS, and Ubuntu. I have to occasionally use windows and MacOS for work but since new MBPs are expensive, thinking of going back to the Linux route again but I will most likely be sharing the data in the new external hard drive with the two aforementioned OSes.

I would like to use a format that can also work with big files as the current format in one of my current external drives cannot work with files larger that 4GB!

All advice and assistance is appreciated.

Thanks in advance!

---

### Post by CelticWarrior on 2020-12-28
> [COLOR=#000000]the current format in one of my current external drives cannot work with files larger that 4GB![/COLOR]
It must be FAT32.

Regarding your main question, Windows and any modern Linux can share NTFS formatted partitions as long as the Fast Startup feature in Windows is disabled (Windows 8 or newer). I don't know about Mac.

---

### Post by TheFu on 2020-12-28
For data only, not programs, NTFS is the only choice.  

It is not a suitable file system to backup OSes unless the backup tool used places the files, permissions, owner, group, ACLs, and xattrs into a blob-file, however.  That restriction drastically reduces the choice for backup tools, at least on Linux. Basically, only duplicity or a tool based on duplicity can be used for backups to NTFS.

There will be other complexities likely even for the data files, since methods to sync data efficiently are dependent on rsync and rsync tries to honor fully Unix permissions which aren't supported by NTFS.

Perhaps the best answer is to have 3 partitions on that HDD, formatted individually with the native file systems for the OSes involved.  NTFS, ext4, and whatever OSX uses.  Just a thought.  For data like music and videos that is accessed directly as files, NTFS is the best of poor choices.  It effectively has no security.

---

### Post by coffeecat on 2020-12-28
Have a look at exFAT. It's supported by Windows, MacOS 10.6.5 and later, and the Linux kernel starting with 5.4. The latter means that exFAT should work out of the box for Ubuntu 20.04, or you would need to install the packages exfat-fuse and exfat-utils in earlier versions of Ubuntu.

According to [WIkipedia](https://en.wikipedia.org/wiki/ExFAT), file size limit is 16 exbibytes which is so large I'm having difficulty getting my head around it. You certainly wouldn't have the 4GB limitation of FAT32.

Please let us know if you try exFAT and how you get on. This is a fairly perennial question - how to share external drives between the three operating systems. Being a Microsoft filesystem exFAT won't support Unix type permissions, but if you're just backing up personal files, it should do fine.

---

### Post by TheFu on 2020-12-28
exFAT is a great improvement over prior FAT options, but since it isn't journaled, it should be avoided on non-flash storage.
> The standard exFAT implementation is not journaled and only uses a single file allocation table and free space map. [https://en.wikipedia.org/wiki/ExFAT](https://en.wikipedia.org/wiki/ExFAT)

NTFS is journaled.  Anyone who remembers running an fsck/chkdsk knows the difference between journaled and non-journaled file systems.  A 2TB HDD, is almost certainly a spinning disk and a journaled file system would be the choice.

IMHO.

---

### Post by CelticWarrior on 2020-12-28
> [COLOR=#000000]exFAT is a great improvement over prior FAT options, but since it isn't journaled, it should be avoided on non-flash storage.[/COLOR]

[COLOR=#000000]+1
[/COLOR]

---

### Post by randytan on 2020-12-29
Hi All!

I apologize for being unclear with my intentions, this drive will store files, PDFs, photos, videos, basically data only. No apps or programs. Apps and Programs will be installed onto whatever computer system I'll be working with.

If it helps narrow things down further, the external drive I'm working with is a Seagate Backup Plus Slim. Upon checking the product website, it seems that this is already reformatted in exFAT as the manufacturer touts that the drive can be used with windows and MacOS. So I guess it would work with Linux as well? While no information on Linux, they do give some nice details on which format to use if you use either windows or Macs exclusively. They do say that exFAT is the way to go if using with both systems. They also warn about the no journaling thing mentioned by TheFu and that you can lose or corrupt data if the drive is not removed / unmounted from the system properly. Looks like I'll have to keep ejecting the drive whenever I leave my work area for any extended period of time. My MBP is hit or miss when drives are connected and it falls asleep. I guess this means I should reformat my other, older 1TB external drive so I can do away with FAT32!

Keep you input and feedback coming! I'm learning a lot and it is greatly appreciated!

---

