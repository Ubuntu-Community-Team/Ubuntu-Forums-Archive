---
title: "GParted: Error with Log (prep for Hardy install!)"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by lorienjohnson on 2008-04-27
Gateway Notebook MX6426

Hello!

I'm walking slightly blind through all of this. I've been a Windows user since 3.1, and am attempting to make the switch over before I'm forced into Vista. Therefore... Ubuntu!

I had a partitioning error during the Ubuntu install, so I came here and saw a recommendation for Gparted's manual partition. I attempted the manual partition, however I had another error.

The log follows:

**GParted 0.3.5**

Libparted 1.7.1

Shrink /dev/hda1 from 69.27 GiB to 32.17 GiB  00:13    ( ERROR )
     	
calibrate /dev/hda1  00:01    ( SUCCES )
     	
path: /dev/hda1
start: 11020590
end: 156280319
size: 145259730 (69.27 GiB)
calculate new size and position of /dev/hda1  00:00    ( SUCCES )
     	
requested start: 11020590
requested end: 78477524
requested size: 67456935 (32.17 GiB)
new start: 11020590
new end: 78477524
new size: 67456935 (32.17 GiB)
check filesystem on /dev/hda1 for errors and (if possible) fix them  00:03    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/hda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/hda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 74372981248 bytes (74373 MB)
Current device size: 74372981760 bytes (74373 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Found backup boot sector in the middle of the volume.
Space in use : 24358 MB (32.8%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 8762 MB 0
Multi-Record : 41164 MB 55709
$MFTMirr : 18598 MB 1
Compressed : 38896 MB 63967
Ordinary : 41700 MB 58703
You might resize at 24357847040 bytes or 24358 MB (freeing 50015 MB).
Please make a test run using both the -n and -s options before real resizing!
shrink filesystem  00:05    ( ERROR )
     	
run simulation  00:05    ( ERROR )
     	
ntfsresize -P --force --force /dev/hda1 -s 34537950719 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/hda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 74372981248 bytes (74373 MB)
Current device size: 74372981760 bytes (74373 MB)
New volume size : 34537943552 bytes (34538 MB)
Checking filesystem consistency ...
Accounting clusters ...
Found backup boot sector in the middle of the volume.
Space in use : 24358 MB (32.8%)
Collecting resizing constraints ...
Needed relocations : 12456 (52 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (1032 > 1024), not yet supported!
Please try to free less space.
check filesystem on /dev/hda1 for errors and (if possible) fix them  00:03    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/hda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/hda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 74372981248 bytes (74373 MB)
Current device size: 74372981760 bytes (74373 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Found backup boot sector in the middle of the volume.
Space in use : 24358 MB (32.8%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 8762 MB 0
Multi-Record : 41164 MB 55709
$MFTMirr : 18598 MB 1
Compressed : 38896 MB 63967
Ordinary : 41700 MB 58703
You might resize at 24357847040 bytes or 24358 MB (freeing 50015 MB).
Please make a test run using both the -n and -s options before real resizing!
grow filesystem to fill the partition  00:01    ( SUCCES )
     	
run simulation  00:00    ( SUCCES )
     	
ntfsresize -P --force --force /dev/hda1 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/hda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 74372981248 bytes (74373 MB)
Current device size: 74372981760 bytes (74373 MB)
New volume size : 74372977152 bytes (74373 MB)
Nothing to do: NTFS volume size is already OK.
real resize  00:01    ( SUCCES )
     	
ntfsresize -P --force --force /dev/hda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/hda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 74372981248 bytes (74373 MB)
Current device size: 74372981760 bytes (74373 MB)
New volume size : 74372977152 bytes (74373 MB)
Nothing to do: NTFS volume size is already OK.

========================================

Grow /dev/hda1 from 32.17 GiB to 35.09 GiB

========================================

Shrink /dev/hda1 from 35.09 GiB to 32.17 GiB    ( ERROR )

========================================

---

### Post by lorienjohnson on 2008-04-28
Is there a more appropriate place to post this question? I thought this would be best as I'm a) definitely a Linux beginner, and b) this is a problem I'm encountering in the install process.

Please let me know if there's a better subforum for this question!

Thanks!
- Lorien

---

### Post by Oldsoldier2003 on 2008-04-28
a couple pointers about resizing ntfs partitions.

Before you attempt to resize a NTFS partition you should chkdsk and defrag it. Of course making a backup of your impotatnt data is always a good idea before proceeding with any type of Filesystem changes in gparted.

Make sure you are running the most ccurrent stable version of the [GParted Live CD]("http://gparted-livecd.tuxfamily.org/"), and be sure to burn the the CD at a low speed. Run an integrity check of the CD beofre attempting to use it.

---

### Post by lorienjohnson on 2008-04-28
Thanks!

I'm running GParted from within the live CD of Hardy Heron. Do you think that's sufficient?

---

### Post by Oldsoldier2003 on 2008-04-28
> **lorienjohnson said:**
> Thanks!

I'm running GParted from within the live CD of Hardy Heron. Do you think that's sufficient?

it should be recent enough that you dont really need to worry about updating it.

---

### Post by lorienjohnson on 2008-04-28
Excellent, thanks! Defrag was sufficient.

I ended up undoing my partition in Gparted and using the Ubuntu installer to partition. I figure I can sort things differently when I've learned more about the process.

---

