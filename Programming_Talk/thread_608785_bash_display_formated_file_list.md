---
title: "bash: display formated file list"
date: 2007-11-10
forum: Programming Talk
---

### Post by S11 on 2007-11-10
Hi,

i was wondering if there is any possibility to display a sorted file list only with the last write date and time, filename and file size. Maybe with ls -l -G -g:

-rw-r--r--  1 5820 2007-10-20 17:29 botlib.log
-rw-r--r--  1 5820 2007-10-20 17:29 botlib2.log
The problem is I don't want the link count and the access permission shown.

This would be nice:
5820 2007-10-20 17:29 botlib.log

Any solution with pipes, other commands or what ever is welcome :D.
Thanks in advance.

---

### Post by cwaldbieser on 2007-11-10
```

ls -lgG --full-time | awk '{rest=""; for(i=7; i<= NF; ++i) rest = rest " " $i; printf("%s %s %s\n",  $3, $4, rest)}'   

```
The "--full-time" option puts the date in the format you indicated in your example.  The awk command prints the size and date fields, and fields 7 and greater.  These fields are the file names, which may include spaces.

This may not work correctly for file names with multiple spaces or tabs in the name, though.

---

### Post by geirha on 2007-11-11
You could cut away the first two fields with cut
```
ls -lGg | cut -d" " -f3-
```

---

