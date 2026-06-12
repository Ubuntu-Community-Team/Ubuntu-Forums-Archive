---
title: "Ubuntu bootup"
date: 2012-06-24
forum: New to Ubuntu
---

### Post by Arendyl on 2012-06-24
Just installed ubuntu 12.04, installation was successful. When I go to boot up my computer again, it does not give me the option to select ubuntu and boots windows like it did before. Can anyone explain to me how to create the grub prompt where i get to choose the ubuntu partition instead? thanks

---

### Post by nipunshakya on 2012-06-24
Boot into your LiveCd mode, from there, install the boot-repair tool and run it... select 'try recommended ' button and restart... that might help.. the following link is worth reading before running the tool...
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Shadius on 2012-06-24
Seems like GRUB didn't install or installed incorrectly. You can use Boot-Repair to reinstall GRUB or post the output of:
```
sudo fdisk -l
```
and we'll continue from there.

---

### Post by Fernhill Linux Project on 2012-06-24
Did you use a USB to install Ubuntu? If so try booting the system with the USB connected and see if it boots.

If it boots and you see the GRUB menu, then grub has been installed to the USB. From your booted Ubuntu system, open a terminal, then use the following commands to install grub to the internal drive :

```
sudo grub-install /dev/sdX
sudo update-grub
```

Replacing ```
sdX
``` with the actual drive, which will probably be ```
sda
```, but use disk utility to double check if you are unsure.

---

### Post by NikoC on 2012-06-24
Grub2 boot menu is hidden: holding shift when booting should present you the familiar grub options.

[More info here]("http://ubuntuforums.org/showthread.php?t=1195275").

---

