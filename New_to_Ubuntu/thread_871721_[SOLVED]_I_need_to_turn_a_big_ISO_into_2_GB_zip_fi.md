---
title: "[SOLVED] I need to turn a big ISO into 2 GB zip files"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by diablo75 on 2008-07-27
I need to turn a large file into several smaller zip (or rar) files, to be moved to another computer and then the contents of the zip reassembled.  How do I create a multiple file archive like this with Ubuntu?

---

### Post by vanadium on 2008-07-27
split. For documentation, see "man split"

---

### Post by diablo75 on 2008-07-27
No no, not sure if that will work for me.  The target PC is a windows system.  So I was wanting to use something (zip/rar files perhaps) that would do the trick easily...

---

### Post by billgoldberg on 2008-07-27
for creating split rar archives:.

Lets grab the rar program:

```
sudo apt-get install rar
```

Ok lets compress our directory of files:

To compress file(s) to split rar archive know which directory you want to compress, I used /home as an example

```
rar a -m5 -v5M -R myarchive /home/
```

Let me break the above command down

rar - starts the program
a - tells program to add files to the archive
-m5 - determine the compression level (0-store (fast)...3-default...5-maximum(slow))
-v5M - determine the size of each file in split archive, in this example you get files with size 5MB (if you wanted files of 512kB size you would write -v512k)
myarchive - name of the archive you are creating
/home/ - is folder of the files you wish to add to the archive


Copied from [http://www.ubuntu-unleashed.com/2008/05/howto-create-split-rar-files-in-ubuntu.html](http://www.ubuntu-unleashed.com/2008/05/howto-create-split-rar-files-in-ubuntu.html)

---

### Post by diablo75 on 2008-07-27
Sweet, I'll try the above instructions with rar.  Thanks!!!

---

### Post by vanadium on 2008-07-27
> No no, not sure if that will work for me. The target PC is a windows system.

Yes, "split" will still work. In Linux, you reconstruct the files like

cat split* > originalfile.iso

In Windows, you reconstruct the file with

copy /b split* originalfile.iso

---

