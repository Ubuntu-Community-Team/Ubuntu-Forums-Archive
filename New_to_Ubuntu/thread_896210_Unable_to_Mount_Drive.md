---
title: "Unable to Mount Drive?"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by hellodoggie on 2008-08-20
Maybe you can help me make sense of this error message:
[[IMG]http://img373.imageshack.us/img373/1310/screenshotrr2.th.png[/IMG]](http://img373.imageshack.us/my.php?image=screenshotrr2.png)

Many thanks
Matthew

---

### Post by MarkieB on 2008-08-21
no longer participating in ubuntuforums.org

---

### Post by cariboo on 2008-08-21
You didn't unmount the drive properly in windows, copy the suggest line in a terminal and it should repair your problem. If you don't want to do what it suggests, boot into windows and unmount your dirve properly, and everything will be ok. I would suggest that you do what it says in any error messages if it suggest a fix, as 99% of the time the error message tells you what is wrong.

Jim

---

### Post by mity on 2008-08-21
try

Sudo mount –t ntfs-3g/dev/sda1

or if you have a windows/mac machine handy. plug in the device in it and eject it properly.

---

