---
title: "stuck in 800x600 at LiveCD"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by Dr Small on 2008-05-29
I just got my LiveCD of 8.04, and I can't seem to find out how to get it into 1024x768, or does in need to be installed first?

---

### Post by sajro on 2008-05-29
> **Dr Small said:**
> I just got my LiveCD of 8.04, and I can't seem to find out how to get it into 1024x768, or does in need to be installed first?

Have you tried installing the drivers for your graphics card (ATI, Nvidia, etc.) while on the LiveCD (it just installs to RAM, use it to test). If that works, then when you install, you can reinstall the drivers.

---

### Post by Dr Small on 2008-05-29
Hrm, well. I thought that is was under some "Restricted Drivers" or something several versions back, and it enabled me to get to a normal screen resolution, but that option wasn't in it this time.

I got a nVidia card, and worked perfect out of the box for Feisty. I don't see why it should have been a problem for a newer version, but uh hum...

Anyhow, how else do you install the nvidia driver for it?
I am so used to building xorg and installing drivers as I go...

Dr Small

---

### Post by neurostu on 2008-05-29
When you start the live CD there will be a F4 option, select this and try booting in "Safe Graphics Mode" or "Force VESA" or something like that, so its probably making its best guess which isn't working. VESA is a pretty standard driver that almost all (?) cards support. Booting into vesa should give you control over resolution.  The LiveCD can't contain all the drivers for all possible video cards. After you install ubuntu will try to find the best possible driver for your video card and install it.

---

### Post by Dr Small on 2008-05-29
Thanks. That's probably what I need to do. I'll test it out next time I try out the livecd. Just wanted to make sure it was possible to get a higher resolution on the disc.

Thanks for your help.

Dr Small

---

### Post by Joeb454 on 2008-05-29
You *might* be able to change xorg.conf and restart X. I've not tried it before though.

Do you have an ATI or Nvidia card?

---

### Post by Dr Small on 2008-05-29
nVidia.
And yeah, I'm pretty most sure you can do that, because I had to do it to even *get* to the desktop with Gusty... :|

---

### Post by neurostu on 2008-05-29
ya I would definately try booting into "Safe Graphics Mode"  I had the same issue when I was first trying to install Gutsy with my Nvidia 140m Quadro card.

---

### Post by Joeb454 on 2008-05-29
Hehe, it's one reason I'm glad I have very generic hardware :D

---

