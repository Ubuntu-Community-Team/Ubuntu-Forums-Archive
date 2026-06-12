---
title: "How to get a menu to choose which OS to boot from"
date: 2013-12-14
forum: New to Ubuntu
---

### Post by Remember2Wipe on 2013-12-14
Installed Ubuntu 13.1 alongside Win7 Ultimate x64 and it boots to only one OS. I ran boot-repair ad set it to keep the menu open for 10 seconds. However, in the Grub menu only Ubuntu is listed, not Windows. 

Anyway to fix this?

---

### Post by thatredbird on 2013-12-14
Have you tried the basic

sudo update-grub

---

### Post by Remember2Wipe on 2013-12-14
Thanks. God that was relieving. Really didn't want another 30+ reply count thread.

---

### Post by Gone fishing on 2013-12-14
If you open a terminal and run ```
 sudo update-grub
``` Your Windows install should be found and added to grub and here's a link to how to install Grub Customizer [http://ubuntuhandbook.org/index.php/2013/08/install-grub-customizer-ubuntu-13-10/](http://ubuntuhandbook.org/index.php/2013/08/install-grub-customizer-ubuntu-13-10/)

---

### Post by mikelavekkia on 2013-12-14
try update-grub2 or if you use kde install kde-config-grub go in system settin > startup > grub an you search for "probe for OS" (or somthing similar) and check this...an reboot

---

