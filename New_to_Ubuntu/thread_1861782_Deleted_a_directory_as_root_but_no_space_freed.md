---
title: "Deleted a directory as root but no space freed?"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by decomp on 2011-10-16
Hello all!

I opened my file manager as root with gksudo and deleted a users home folder from my other partition (which runs ubuntu 10.10.) The space has not been freed. I have tried running a disc check. What do I do? it's about 7GB!

---

### Post by Little Blue on 2011-10-16
You did this in a file manager, e.g., nautilus right? Have you checked your wastebasket? I always thought gui's like that default to moving things to the wastebasket when possible....

---

### Post by sadaruwan12 on 2011-10-16
Yes, did you do a Shift+delete or just a delete if you did a Shift + delete then that'll move your data straight out of the HDD.

But if you just did a delete that'll take your deleted data right in to the trash bin.

Check the bin if it's there or not.

---

### Post by decomp on 2011-10-16
I deleted the file using pcmanfm, which does not support using trash as root user. Also the files were on another partition so it was not possible to use trash. But I have also made sure to empty the trash on both partitions. What do I do now?

---

### Post by Vaphell on 2011-10-16
edit: too late

---

### Post by sadaruwan12 on 2011-10-16
OK, How do you know it's not have been removed from you hard drive does you get a message or any type of a indication?

---

### Post by decomp on 2011-10-16
Because if I browse to that partition in a file manager it still shows the same used/free space as before deleting the files.

---

### Post by drs305 on 2011-10-16
Some disk monitors require refreshing after an operation...

Perhaps some of the tips in this guide will help you locate the (deleted) files or help determine why the space isn't freed up:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

