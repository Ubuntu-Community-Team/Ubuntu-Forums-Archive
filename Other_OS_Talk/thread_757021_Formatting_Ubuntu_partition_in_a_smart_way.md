---
title: "Formatting Ubuntu partition in a smart way"
date: 2008-04-16
forum: Other OS Talk
---

### Post by CrazyArcher on 2008-04-16
Hello

I want to safely wipe out Ubuntu from my dual-boot PC in order to make another one 100% Ubuntu and this one 100% Win. I have 2 HDDs here, one of which is wholly taken by Ubuntu, while another one is divided into 3 NTFS partitions. The main question is, which tools should use in order to format ext3 partition to NTFS, without messing up the bootloader. :confused:

---

### Post by mips on 2008-04-16
gparted?

---

### Post by CrazyArcher on 2008-04-17
Well, the program is not the main question - thanks for the suggestion, however. The question is whether brutal formating of the ext3 partition is likely to mess up my booting process. It's logical that when ext3 partition is formatted, the only possible thing for CMOS to do would be loading from NTFS, but I just want to assure myself.

---

### Post by CrazyArcher on 2008-04-17
OK, I wan't patient enough :)
I've deleted the ext3 partition with gparted and formated the drive into NTFS. However, GRUB still tries to work, and returns an error message instead of letting me boot Windows. 

Here's what it writes:
```
Searching for boot record from IDE-0..OK
GRUB Loading stage1.5

GRUB loading, please wait...
Error 17
```
Then it's just stuck. How can I solve this?

---

### Post by mips on 2008-04-17
Boot your windows install cd and select the repair option I think, you will get some like a dos screen, type help or ? and use the command fixmbr or restore mbr. I cannot remember the exact commands but you will see them.

---

### Post by mips on 2008-04-17
[http://www.blogmanno.com/?q=node/9](http://www.blogmanno.com/?q=node/9)

---

### Post by CrazyArcher on 2008-04-17
Thanks, I'll try out the recipe :)

---

