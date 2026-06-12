---
title: "Removing duplicate data and detecting data errors without ZFS."
date: 2014-04-28
forum: New to Ubuntu
---

### Post by YQ002lc2 on 2014-04-28
I'm aware that ZFS deduplication is a solution for removing duplicate files, but it takes a lot of memory.

Fdupes is good at identifying duplicate files, but can easily delete real data in the case of symbolic links.
The process of manually checking each duplicate to ensure data is preserved makes this impractical. 
Is there a good fdupes alternative, preferably graphical through nautilus or another browser, that doesn't suffer from the same symbolic link problem?

Also, is there a program that can scan for damaged files in a set of data?....

---

### Post by HermanAB on 2014-04-29
See par2 and pypar2.

---

