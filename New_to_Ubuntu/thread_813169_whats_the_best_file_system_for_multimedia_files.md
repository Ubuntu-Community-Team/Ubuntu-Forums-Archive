---
title: "whats the best file system for multimedia files"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by SILLAT on 2008-05-30
I have a 120gig fat32 hard drive with jus multimedia files like vids, pics, music,movies & a lil software thts half full. my other drive is used for ubuntu system/program files.
I'm planning to format my FAT32 120GB hard drive to a new file system to make better use of my hard drive.
whats the best file system to use in Ubuntu for storing multimedia files?
how can i format this drive to a new file system ?(i plan to back up my data to a portable drive first, then format the 120gig drive, then transfer my files back to my drive)

---

### Post by quelx on 2008-05-30
ext3, it's the most mature of the linux file systems (okay ext2) has the most tools and the most support (*read* everyone uses it) the amount of space you'll gain from choosing something else will not outweigh this fact.  Removing journaling may give you some spave and using ext2 would do that but it would not be enough to justify not having a journalized file system.

---

