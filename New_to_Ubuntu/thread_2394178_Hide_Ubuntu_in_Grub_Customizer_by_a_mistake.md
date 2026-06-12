---
title: "Hide Ubuntu in Grub Customizer by a mistake"
date: 2018-06-13
forum: New to Ubuntu
---

### Post by evanthinh on 2018-06-13
[COLOR=#000000]Hello everyone![/COLOR]
[COLOR=#000000]I tried to install Ubuntu along with Windows 10 on my laptop. Then I tried to move Windows to the top in the Grub Customizer, but I I unchecked most of the list except the one i was moving, Windows 10.[/COLOR]
[COLOR=#000000]So when I restart it only shows Windows 10 in the list. So Is there anyway to log back to Ubuntu just by Grub Command Line please? Thank you very much and sorry for my bad english![/COLOR]

---

### Post by adelpozoman-f on 2018-06-13
you are gonna need a live usb (the same you used for installing ubuntu), then install grub customizer and customize it again. Remember, dont install ubuntu, just grub customizer

---

### Post by Dennis N on 2018-06-13
Maybe it can be fixed just from live media, on the premise that the customizer made some permission changes to some grub files in Ubuntu.

Boot into Ubuntu 18.04 live media.
Open File Manager.
From Side Pane, open "Other Locations".
Find the listing for the Ubuntu OS you installed on the internal drive, and open it in Files. Find the **etc** folder in the window and open it. Find **grub.d** folder in the window, right-click on the folder and open in terminal. 
In the terminal, run command: 
```
ls -l
``` 
and post the output in code tags.

---

### Post by leunam12 on 2018-06-14
boot live media, chroot into your installation and run sudo update-grub. The instructions below should work.

[http://grainier.net/how-to-reinstall-update-grub-2-with-a-ubuntu-live-cd/](http://grainier.net/how-to-reinstall-update-grub-2-with-a-ubuntu-live-cd/)

---

