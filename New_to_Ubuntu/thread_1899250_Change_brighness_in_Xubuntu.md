---
title: "Change brighness in Xubuntu?"
date: 2011-12-23
forum: New to Ubuntu
---

### Post by hamstermoon on 2011-12-23
I have a Fujitsu Amilo Li2727 which doesn't seem to want to alter the brightness using its keyboard function keys like it should. The screen is very dark. Any suggestions (and is there a brightness applet like in Ubuntu?)

---

### Post by Toz on 2011-12-23
I remember reading somewhere that the Amilo line have flaky acpi implementations. Do you have a backlight interface?
```
ls /sys/class/backlight
```
If not (no directories are listed), try booting with the following kernel parameters: **acpi_osi=Linux acpi_backlight=vendor** and separately **acpi_osi=Linux acpi_backlight=legacy**. You can temporarily test these parameters by following the instructions here: [https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot"). 

Does the use of these kernel parameters expose a backlight interface and do the function keys work now?

If not, try the following kernel parameter: **acpi=off** (its not a good idea to permanently turn off acpi, but it would be interesting to see if it works)

---

