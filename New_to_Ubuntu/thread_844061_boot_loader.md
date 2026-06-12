---
title: "boot loader"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by cods678 on 2008-06-29
hi everyone i2am running vista and ubuntu 8.04 on my laptop ...the problem i"ve got is everytime ubuntu upgrades i get another unbuntu on my boot loader theres about 5 unbuntu options on boot loader .....is there a way i can delete old ones and stop them building up again many thanks Neil ](*,)

---

### Post by bumanie on 2008-06-29
As long as the you are sure the new ones work, you can delete the old ones, however, it is a good idea to keep one or two old kernels around in case a future kernel causes problems. To remove, go into synaptic and type kernel into the search function. Then scroll down until you find linux headers and remove the kernels you no longer want. You can also go into /boot grub/menu.lst and comment out the entries to kernels that you longer want in the list by putting # before the entries pertaining to the particular kernels. This doesn't remove them, but will stop them being shown at the grub menu stage. Many people prefer this option as it is not altering the OS in any way. To get the menu to edit with # > gksudo gedit /boot/grub/menu.lst and you can edit the kernels you don't want appearing in the list. Whichever method you use is up to you. If you are new to linux, I would suggest commenting out entries, rather than removing them.

---

