---
title: "grub stage1"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by joeboentoe on 2008-06-11
I was wondering, how does stage1 know where he must find stage2? What info is located in stage1 and how can u change it?

thanks

---

### Post by meierfra. on 2008-06-11
> I was wondering, how does stage1 know where he must find stage2?
The answer depends on whether the stage1.5 files are used or not.

Case 1)  Stage 1.5 file is used. (This is the usually the case, when grub is install to the MBR of hard drive)

Then the stage 1.5 file contains the following information:

I)  The partition on which the stage2 files are stored (something like "85", where "85: means 9th partition on 6th hard drive; slightly different if the stage 1 and stage2 files are on the same hard drive)
II)  The full path of the stage2 files (usually /boot/grub/stage2)
III) The full path of the "menu.lst" (usually /boot/grub/menu.lst)

(The stage 1.5 file is located right after the stage1 file)


Case 2)  No Stage1.5 file is used. (This is the usually the case, then grub is install to boot sector of a partition)

Then the stage1 file contains the following information:

I)  The partition on which the stage2 file is stored. 
II) The physical location  of the stage2 file (the number of bytes from the beginning of the partition to the stage2 file)


> how can u change it?
You  could use "dd" to manually overwrite the stored information. But it is much easier to reinstall grub: Click on FixGrub  in my signature (Edit: Just saw some of you other post, you clearly already know how to reinstall grub)

For more information:
[URL="http://www.geocities.com/thestarman3/asm/mbr/GRUB.htm"]
The GrubMBR[/URL]
[URL="http://www.gnu.org/software/grub/manual/grub.pdf"]
The Grub Manual[/URL]
[URL="http://www.gnu.org/software/grub/"]
Gnu Grub[/URL]

If you would like more detailed information, just asked.

---

### Post by Duck2006 on 2008-06-11
Also stage 1 and stage 2 are loaded into the MBR as stage 1.5 is to large to load to the MBR it is loaded to /boot/grub folder.

---

### Post by joeboentoe on 2008-06-11
thanks, this clears things up :), also very interesting links.

---

### Post by meierfra. on 2008-06-11
> Also stage 1 and stage 2 are loaded into the MBR as stage 1.5 is to large to load to the MBR it is loaded to /boot/grub folder

Not quite:

stage1    is located in  the MBR or the boot sector of partition(  first sector of the hard drive or partition)
stage1.5  is either not used or right after the mbr.(sectors 2-16)
stage2    is located in /boot/grub 


Sizes: 
stage1..........512 b
stage1.5......8000 b
stage2.....130000 b
MBR..............512 b

---

