---
title: "need to delete versions"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by mookie_jones on 2008-08-24
i have 3 different installs of ubuntu.

I somehow messed up my grub so i ran fdisk/mbr and then reinstalled ubuntu. 

I now have 3 installs and want to delete 2 of them but dont know how to go about doing it.

can i get some advice?

---

### Post by Bucky Ball on 2008-08-24
Hey Mookie. This might help.

[http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/](http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/)

You can, of course, just delete the entries in menu.lst by hand so they don't appear at boot, but that still leaves them in the machine. The method outlined in the link is more thorough though. :)

* PS: good idea (if you follow this link method) to also go to Synaptics and do a search for: 

linux-headers-2

It is mentioned further down on that page. In both operations, make sure you are deleting the right kernels and headers else you'll break. If you follow the instructions though you'll be fine.

---

