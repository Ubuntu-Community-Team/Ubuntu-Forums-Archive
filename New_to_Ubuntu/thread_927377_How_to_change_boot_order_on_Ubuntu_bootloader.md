---
title: "How to change boot order on Ubuntu bootloader?"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by Metuas on 2008-09-22
I saved my father's PC by installing Ubuntu as a recovery partition, but now when it starts the bootloader, instead of defaulting to Windows XP, it defaults to Ubuntu.  I can still pick XP, but if it isn't chosen quickly enough, it will automatically choose.  Is there a simple way to change this?

---

### Post by TriSwords on 2008-09-22
Go into the terminal and type in sudo vi /boot/grub/menu.lst

Find the line that reads "default 0". Change the 0 to whatever option you want. The first option on the boot menu is 0, second is 1 and so on.

If your options are 

Ubuntu
XP
Vista 

on GRUB, then Ubuntu would be default 0, XP 1 and Vista 2.

Save it and when you restart it should change the default OS it picks.

---

### Post by kansasnoob on 2008-09-22
In Ubuntu just go to terminal and install startupmanager:

```
sudo apt-get install startupmanager
```

It'll then show up in System > Administration > Startup Manager:

[ATTACH]86140[/ATTACH]

See where it says, "Default Operating System"? You can click on the toggle and change it!

---

