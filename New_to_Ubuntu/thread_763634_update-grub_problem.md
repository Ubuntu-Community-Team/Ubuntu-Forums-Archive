---
title: "update-grub problem"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by poscomp on 2008-04-23
How do I change GRUB so I can change the boot sequence. I tried update-grub but it would not accept mu su password while I was in terminal mode.********

---

### Post by bluefrog on 2008-04-23
you need to edit /boot/grub/menu.lst.
no need to run update-grub

---

### Post by gandaran on 2008-04-23
another way is to install StartUP-Manager

---

### Post by RobHK on 2008-04-23
> **bluefrog said:**
> you need to edit /boot/grub/menu.lst.
no need to run update-grub

You need to be root (have admin privileges) to do that.

Copy the below into a terminal and hit enter. It will ask for your password. Enter password and you should be able to edit menu.lst.

gksudo gedit /boot/grub/menu.lst

---

### Post by qhaz on 2008-04-23
Hi poscomp.  Not sure I understand exactly what you mean . . . but if you wish to change for example the default image that grub will boot, then you need to do something like this.
sudo vi (or your text editor of choice) /boot/grub/menu.lst

. . . then find the line that says this

default     0

. . . change the 0 to whatever grub entry you wish to be the default.  Remember that zero is the first entry, so if you wish for the fourth entry listed to become the default boot image then change the "0" to "3" (without the quotes ;-))

. . . then run sudo update-grub

cheers

---

### Post by bluefrog on 2008-04-23
edit menu.lst

DO NOT RUN update-grub

---

