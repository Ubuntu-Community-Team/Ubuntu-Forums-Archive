---
title: "I need help!"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by jeff Odom on 2008-09-25
I downloaded the desktop version, and it said it came with grub, but it took over my computer. It ate my microsoft windows. No big deal, but some of the websites I goto have to have media player, because of the streaming, or at least they only give that or Apple the as the only choices. Can ya' help?

---

### Post by Crafty Kisses on 2008-09-25
First off install this package:
```
sudo apt-get install ubuntu-restricted-extras
```
You can add Windows back to the GRUB list by doing the following:
```

title Microsoft Windows
root (hd0,1)
savedefault
makeactive
chainloader +1
```

---

### Post by tuxxy on 2008-09-25
If you didnt remove XP you most likely just need to add it back to your GRUB loader so it can boot.

Another method would be to install the XP to a virtual drive in Ubuntu, also the advantage here would be you that you could run XP from within Ubuntu without needing to power down the machine to switch between the two.

I would recommend [VirtualBox 2.0]("http://www.virtualbox.org/wiki/Downloads") the PUEL version, [heres a guide]("https://wiki.ubuntu.com/VirtualBox") to setting up a virtual drive

---

### Post by jeff Odom on 2008-09-25
> **Codename said:**
> First off install this package:
```
sudo apt-get install ubuntu-restricted-extras
```
You can add Windows back to the GRUB list by doing the following:
```

title Microsoft Windows
root (hd0,1)
savedefault
makeactive
chainloader +1
```
thanks guys. I will see if it works.

---

### Post by caljohnsmith on 2008-09-25
It would help if you can post the output of:
```
sudo fdisk -lu
```
Then we will know for sure if your Windows partition got overwritten, or if it still exists. If it is still there, we can help you add it as an option in your Grub menu on start up.

EDIT: I saw your other thread, Jeff, so to run the above command, just go to Applications > Accessories > Terminal (the menu in the upper-left corner of your desktop), and then you can run the command.

---

