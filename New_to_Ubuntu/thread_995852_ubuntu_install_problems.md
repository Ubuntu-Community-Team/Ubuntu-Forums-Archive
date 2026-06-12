---
title: "ubuntu install problems"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by delzio on 2008-11-28
I had installed in my computer 3 hds .One of them with UBUNTU 8.10 and the other two windows XP and the other windows VISTA.
The question is when I install ubuntu , GRUB show me al the systems installed in menu.lst but when you call for the windows vista appears a message about grub and windows not start.Really it happened an interaction between the two platforms and I do not know how to fix it.Is there someone that can help me please? certainly I made something wrong in installation.

Thank you

Delzio

---

### Post by maybeway36 on 2008-11-28
It might help to post the contents of your /boot/grub/menu.lst here, as well as the output of
```
sudo fdisk -l
```

---

### Post by Michael.Godawski on 2008-11-28
In what order did you install the three systems? Which was the first, which the last?

Perhaps there is something mixed up with the grub.

---

