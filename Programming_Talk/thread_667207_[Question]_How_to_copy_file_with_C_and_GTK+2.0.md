---
title: "[Question] How to copy file with C and GTK+2.0?"
date: 2008-01-14
forum: Programming Talk
---

### Post by Arlanthir on 2008-01-14
Hi.
I'm doing a little PSP managing utility (along the lines of qpspmanager, for those who know it) using GTK with C. 
I'm in a part where I need to copy files from the PC to the PSP (not local, then) and, if possible, show a little progress bar. 
Thing is, the only way I can copy the files is using a system call to exec cp. I've tried the copy char by char variant with no success, it works fine for files in the desktop but once you do that to a PSP with files over 1GB it's not *that* productive.
I was wondering if someone here knew a better way to do this, like nautilus does, exactly. 

Another doubt I have is how can I see the total or free space (any, or both, will do) in a given dir/drive with a C function?

Thank you very very much!

---

