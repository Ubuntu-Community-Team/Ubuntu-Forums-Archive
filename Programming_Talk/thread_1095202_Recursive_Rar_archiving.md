---
title: "Recursive Rar archiving"
date: 2009-03-13
forum: Programming Talk
---

### Post by houseonfire on 2009-03-13
I'm wondering if theres an already existing command that I missed where I can specify a directory and have each file in the directory go into an rar archive, and if the file is more than a certain amount, it splits the archive.
If not, how would I go about doing this in Python 2.6?

---

### Post by geirha on 2009-03-13
If you install [rar](apt://rar), you can archive with something like:
```
rar a -r -v1024k name.rar /path/to/files
```
The above will add files recursively (-r), and split to files of 1024KiB (-v1024k) in size.

Read the man-page for other options.
```
man rar
```

---

### Post by houseonfire on 2009-03-14
Thanks for your help. You made some things aware to me that I did not know about.
Is it possible to archive every file in a folder into their own (seperate) rar files?

Example

folder1:
video1.avi
video2.avi
video3.avi

Then use the rar command to archive every file in the folder:

folder1:
video1.rar
video2.r01
video2.r02
video3.rar


EDIT:
I wined winRAR, highlight the files you want to archive in winrar, click add, select a split size (100m for 100mb) and then click on the files tab, check the "split files into separate archives".

---

