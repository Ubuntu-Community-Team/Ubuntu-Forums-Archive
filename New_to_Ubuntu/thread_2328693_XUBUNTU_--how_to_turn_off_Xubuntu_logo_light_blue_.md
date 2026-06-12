---
title: "XUBUNTU --how to turn off Xubuntu logo light blue screen during boot ?"
date: 2016-06-23
forum: New to Ubuntu
---

### Post by jim102 on 2016-06-23
Xubuntu takes 2 minutes to get from grub to desktop screen, with automatic login
it spends 1.5 minutes showing Xubuntu logo and light blue screen with something  like a white circle rotating
Is there any way to turn this off this useless feature and actually see on a screen what is happening ?
thanks

---

### Post by slickymaster on 2016-06-23
Hi jim102, welcome to the forums.

See if this is what you want: [http://askubuntu.com/questions/33416/how-do-i-disable-the-boot-splash-screen-and-only-show-kernel-and-boot-text-inst](http://askubuntu.com/questions/33416/how-do-i-disable-the-boot-splash-screen-and-only-show-kernel-and-boot-text-inst)

---

### Post by jim102 on 2016-06-23
thank you for your reply
yes, I would prefer to see black/white messages during boot, instead of the meaningless black screen at first which changes to a blue screen with logo and a white rotating thingy
blue screen with rotating thingy ---it reminds me what Windoz does
tried already using "synaptic" to remove  "plymouth" and related, but it is so inter-tangled with other things, that it wants to remove "xfce" + more
do not really want to play with grub, if its gets broken due to wrong config/setting-----system will not boot anymore !
I find XUbuntu's 2 min boot also way too slow, on a same computer Debian Jessie boots about 30 sec from grub to desktop screen

---

### Post by The Cog on 2016-06-25
I prefer to see what's happening too. 
The way I do it is to edit /etc/default.grub:
```
sudo nano /etc/default/grub
```
comment out the line about quiet, splash and add another line beneath that doesn't default to quite splash (so afterwards it looks like this):
```
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT=""
```
and then update the grub install with the new settings:
```
sudo update-grub
```


EDIT
As an afterthought, that's what slickymaster linked. I don't touch plymouth though.

---

### Post by jim102 on 2016-06-25
thanks for all the info
Meanwhile I learned that XUBUNTU is not really for me
Going to stay with pure Debian based distros, like Kali, Sparky, Point, Solydx, Siduction, Star

---

### Post by kurt18947 on 2016-06-26
> **jim102 said:**
> thanks for all the info
Meanwhile I learned that XUBUNTU is not really for me
Going to stay with pure Debian based distros, like Kali, Sparky, Point, Solydx, Siduction, Star

'nuther distro to consider - MX15. I don't care for the default desktop, especially how the panel is set on on the left. It's easy enough to change and it seems quite light and doesn't require many of post-install tweaks (except for the initial desktop)

---

### Post by jim102 on 2016-06-26
yes, I forgot to mention mx15 and antiX
thanks

---

