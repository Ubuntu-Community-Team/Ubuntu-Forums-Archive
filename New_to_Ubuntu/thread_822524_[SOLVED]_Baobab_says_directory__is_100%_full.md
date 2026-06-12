---
title: "[SOLVED] Baobab says directory / is 100% full"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by raymondvillain on 2008-06-08
When I use Baobab (in Hardy 8.04) it shows the / directory to be 100% full, 3.4 Gigabytes.  I have gobs of free space (240+ Gigabytes free, according to Baobab).  Is this something to worry about?  Or do I need to resize my partitions and allocate more space to the / partition?  What is taking up so much space?  If I bring up a terminal window and change directory to /, how do I find sizes of files and directories in / ?

Thanks in advance

---

### Post by quelx on 2008-06-08
in the terminal ```
cd /
ls -lahSr
``` will show you the files (and their sizes),

```
df -h
``` will show the space on drives.

The 100% is telling you that of all the used space on the drive mounted at /, all of it is contained in the / directory.  This is normal and to be expected if all the subfolders of / are contained in the same drive partition (which they are in a default ubuntu installation).  

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

