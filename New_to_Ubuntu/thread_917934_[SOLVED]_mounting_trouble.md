---
title: "[SOLVED] mounting trouble"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by seanjohn81 on 2008-09-12
Hey everyone.
    I am having some difficulty mounting a second hard drive. It seems like there are a million threads on here with problems mounting but I can't seem to find an answer to my problem. I know that the hdd I'm trying to mount is sdb1 and have formatted it to ext2, but when I mount it I just get a lost+found folder where it should be. I followed the information here to format. [http://www.ehow.com/how_1000631_hard-drive-linux.html]("http://www.ehow.com/how_1000631_hard-drive-linux.html")

---

### Post by wolfen69 on 2008-09-12
see [this]("http://ubuntuforums.org/showthread.php?t=917864") thread. of course, replace ext3 with ext2.

---

### Post by Elfy on 2008-09-12
Can you post the result of 
```
sudo fdisk -l
cat /etc/fstab/
sudo blkid
```

Edit - indeed, do follow the thread instead :)

---

### Post by wolfen69 on 2008-09-12
you will also have to replace gksudo and gedit with sudo and whatever text app is used in xubuntu.

---

### Post by Elfy on 2008-09-12
you can use ```
gksudo mousepad
``` instead of gksuod gedit

---

### Post by seanjohn81 on 2008-09-12
Thanks everyone wolfen69 solved this for me I just needed to reformat to ext3 instead of ext2. Thanks again.

---

