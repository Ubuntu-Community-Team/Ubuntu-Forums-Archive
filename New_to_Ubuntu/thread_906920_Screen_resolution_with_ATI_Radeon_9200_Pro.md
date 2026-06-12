---
title: "Screen resolution with ATI Radeon 9200 Pro"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by yhall on 2008-08-31
Hi Guys,

I'm a complete noob to linux and ubuntu so apologies in advance if this is a really simple problem.

I've just installed ubuntu onto my old xp box and have been scratching my head on how to get my screen resolution back to the maximum of 1280x1024 for my monitor (a Viewsonic VG900). The screen resolution preference only goes up to 1280x800 and I am currently using 1024x768. My graphics card is an ATI Radeon 9200 Pro.

My searches have found threads suggesting playing with sudo displayconfig-gtk but I've had no luck. I've also found threads suggesting editing the xorg.conf file but I wouldn't know where to start! I'd really appreciate any suggestions.

Thanks in advance!
yhall

---

### Post by nickgaydos on 2008-08-31
Try installing the ATI driver for linux
```
sudo apt-get install envyng-gtk
```

---

### Post by pi.boy.travis on 2008-08-31
Have you tried the "hidden" Screens and Graphics dialog?

It is hidden by default, so right click on your GNOME menu (the one that begins with Applications) and select edit menus.  It should be under other.

This one had me confused for weeks. . .

---

### Post by yhall on 2008-08-31
Thanks for the suggestions guys but still no luck.

I installed envyNG and when i click on install the ATI driver i get the following output:

EnvyNG - Version 1.1.1
Ubuntu Hardy 32bit
Your graphic card has been detected as a ATI Radeon 9250
Your graphic card is supported by the legacy Driver
EnvyNG ERROR: ATI's legacy driver does not support your operating system

Cool tip on the hidden menu (looks like there's a bunch of cool stuff in there that I would never have found!). But the screen and graphics menu turns out to be the same as what you get when you do sudo displayconfig-gtk.

---

### Post by pi.boy.travis on 2008-08-31
You wouldn't happen to be running 64 bit, would you?

---

### Post by yhall on 2008-09-01
I'm not that tech savvy and not sure how to tell. I'm running the standard ubuntu install so I'd say no?

---

### Post by Jason Weiss on 2008-10-06
Is there an answer to this I am having the same problem.

---

### Post by Ryadt on 2008-10-06
> **Jason Weiss said:**
> Is there an answer to this I am having the same problem.

Try ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by RjNeLLY on 2009-12-22
hey peeps!! iam having the same problem got the envyng installes but couldnt click on it! or it would not open up....have a ati radeon 9200...running ubuntu 9.10 karmic..please help...thanks...dying to run compiz on computer...thanks

---

