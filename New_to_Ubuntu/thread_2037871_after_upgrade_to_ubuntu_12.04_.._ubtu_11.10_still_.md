---
title: "after upgrade to ubuntu 12.04 .. ubtu 11.10 still on the boot menu"
date: 2012-08-05
forum: New to Ubuntu
---

### Post by redsprite on 2012-08-05
hey averyone,

 I recently upgraded to Ubuntu 12.04  but on the boot menu i have ubuntu 11.10  linux version 3.0.0.0-12 

i would like to boot on ubuntu 12.4 :linux version 3.2.0-25  like what i have installed as upgrade and update

Any help is much appreciated!

---

### Post by cortman on 2012-08-05
> **redsprite said:**
> hey averyone,

 I recently upgraded to Ubuntu 12.04  but on the boot menu i have ubuntu 11.10  linux version 3.0.0.0-12 

i would like to boot on ubuntu 12.4 :linux version 3.2.0-25  like what i have installed as upgrade and update

Any help is much appreciated!

Hm, run

```
sudo apt-get upgrade && sudo apt-get dist-upgrade
```

Then reboot, to make sure the upgrade didn't miss any packages.

---

### Post by redsprite on 2012-08-05
hello ,
i did it but no change ,ubuntu 11.10 still  on the menu

lol@illusion:~$ sudo apt-get upgrade
[sudo] password for lol: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
lol@illusion:~$ apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by 3177 on 2012-08-05
you need to update GRUB. After which both kernels will show up on the menu.

---

### Post by cortman on 2012-08-05
Try

```
sudo update-grub
```

And reboot... (this feels like Windows) :P

---

### Post by asmolinski on 2012-08-05
Try [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by redsprite on 2012-08-05
cortman  + asmolinski + 3177
 thank u all 
 it was about grub updating

---

