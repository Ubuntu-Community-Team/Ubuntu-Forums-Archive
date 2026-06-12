---
title: "Dual boot with Vista question"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by phil81uk on 2008-06-10
Hello,

I wish to give Linux another go and am planning a dual boot system, where I can carry on using Vista until I have everything working on Linux.

Last time I installed Fedora onto my laptop along with Windows then Fedora took over the startup screen and gave me the choice of booting into Windows or Fedora. If I didn't select then it defaulted into Windows.

Ideally, I would want the bootup to remain with Vista as that will be my primary system. And I certainly wouldn't want it to default to Ubuntu if I don't press any key.

Can anyone advise me on this?

Regards
Philip

---

### Post by dracayr on 2008-06-10
Just install Ubuntu as normal, than it will use GRUB. GRUB will show a menu at startup where you can choose between windows and ubuntu (just like Fedora did). You can change that menu, so that windows is at the first place (and boots if you don't press any key) by editing /boot/grub/menu.lst

dracayr

---

### Post by jon8105 on 2008-06-10
> **dracayr said:**
> Just install Ubuntu as normal, than it will use GRUB. GRUB will show a menu at startup where you can choose between windows and ubuntu (just like Fedora did). You can change that menu, so that windows is at the first place (and boots if you don't press any key) by editing /boot/grub/menu.lst

dracayr

That is exactly what I did and when I boot up I have the choice of either Ubuntu or Windows XP.  As long as Vista is already installed, it is very easy to install Ubuntu and have a menu at start-up to let you choose which OS you want.

---

### Post by Duck2006 on 2008-06-10
> **phil81uk said:**
> Hello,

I wish to give Linux another go and am planning a dual boot system, where I can carry on using Vista until I have everything working on Linux.

Last time I installed Fedora onto my laptop along with Windows then Fedora took over the startup screen and gave me the choice of booting into Windows or Fedora. If I didn't select then it defaulted into Windows.

Ideally, I would want the bootup to remain with Vista as that will be my primary system. And I certainly wouldn't want it to default to Ubuntu if I don't press any key.

Can anyone advise me on this?

Regards
Philip

Some info on grub.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by meierfra. on 2008-06-10
If you want to keep using the Vista boot loader: Use [EasyBCD]("http://neosmart.net/wiki/display/EBCD/Ubuntu")

---

