---
title: "physical devices : partitions : file system : files"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by aspergerian on 2008-08-28
Where is the best explanation (book, wiki, tutorial) for the relationship between (a) physical devices and their partitions, (b) the ubuntu file system, and (c) where within ubuntu to see what files are on each specific partition?

I've read lots of wiki explanations, etc, and still have no working knowledge in regard to what files are located in which partitions - for my Asus 901 running only 8.04.1 (ie, no Xandros). I've included three screen shots because they portray my computers' devices and file system. Gparted provides a little more information but doesn't tell me which files and which directories are on each partition.

Here's a practical example. If I want to write some data files to sdb5, I have no idea how to do that. Perhaps the pathway is within File Browser, but if so,  I don't know how to find the proper folder. 

Suggestions towards a book, wiki, or tutorial - in regard to what I've sketched above - would be appreciated.

:confused:

---

### Post by bangmalley on 2008-08-31
[this]("https://help.ubuntu.com/8.04/hardware/C/disks.html") article explains the filesystem and partition.
To write files to a partition, for example /dev/sdb5. u need to [mount]("http://library.gnome.org/users/user-guide/stable/gosnautilus-462.html.en") it 1st.

---

