---
title: "Boot windows from Grub"
date: 2017-01-05
forum: New to Ubuntu
---

### Post by ru-progers on 2017-01-05
Hello, i have Windows 10 on my SSD disk and the windows loader is on SSD, also i have ubuntu 16.10 on my HDD disk with grub loader on hdd what can i do so grub loader can see the windows loader on ssd?
Its not comfortable to switch them by using bios, so i want to use grub for switch.

---

### Post by ajgreeny on 2017-01-05
See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 **Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system. 

Did you have the SSD disconnected when you installed Ubuntu to the HDD?
Normally grub would see any other OS when installing Ubuntu and add it to the grub menu, but if the Windows SDD was not available to the Ubuntu installer it would not be able to do so.

Try booting to Ubuntu and then running ```
sudo update-grub
``` then set the Ubuntu HDD as first boot device and you may find all is as you want it.

---

