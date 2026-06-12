---
title: "nedd absolute pathname"
date: 2009-02-20
forum: Packaging and Compiling Programs
---

### Post by veda87 on 2009-02-20
I am using ext2 file system on linux-2.6.26. i want to know whether the file system keeps a record of the absolute pathname for each and every file that have been created. if so, where could i find it.

---

### Post by geraldm on 2009-02-20
I am not aware of any record of absolute pathnames.

You might want to look into the package fam. (file access monitor).  You might find a way to extract the information you want from it.  There is also a wrapper package named fam++

Gerald

---

