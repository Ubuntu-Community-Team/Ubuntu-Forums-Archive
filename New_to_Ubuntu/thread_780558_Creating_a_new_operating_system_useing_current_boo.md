---
title: "Creating a new operating system useing current bootloader"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by joyser on 2008-05-03
Hey,
I'm looking at the folder boot on my hard drive in windows, there are the generic files. I want to make my own operating system and thought this would be a good way to boot it. How can i make my test operating system visible in the boot menu when the computer starts up. 
thanks for help!

---

### Post by mlentink on 2008-05-03
Do you really want to make your own os? If so, it will have its own boot procedure, which you could integrate into grub. If you want to make your own distro, its boot files would be in its own /boot, which you would reference from grub.

---

