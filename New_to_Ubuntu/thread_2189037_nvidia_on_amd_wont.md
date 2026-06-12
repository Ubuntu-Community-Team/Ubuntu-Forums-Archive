---
title: "nvidia on amd wont"
date: 2013-11-20
forum: New to Ubuntu
---

### Post by luij82 on 2013-11-20
installed ubuntu on a 2005 windows desk top with amd 64 used 32 bit install, once installed would work temp screen would go black and purple flashing when you would move mouse, restarted held shift found where to put no mode set got i to work, downloaded additional drives and choose first one, restarted computer nvivia flash on screen 3 times goes to black screen can do nothing,

---

### Post by efflandt on 2013-11-20
Which Ubuntu version? And is it installed on its own partition, or was it installed using Wubi within Windows?

What video card and/or if you can boot in (rescue) mode or from CD/DVD or bootable USB with install iso, what shows for following typed in a terminal (starts with small L)```
lspci | grep VGA
```If you have an old nvidia video card (like 5200) it might not be supported by current nvidia driver, but apparently works with default nouveau driver (as long as you use **nomodeset** boot parameter). But even if you have a newer nvidia card, you might still need the **nomodeset** boot parameter so nvidia and nouveau drivers cooperate with each other.

If nomodset works with the nvidia driver you can add that to grub using gksu gedit /etc/default/grub and inserting it in this line like this```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```Save the file then in a terminal do: **sudo update-grub**

---

