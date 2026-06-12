---
title: "dual boot"
date: 2014-04-22
forum: New to Ubuntu
---

### Post by windowsfree on 2014-04-22
how do i edit the menu to choose an OS on a dual boot computer.  I am running Windows OS and Xubuntu.

thank you.

---

### Post by oldfred on 2014-04-22
Many may suggest grub customizer, but I prefer to manually do it.

You can use the number it is in the menu, but better to use description. But description must be exact.

       find your windows entry in grub.cfg and copy to grub default like this Vista entry - If you edit your windows command use the edited copy as this must match the title exactly:

gedit /boot/grub/grub.cfg
and copy & paste Windows title into grub_default  here:

gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new :
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Save & Then do:
sudo update-grub

---

