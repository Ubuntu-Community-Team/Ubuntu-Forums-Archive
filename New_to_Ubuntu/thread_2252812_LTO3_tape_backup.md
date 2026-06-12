---
title: "LTO3 tape backup"
date: 2014-11-14
forum: New to Ubuntu
---

### Post by bras2 on 2014-11-14
Hey guys,
I'm new to ubuntu and I have a crashed array. The array was backed up on old LTO3 tapes using dump. I have the tape drive up and running on an old server and can see everything on the tapes using the  "restore" command. I am looking for a way to export this list of contents to a text file. Please help

cd /mnt/tape
restore -if /dev/st0
restore>ls

From here I can see many files and folders. Is there a way to see or expand all folders? Or is there a way to export a list of files and folders to text file?

Thanks

---

### Post by bashiergui on 2014-11-16
```
ls -R /path/to/tape >> ListOfFiles.txt /path/to/wherever/you/want/output
```
Look at the man page for ls if you'd like to format and/or sort the results. The -R switch does a recursive listing which will get all subdirecory contents.

---

