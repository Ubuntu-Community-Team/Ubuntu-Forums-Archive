---
title: "usb hard drive troubles"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-07-25
i bought a usb hard drive called my passport,when i open it up it asks me to auto run then says permission denied??is there a fix for this or can i
format it for linux,also besides storage can you put an operating system 
on it?? as you can see i switched back to ubuntu i didnt like kubuntu!!
rick

---

### Post by PmDematagoda on 2008-07-25
Did you try opening the drive manually through nautilus without the autorun prompt? About installing an OS on it, yes, that can be done provided there is enough space(which as a hard drive, it normally does:)).

---

### Post by Potatoj316 on 2008-07-25
You can put an OS on it if you want.  How do you try to mount it, manually or automatically?

---

### Post by phidia on 2008-07-25
Open a terminal and enter this "sudo fdisk -l" If there are no partitions on that external drive that's probably why you're getting that message. 
Yes you can format it for linux and you could also install an OS on it too.
See the contents box from [this page]("https://help.ubuntu.com/community/Installation").

---

