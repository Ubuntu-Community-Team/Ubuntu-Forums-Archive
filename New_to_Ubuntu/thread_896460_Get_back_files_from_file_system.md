---
title: "Get back files from file system"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by um_nirvani on 2008-08-21
Hi guys,

I moved some files to /tmp and after reboot i lost all those files..

Is there any way to get back those deleted files. My root partition type is ext3. How do i get back those files. i guess i can since it is ext3 which is a journaling file system.

---

### Post by kpkeerthi on 2008-08-21
I use [System Rescue CD]("http://www.sysresccd.org/Main_Page"). I comes with [tools]("http://www.sysresccd.org/System-tools") to recover data.

---

### Post by fiddledd on 2008-08-21
AFAIK you can't recover files deleted from the ext3 file system. At least that's what one of it's developers says, and I quote: 
"In order to ensure that ext3 can safely resume an unlink after a crash, it actually zeros out the block pointers in the inode, whereas
ext2 just marks these blocks as unused in the block bitmaps and marks the inode as "deleted" and leaves the block pointers alone.

Your only hope is to "grep" for parts of your files that have been deleted and hope for the best."

---

