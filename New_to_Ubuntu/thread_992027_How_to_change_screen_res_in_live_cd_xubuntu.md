---
title: "How to change screen res in live cd xubuntu?"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by bmann11 on 2008-11-24
I'm checking out xubuntu on a via live cd, but I can only access two screen resolution options, neither of which work for my computer.  Is there a way to have access to other screen resolutions while booting from live cd?  Thanks.

---

### Post by bodhi.zazen on 2008-11-24
What videocard do you have ?

It sounds as if what you will need to do is use the alternate CD and install Ubuntu -> then post install install the drivers.

Did you try the safe video mode ?

---

### Post by bmann11 on 2008-11-24
I don't know what safe video mode is, and I can't install onto the hard drive...for now.  I can only check things out using the live cd.  Thanks

---

### Post by bodhi.zazen on 2008-11-24
> **bmann11 said:**
> I don't know what safe video mode is, and I can't install onto the hard drive...for now.  I can only check things out using the live cd.  Thanks

When you first boot Ubuntu, at the boot screen, when you select your language, right after that is a menu, an option from the menu is the safe graphics mode, I believe you hit F4 (not 100 % on that).

---

### Post by overdrank on 2008-11-24
I believe you are correct bodhi.zazen as F6 will allow you to edit the kernel line. :)

---

### Post by bmann11 on 2008-11-24
No, I'm not in safe mode.  Any ideas from here.  Thanks

---

### Post by bmann11 on 2008-11-24
Update

I downloaded the recommended nividia driver, but when I open up the nvidida server settings i get a screen stating "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

However, I did run that as root, but nothing seems to have happened.  Also, I don't know how to restart the x server.

---

### Post by bodhi.zazen on 2008-11-24
I do not think you can use the nvidia driver without rebooting, which is why you can not use it with a live CD.

You can try re-starting X with Ctrl-Alt-Backspace

---

### Post by bmann11 on 2008-11-24
Yep, that seems to be the case.  I tried rebooting but the driver doesn't stay installed, so it looks like it can't be done. Thanks anyway.

---

