---
title: "shut down but no pwer down?"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by too_funky on 2008-11-19
i have an old pc which i dual boot with windows 98se and ubuntu hardy heron. when i shutdown in windows 98, it goes through the shutdown procedure and turns off the computer. However when i shutdown in ubuntu, the ubuntu shut down screen comes up, it shutsdown, but then it just cimes to a blank screen and the computer does not power down as with windows 98. I have recently changed the linux os to xubuntu to try and speed things up, but i still have the same problem. IS this an x/ubuntu bug? can i fix it.

Thanks in advance

---

### Post by philinux on 2008-11-19
It's the bios.
This thread solves it though.
[http://ubuntuforums.org/showthread.php?t=981610](http://ubuntuforums.org/showthread.php?t=981610)

---

### Post by too_funky on 2008-11-19
that thread seesm to be ubuntu specific, the command line

gksudo gedit /boot/grub/menu.lst

doesnt seem to do anything

EDIT: changed gedit to mousepad, works fine now

---

### Post by philinux on 2008-11-19
you need 

kdesu kate or gksudo mousepad

instead of gksudo gedit

---

