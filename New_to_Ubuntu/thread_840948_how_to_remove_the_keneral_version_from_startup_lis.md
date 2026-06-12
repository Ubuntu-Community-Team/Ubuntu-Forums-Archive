---
title: "how to remove the keneral version from startup list"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by hangnguyen on 2008-06-25
hello

On startup list of ubuntu I have many keneral version from .10 to .19 , how I clean it ???

thanks for your time !

HN

---

### Post by hariprs on 2008-06-25
Just go synaptic package manager and uninstall the unwanted kernel versions. This will remove the those kernels from the driver as well as the GRUB list.

---

### Post by hangnguyen on 2008-06-25
thank you for your help, I found an other solution from this tip:

[http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/](http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/)

check it out .

BR

HN

---

### Post by tamoneya on 2008-06-25
go into terminal and type:```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
sudo nano /boot/grub/menu.lst
```Then go to the bottom of the file.  It should be self explanatory just delete or better yet comment out (place a "#" in front) the lines that correspond to the old kernels.

---

### Post by hariprs on 2008-06-25
> **hangnguyen said:**
> thank you for your help, I found an other solution from this tip:

[http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/](http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/)

check it out .

BR

HN

Hi,

This will not remove the old kernels from your drive. Uninstalling will free up more space in your HD.

---

