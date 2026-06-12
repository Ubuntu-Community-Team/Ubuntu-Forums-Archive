---
title: "can ubuntu studio be run inside of ubuntu 11.10?"
date: 2012-05-03
forum: New to Ubuntu
---

### Post by linux623 on 2012-05-03
i wanted to start using ubuntu studio, but i am not sure if i can run it along side ubuntu 11.10 or inside of it. also how do i get sound to be recorded from my microphone?

---

### Post by holycow131415 on 2012-05-03
If you want to do it inside ubuntu, install virtualbox from virtualbox.org.

Yes you can dualboot ubuntu studio too. Create a partition with gparted and run studio's livecd to install it on that partition.

---

### Post by linux623 on 2012-05-03
thank you but i am new to ubuntu (very new) so i would need the instructions on how to dual boot because i thank that's the best idea

---

### Post by holycow131415 on 2012-05-03
Use ubuntu software center to install gparted if you dont already have it. open gparted, shrink your current partition to the size you want studio's disk space to be. Apply the changes. You will need to download and burn the studio ISO to a CD/DVD. Pop the disk in your computer, and reboot to boot off the disk. When the install asks where to install ubuntu, chose the partition that you created. From there its a normal install.

---

### Post by zombifier25 on 2012-05-03
Actually, you can install Ubuntu Studio on top of Ubuntu 11.10 and all settings, packages, etc. will be preserved.
Type this into the terminal:
```
sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
```

EDIT: Wait, you're better off installing it side-by-side, since Ubuntu Studio may require some configs if installed on top of regular Ubuntu.

---

### Post by linux623 on 2012-05-03
ok how do i install it side by side?

---

### Post by Bucky Ball on 2012-05-03
> **holycow131415 said:**
> open gparted, shrink your current partition to the size you want studio's disk space to be. Apply the changes.

All resizing should be done from a LiveCD as the partitions need to be unmounted. 

You don't need to create a partition to install Studio to. You can create that when you install Studio or it will do it itself.

---

### Post by holycow131415 on 2012-05-03
You will need to download and burn the ubuntu studio ISO to a CD/DVD. Pop the  disk in your computer, and reboot to boot off the disk. When the install  asks where to install ubuntu studio, choose the side by side.  Youll be able to move a slider to decide how much room ubuntu studio will take from regular ubuntu. From there its a normal install.

---

### Post by mcduck on 2012-05-04
> **zombifier25 said:**
> Actually, you can install Ubuntu Studio on top of Ubuntu 11.10 and all settings, packages, etc. will be preserved.
Type this into the terminal:
```
sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
```

EDIT: Wait, you're better off installing it side-by-side, since Ubuntu Studio may require some configs if installed on top of regular Ubuntu.

+1 to this, Ubuntu Studio, just like all the other Ubuntu variants, is not a separate operating system, instead they are all one and the same Ubuntu, only with different things installed by default.

So if you want Studio, the best way is to simply install the ubuntustudio packages on whatever Ubuntu variant you are running at the moment. Just like the best way to get a different desktop environment, or server applications, isn't making a separate install of kubiuntu/xubuntu/lubuntu/ubuntu server, but simply installing the packages you want to have. :)

---

