---
title: "Showing only text at startup"
date: 2018-11-26
forum: New to Ubuntu
---

### Post by automate-stuff on 2018-11-26
I want to only see text at startup so I have : 


GRUB_CMDLINE_LINUX_DEFAULT="text" 


in /etc/default/grub  ...


My problem is that at startup, screen resolution changes..it is larger text at first but then the text becomes smaller(text with green OKs in the beginning) which I think is due to change in resolution....is there a way to fix this ? I don't want this resolution change....I want it to be in a single resolution..

---

### Post by NM5TF on 2018-11-26
you can use xrandr to set the resolution

you might find some useful info here [https://unix.stackexchange.com/questions/227876/how-to-set-custom-resolution-using-xrandr-when-the-resolution-is-not-available-ihttp://]("https://unix.stackexchange.com/questions/227876/how-to-set-custom-resolution-using-xrandr-when-the-resolution-is-not-available-ihttp://")

tommy

---

### Post by CatKiller on 2018-11-27
You can use the nomodeset kernel parameter to stop the screen mode being set.

---

### Post by mastablasta on 2018-11-27
> **automate-stuff said:**
> I want to only see text at startup ... 



why? 

you can see it later if you want in dmesg.

---

### Post by automate-stuff on 2018-11-27
> **CatKiller said:**
> You can use the nomodeset kernel parameter to stop the screen mode being set.


that did the trick.

---

