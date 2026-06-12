---
title: "Ubuntu installer doesn't recognize windows 7 partition"
date: 2012-05-25
forum: New to Ubuntu
---

### Post by jmieres on 2012-05-25
Hi everyone, I bought a desktop computer recently and I installed windows 7, then I tried to install ubuntu but the installer didn't give me the option to install alongside windows.  I looked on the web for answers or something that helps me, and I've noticed that it's a frequent problem reported but it appears to me that there are several causes since there are many "solutions" posted but none worked for me.

Anyway, this is the output of sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x081914de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1638402047   819097600    7  HPFS/NTFS/exFAT

(by the way, windows 7 is working normally)

I am a newbie so I don't have much idea what's going on. Any help will be appreciated. Thanks.

---

### Post by oldfred on 2012-05-25
Welcome to the forums.

Windows only installs to gpt(GUID) partitioned drives if you boot with UEFI not BIOS, but you do not have a efi partition, so Windows converted the gpt partitioning to MBR(msdos) partitioning. But gpt includes a backup partition table and Windows only deletes the primary table. Then LInux tools see the backup gpt partition and the MBR partitions and get confused.

You need to remove the backup gpt partition data.

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)


Info:
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by jmieres on 2012-05-25
Wow, I'm very surprised for the quick answer. I was able to see the windows 7 partition with fixparts, sadly I ended up with an unbootable system, after many hours of fighting with it now i have both OS working (I hope). Thanks again for your advice, sure I'll come back in case I need something else, now I will sink into ubuntu depths.

---

### Post by TechIS on 2013-01-03
What exactly happened for you to end up with the unbootable system? And what did you do in order to make both OS's work? I'm having the same problem you described but I can't afford to lose too much time or end up with an unbootable pc because i'm having exams...

Thank you in advance!

---

