---
title: "Shotwell will not launch"
date: 2013-01-28
forum: New to Ubuntu
---

### Post by Thumbs1976 on 2013-01-28
Installed Shotwell and was importing library when system crashed. Now Shotwell wont launch. Tried removing and reinstalling but no joy. Runs when i sudo shotwell but when i run in terminal i get the following

shotwell
cp: cannot stat `/home/john/.shotwell/data/photo.db.bak': No such file or directory
**
ERROR:/build/buildd/shotwell-0.12.3/src/db/VersionTable.vala:18:version_table_construct: assertion failed: (_tmp3_ == SQLITE_OK)
Aborted (core dumped)


Any ideas for a beginer???

---

### Post by ajgreeny on 2013-01-28
Try removing the hidden /home/john/.shotwell folder and everything in it, then see if shotwell will start.  You will have to re-import all your pictures again, which can take an age in my experience, which is one of the many reasons why I prefer digikam, even in gnome.

---

### Post by Thumbs1976 on 2013-01-28
Many thanks, that has worked a treat!

And now i know how to find hidden files....

---

### Post by ajgreeny on 2013-01-28
Great!
Please mark the thread as SOLVED from the thread tools menu at the top.

---

