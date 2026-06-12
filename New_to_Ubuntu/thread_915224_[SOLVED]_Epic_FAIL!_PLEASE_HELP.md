---
title: "[SOLVED] Epic FAIL! PLEASE HELP"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-09-09
I was trying to optimize my Ubuntu installation by editing my fstab file. I changed the options for mounting my ext3 ( encrypted root ) drive. The options were relatime,errors=remount-ro, and I changed it to data=writeback,relatime,errors=remount-ro. It now wont boot and I can't change to file back. I made a back up of it, but when it boots it only boot in read only mode. I have tried to change it back by booting up in recovery mode, and several live cds. When I boot up in the live cds it wont allow me to mount the drives. What can I do?

---

### Post by hyper_ch on 2008-09-09
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

### Post by wolfen69 on 2008-09-09
put in the live cd and do ```
sudo su
``` then```
nautilus
```then open the drive where ubuntu is installed, and go to where the backup is and just replace it.

---

### Post by slughappy1 on 2008-09-09
Wolden69, that doesn't work. It only recognizes the boot partition. My other partitions are encrypted.

---

### Post by slughappy1 on 2008-09-09
Success, I stumbled upon [this]("http://ubuntuforums.org/showthread.php?p=5448385") post. The [sixth]("http://ubuntuforums.org/showpost.php?p=5448385&postcount=6") post told me how to do it.

---

