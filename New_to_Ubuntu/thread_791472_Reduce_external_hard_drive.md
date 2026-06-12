---
title: "Reduce external hard drive"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by philipluna66 on 2008-05-12
I have a external hard drive with NFTS files on from my windows xp I am trying to reduce the size to make room for my Linux files but gparted hits an error
GParted 0.3.5

Libparted 1.7.1

Move /dev/sdc1 to the left and shrink it from 232.88 GiB to 86.40 GiB  02:19    ( ERROR )
     	
calibrate /dev/sdc1  00:00    ( SUCCES )
     	
path: /dev/sdc1
start: 63
end: 488392064
size: 488392002 (232.88 GiB)
calculate new size and position of /dev/sdc1  00:00    ( SUCCES )
     	
requested start: 0
requested end: 181197134
requested size: 181197135 (86.40 GiB)
new start: 63
new end: 181197134
new size: 181197072 (86.40 GiB)
check filesystem on /dev/sdc1 for errors and (if possible) fix them  00:17    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/sdc1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sdc1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 250056704512 bytes (250057 MB)
Current device size: 250056705024 bytes (250057 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 15858 MB (6.3%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 125096 MB 0
Multi-Record : 125097 MB 25
$MFTMirr : 125029 MB 1
Compressed : 15857 MB 5855
Ordinary : 125105 MB 4
You might resize at 83358347264 bytes or 83359 MB (freeing 166698 MB).
Please make a test run using both the -n and -s options before real resizing!
shrink filesystem  01:30    ( ERROR )
     	
run simulation  01:22    ( SUCCES )
     	
ntfsresize -P --force --force /dev/sdc1 -s 92772900863 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sdc1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 250056704512 bytes (250057 MB)
Current device size: 250056705024 bytes (250057 MB)
New volume size : 92772893184 bytes (92773 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 15858 MB (6.3%)
Collecting resizing constraints ...
Needed relocations : 16753 (69 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
The read-only test run ended successfully.
real resize  00:08    ( ERROR )
     	
ntfsresize -P --force --force /dev/sdc1 -s 92772900863
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
ERROR(95): Opening '/dev/sdc1' as NTFS failed: Operation not supported
The NTFS journal file is unclean. Please shutdown Windows properly before
using this software! Note, if you have run chkdsk previously then boot
Windows again which will automatically initialize the journal correctly.
check filesystem on /dev/sdc1 for errors and (if possible) fix them  00:16    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/sdc1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sdc1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 250056704512 bytes (250057 MB)
Current device size: 250056705024 bytes (250057 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 15858 MB (6.3%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 125096 MB 0
Multi-Record : 125097 MB 25
$MFTMirr : 125029 MB 1
Compressed : 15857 MB 5855
Ordinary : 125105 MB 4
You might resize at 83358347264 bytes or 83359 MB (freeing 166698 MB).
Please make a test run using both the -n and -s options before real resizing!
grow filesystem to fill the partition  00:16    ( ERROR )
     	
run simulation  00:08    ( SUCCES )
     	
ntfsresize -P --force --force /dev/sdc1 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sdc1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 250056704512 bytes (250057 MB)
Current device size: 250056705024 bytes (250057 MB)
New volume size : 250056700416 bytes (250057 MB)
Nothing to do: NTFS volume size is already OK.
real resize  00:08    ( ERROR )
     	
ntfsresize -P --force --force /dev/sdc1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
ERROR(95): Opening '/dev/sdc1' as NTFS failed: Operation not supported
The NTFS journal file is unclean. Please shutdown Windows properly before
using this software! Note, if you have run chkdsk previously then boot
Windows again which will automatically initialize the journal correctly.

========================================

How do i reduce the NFTS to about 80gig and make the rest available for use in Ubuntu I rearly need the extra capacity

---

### Post by steve-shinn on 2008-05-12
Did you defragment the hard drive before trying to add another partition ?

---

### Post by philipluna66 on 2008-05-12
No I didnt I will put it back in my xp computer and defrag see if that works thanks

---

### Post by steve-shinn on 2008-05-12
Best to defrag a couple of times.

If all else fails, you can still save your linux files to an ntfs formatted hard drive.

---

### Post by philipluna66 on 2008-05-12
No I can't that is why I am trying to partition it My ubuntu 8.04 says it canot access NFTS files

---

### Post by steve-shinn on 2008-05-12
Have you tried the following :-

[http://ubuntuforums.org/showthread.php?t=773816&highlight=ntfs](http://ubuntuforums.org/showthread.php?t=773816&highlight=ntfs)

It would appear that this not an uncommon problem with 8.04

---

### Post by philipluna66 on 2008-05-12
THANKS that worked great I can now access my usb disk and it is showing my ntfs files

---

### Post by Crossroads on 2008-05-12
> **steve-shinn said:**
> Best to defrag a couple of times.

If all else fails, you can still save your linux files to an ntfs formatted hard drive.

I've read this advice a few times about defragging before using GPartEd.

So that I understand, is the underlying reason that GPartEd does not move sectors when resizing a partition? In effect, it is releasing unused contiguous sapce from the end of an existing partition.

I could be missing something.

---

### Post by Crossroads on 2008-05-13
Anyone ??

---

### Post by philipluna66 on 2008-05-14
If it is necessary to defrag before using Gparted can you defrag in Ubuntu I put my hard drive back in my Win xp machine. I am not sure weather defrag helped or not because I defraged then I /sbin/mount.ntfs-3g --help in the terminal window so not sure which worked but after 8.04 could mount my hard drive read the files but then Gparted would not let me partition the hard drive but its OK I just created files and that works OK for me

---

