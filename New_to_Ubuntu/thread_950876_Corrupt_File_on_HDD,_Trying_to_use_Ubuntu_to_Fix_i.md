---
title: "Corrupt File on HDD, Trying to use Ubuntu to Fix it"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by DArtagnon on 2008-10-17
I recently helped a friend copy his files to an external hdd, reinstall his OS, and move the files back.  One of the files corrupted and WinXP wouldn't recognize the hdd.  The Kubuntu live CD still would, and I was able to copy back all of the information except the corrupt file.

The file was a *.txt and for some reason, Kubuntu thinks it's a directory that points to the directory it is in.

To clarify: when I try to open the folder /foo/bar.txt, it brings me to /foo/foo which has identical contents to /foo.

Because of this, when I try to delete bar.txt, it tries to be recursive and the file/folder count climbs quickly into the tens of thousands.

Thanks in Advance for any suggestions.

---

### Post by jerome1232 on 2008-10-17
Well since you already have all of that data off onto the Windows computer, I would just format the thing.

---

### Post by DArtagnon on 2008-10-17
I have other files on the drive, taking up about 130GB.  The transfer rate is so slow that I would much prefer to find a way of deleting the file.

Copying all of the files to my HD and back would take all day :P

---

### Post by bobnutfield on 2008-10-17
How are you trying to delete this file?  Have you tried:

> rmdir -R /foo

This should delete the directory /foo and everything under it.

---

### Post by jerome1232 on 2008-10-17
It sounds like it's a symlink to it's parent directory to me...

can you post the output of this, to see exactly what it is.
```
ls -l filenamehere
# or if it's a directory
ls -ld directorynamehere
```

---

