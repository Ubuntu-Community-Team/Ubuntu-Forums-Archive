---
title: "Fast dir files count?"
date: 2009-05-17
forum: Programming Talk
---

### Post by cl333r on 2009-05-17
Folks,
I thought maybe there's some (low level) way to fetch the files count in a directory? Maybe the file systems keep track of this number in some settings field?
Anyone?

---

### Post by Martin Witte on 2009-05-17
As far as I know the only method to get this is to count the files, eg. with **ls -a|wc -l**, or **find . -type f | wc -l** if you want to include files in subdirectories

---

### Post by cl333r on 2009-05-17
I'm using C++ and I'm iterating through each dir entry to count them all. I thought there could be a "feature" in the filesystem(s) in the form of some field telling how many entries are in a given dir thus not having to iterate through each entry, would be much faster especially for dirs with many files. In my case the speed gains are worth the "workaround".

---

### Post by Arndt on 2009-05-19
> **cl333r said:**
> I'm using C++ and I'm iterating through each dir entry to count them all. I thought there could be a "feature" in the filesystem(s) in the form of some field telling how many entries are in a given dir thus not having to iterate through each entry, would be much faster especially for dirs with many files. In my case the speed gains are worth the "workaround".

You may want to look at the file /usr/include/dirent.h, but there's no such information there.

Why are you interested in just the number of entries?

---

### Post by cl333r on 2009-05-19
I'm creating a file browser, like Thunar but in C++ and faster, + a bit different, so when browsing a directory - all subdirectories should report the number of files within them, but I thought iterating through each subdir is a bit overkill and wished there was a workaround for that, would be (much) faster and avoid trashing the HDD. Since this happens almost every time one browses a given dir - I'm sure it's worth the effort, especially if the file browser is not gonna be used only by me.

---

