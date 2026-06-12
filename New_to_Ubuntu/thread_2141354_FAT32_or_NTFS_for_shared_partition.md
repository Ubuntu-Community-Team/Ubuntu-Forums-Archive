---
title: "FAT32 or NTFS for shared partition?"
date: 2013-05-02
forum: New to Ubuntu
---

### Post by JonthueM on 2013-05-02
I been looking and looking and looking but everyone seem to mostly be on the FAT32 or NTFS shared partitions, so my question is which one do you prefer/use and why do you use them? What is the con and pro to both for a newbie like me who is deciding on what type of partition format to do it on?

---

### Post by dino99 on 2013-05-02
windows can read/write the ext (3/4) format, and linux knows about ntfs; so no worry

---

### Post by oldfred on 2013-05-02
NTFS.

Only use FAT32 for small partitions or devices like your phone or camera cards. Or installer flash drives or the small FAT32 partition required for UEFI boot. 
FAT32 has no journal, so a large partition may not be easily repaired or chkdsk will take forever. With a small partition a journal is less important.
Also FAT32 has a file max of 4GB (less 2 bytes). So you cannot store large videos or backups. About 7 years ago I had a FAT32 partition and was copying backups to it. I noticed they always were about 4GB but did not think too much at the time. But I never had any backups as they all were truncated and damaged. Fortunately I never needed them.

---

### Post by oldfred on 2013-05-02
@dino
Window can read ext3 and maybe ext4, but I do not think it can write to Linux partitions due to ownership & permission issues.

Linux NTFS driver allows read write to NTFS, but we still suggest setting a Windows system partition as read only to avoid accidental damage. The Linux NTFS driver exposes all the hidden files & folders that Windows hides.
Best to use a separate NTFS shared data partition.

---

### Post by slickymaster on 2013-05-02
If you're using both Ubuntu and Windows, then I would advise on choosing NTFS, because you should probably store files you want accessible by both systems. Ubuntu can safely read and write files on the Windows partition itself.

Like oldfred stated, FAT32 doesn't support files larger than 4 GiB. These days, you may well have files that large, depending on what you're using your computer for, and neither exFAT nor FAT32 support file ownership and permissions.

---

### Post by JonthueM on 2013-05-02
Interesting this site says that 

[COLOR=#000000][FONT=bitstream vera sans][IMG]http://www.psychocats.net/ubuntu/images/partitioning3.png[/IMG][/FONT][/COLOR]
[COLOR=#000000][FONT=bitstream vera sans]Pictured above is a more common scenario&#8212;a Ubuntu partition, a Windows partition, and a FAT32 partition in the middle to share data between the two operating systems. **This is frequently recommended on the [Ubuntu Forums]("http://www.ubuntuforums.org/") as a good way to partition a drive, since both Windows and Ubuntu can natively read from and write to FAT32.**[/FONT][/COLOR]
[COLOR=#000000][FONT=bitstream vera sans]Ubuntu now has a pretty reliable mechanism for reading from and writing to NTFS, but some people like to play it extra safe and have a separate FAT32 partition for both Windows and Ubuntu to work from.

[/FONT][/COLOR][http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by oldfred on 2013-05-02
The site is being updated.
[http://ubuntuforums.org/showthread.php?t=416802&p=12573520#post12573520](http://ubuntuforums.org/showthread.php?t=416802&p=12573520#post12573520)

I often refer to psychocats as the info is good, but that page is very dated. It show ext3 for / which has been ext4 since 9.10. I did use FAT32 back in 2006 as back then the NTFS driver has some issues, but changed to NTFS with 9.10 when I converted from 32bit install to 64 bit.

---

