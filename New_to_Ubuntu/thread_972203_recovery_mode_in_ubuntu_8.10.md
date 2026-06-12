---
title: "recovery mode in ubuntu 8.10"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by Matt26 on 2008-11-05
how do i get access to the recovery mode in ubuntu 8.10?  if i remember correctly you had to hit the F11 key during startup to access it back in 8.04, but that doesn't seem to work for 8.10.

any help is appreciated.

thanks.

---

### Post by WelshChris on 2008-11-05
Hmm.  Can't you boot into recovery mode by appending 's' to the kernel arguments in Grub?

At the grub menu, press 'a' to append, then 's'. 

Can't check this at the moment, though. I'm sure someone will correct me!

---

### Post by bodhi.zazen on 2008-11-05
Recovery mode is an option on the grub boot menu. If you have a "hidden menu" hit Esc

---

### Post by Matt26 on 2008-11-05
i might be wording the question incorrectly- i'm trying to get to the menu that can be accessed just before ubuntu begins to load (i believe just after the GRUB boot loader shows up after POST and does its count down before the OS loads) and it gives the option to fix the X server and some other options (can't remember what they are at the moment) and i'm pretty sure back in 8.04 you could access this menu by hitting F11.  hope this makes more sense.

---

### Post by DGortze380 on 2008-11-05
> **Matt26 said:**
> i might be wording the question incorrectly- i'm trying to get to the menu that can be accessed just before ubuntu begins to load (i believe just after the GRUB boot loader shows up after POST and does its count down before the OS loads) and it gives the option to fix the X server and some other options (can't remember what they are at the moment) and i'm pretty sure back in 8.04 you could access this menu by hitting F11.  hope this makes more sense.

grub will either show up when booting, or it will say something like 'Press ESC to enter menu' and count down from 3. Press ESC.

---

