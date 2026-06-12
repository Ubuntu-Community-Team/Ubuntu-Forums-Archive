---
title: "Grub-Customizer for bootmenu on Multipartioned USB-Stick"
date: 2013-08-31
forum: New to Ubuntu
---

### Post by mladyluck on 2013-08-31
Hello,

i try to make my Grub bootmenu with Grub-Custoizer, but fist of all if i switch to the bootpartion of my Stick i see many red signs at the left side, and if i choose "Use" i got an error like this:

chroot '/media/grub-customizer_recovery_root_mountpoint' grub-mkconfig konnte nicht erfolgreich ausgeführt werden. Fehlermeldung :  chroot: failed to run command `grub-mkconfig': No such file or directory

so i don't understand why, because the 'grub-mkconfig' is located in /usr/sbin and this directory is in path.

hope you can help me soon

BTW: Ubuntu 12:10 running

Did I have to copy files to my bootpartion? Did i ihave to run something before callig 'grub-custimizer'? What is my fault?

---

### Post by mladyluck on 2013-09-01
Problem solved: Some BIOS put USB-Sicks in the Boot-Menu-Cathegorie HARDDISK

So I have to say after feeled a million trys all is fine and works well! Thank you for this great Program

---

### Post by Jonathan Precise on 2013-09-01
My bad!!! Didn't see the tag [SOLVED].

Mark this as solved by going to thread tools.

---

