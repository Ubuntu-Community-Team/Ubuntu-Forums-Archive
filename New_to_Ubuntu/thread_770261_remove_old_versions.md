---
title: "remove old versions?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by thepocketdrummer on 2008-04-27
So, I upgraded to 8.04 just now, and there are still entries for 7.10. How do I get rid of it and make my system squeaky clean?

Oh, and how do I get my G9 mouse buttons to work?

---

### Post by artir on 2008-04-27
[http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/](http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/)

---

### Post by TeoBigusGeekus on 2008-04-27
Where are these entries? Do you mean in the grub menu, the software sources or something else?

---

### Post by southernman on 2008-04-27
> **thepocketdrummer said:**
> So, I upgraded to 8.04 just now, and there are still entries for 7.10. How do I get rid of it and make my system squeaky clean?


Exactly how did you do the upgrade? commando style, or gui?

One would think doing a dist-upgrade or by gui either one, would remove all Gutsy components and install Hardy. Never done them, always clean installs for muah.

For your button issues, try Googling "how to make g9 buttoms work ubuntu"

---

### Post by sailor2001 on 2008-04-27
> **thepocketdrummer said:**
> So, I upgraded to 8.04 just now, and there are still entries for 7.10. How do I get rid of it and make my system squeaky clean?

Oh, and how do I get my G9 mouse buttons to work?

If you are referring to your old kernels:  sudo aptitude purge linux-image -2-6-24-14 generic  (if that is the old kernel you want to get rid of ) It is suggested you keep the last kernel for back-up purposes

---

### Post by mister_pink on 2008-04-27
You can make grub hide the extra ones if you want, rather than removing them. Edit the menu file:
```
gksudo gedit /boot/grub/menu.lst
```
Then search the file for "howmany". I can't remember what it is as a default, probably
#howmany=all
and change it to
#howmany=2
or however many ones you want (minimum 1 obviously, otherwise it won't show the current one!)

Then save and exit and run:
```
sudo update-grub
```

---

