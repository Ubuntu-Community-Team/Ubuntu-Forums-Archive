---
title: "How to edit boot manager."
date: 2016-03-03
forum: New to Ubuntu
---

### Post by czarek2 on 2016-03-03
Hello.
I Installed Ubuntu on the second partition next to Widnows.
Boot manager place Ubunktu as first and Windows as last one.
How to edit it to place Windows as first default position??

Regards
Czarek

---

### Post by mastablasta on 2016-03-03
you can do it manually by editing config files or you can use a graphics interface such as grub customizer: [https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

---

### Post by fantab on 2016-03-03
Do you want the Windows menu entry in Grub to be first? OR
Do you want Windows to boot first by default?

If you are after first... then you probably need to create a custom file, usually */etc/grub.d/40_custom*. [More Info]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Making_the_custom_Grub2_Menu_entries").

If you want grub to boot Windows first by default then you'll need to edit */etc/default/grub* file.
To edit the file:
```
Alt+F4 -> gksu gedit /etc/default/grub
```
**GRUB_DEFAULT=0** is the default entry where '0' = 1st entry in the existing menu. If you want, say, fourth entry in the menu to boot first then replace '0' with '3'. The Grub menu numbering starts from '0'.

After any change to either of the files run:
```
sudo update-grub
```

Grub Customizer is not really needed.

---

