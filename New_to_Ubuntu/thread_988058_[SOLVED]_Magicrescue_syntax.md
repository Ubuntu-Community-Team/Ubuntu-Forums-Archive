---
title: "[SOLVED] Magicrescue syntax"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by Loki*PI on 2008-11-20
I'm trying to rescue some deleted files with Magicrescue. Using the following syntax:
$ magicrescue -r zip -d /media/WORKINGFILE/output /1dev/sdb3

results I'm getting are:  

opening /1dev/sdb3: No such file or directory

I'm not sure what it is telling me, it cannot find any zip type files, I'm trying to undelete openoffice files, it cannot find the partition 1dev/sdb3, or it cannot find the output file? 

Any help would be appreciated.

---

### Post by Dedoimedo on 2008-11-20
Try without 1 at the beginning, just /dev/sdb3.
Dedoimedo

---

### Post by Loki*PI on 2008-11-20
Yes, thanks.  Also need path to the zip.  This seems to work, at least it is running:

 sudo magicrescue -d /media/WORKINGFILE/output -r /usr/share/magicrescue/recipes/zip /dev/sdb3

Thanks.

---

### Post by Dedoimedo on 2008-11-20
My pleasure. If you're satisfied, close the thread and mark it solved!
Dedoimedo

---

### Post by Loki*PI on 2008-11-20
This is Absolute Beginner so I'll ask.  How do I do that, I've looked around for a button or something to mark it closed but nothing?

---

### Post by Dedoimedo on 2008-11-20
There you go:
[http://ubuntuforums.org/showthread.php?t=726219](http://ubuntuforums.org/showthread.php?t=726219)

Specifically:
[http://ubuntuforums.org/attachment.php?attachmentid=62807&d=1205686817](http://ubuntuforums.org/attachment.php?attachmentid=62807&d=1205686817)

Dedoimedo

---

