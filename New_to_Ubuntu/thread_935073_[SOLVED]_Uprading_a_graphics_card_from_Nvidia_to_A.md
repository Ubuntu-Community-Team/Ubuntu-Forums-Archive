---
title: "[SOLVED] Uprading a graphics card from Nvidia to ATI"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by Maupertus on 2008-10-01
Hi guys, 

maybe a strange question, but it's something I've never done before in Linux.

A friend of mine is giving me his 'old' ATI HD2600 PRO AGP graphics card. I've been using my crappy Geforce FX 5200 for years and it can handle most Compiz effects without a hitch and is instantly recognized by Ubuntu in the proprietary drivers section.

I wanted to ask how I have to replace the card in Ubuntu. What are the steps I have to follow. I know that for windows it's:

de-install Nvidia driver
shutdown pc
remove card
install new
reboot
install new driver

How do I do this in Hardy?

Thanks!

---

### Post by vantsochev on 2008-10-01
You can try this way

- remove Nvidia fglrx proprietary drivers (if you installed them)
- install the ATI proprietary drivers (only if you need them)
- reconfigure your graphical interface : type in a terminal

```
sudo dpkg-reconfigure xserver-xorg
```

- let the default choices, but choose the ATI driver when asked
- Shutdown
- Remove the old card and plug the new card
- Reboot

---

### Post by Orange_and_Green on 2008-10-01
Hello Maupertus,

I think it's basically the same procedure:

1) Disable the driver from restricted drivers;
2) [EDIT]This is a good idea too, I suppose :)
> **vantsochev said:**
> ```
sudo dpkg-reconfigure xserver-xorg
```
Thanks vantsochev :) Although, I think that if you don't do this, you will get a warning that the system is using low resolution (i.e. vesa driver) and then you will be able to switch to ati drivers anyway...
3) Shut down PC
4) Replace old card with new one
5) Turn on PC
6) Try the driver recommended in restricted drivers
7) If you are unhappy with that one, try following [this procedure]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI").
8 ) Alternatively (to step 7), you could install "envy" from Synaptic and have it find a driver for you.

Good luck and have fun with your new card:KS

---

### Post by Maupertus on 2008-10-06
Argh, it's really freaking me out, but everytime I try use the restricted drivers, and reboot there is a kernel-panic. In other words, the screen goes black and my Caps and Numlock leds start flashing. 

Would envy help?

I now have a HD2600pro AGP edition.

And YES! It did help, I was a little bit lost and did everything every FAQ told me to do, and then in the end, I installed and it worked wonderfully!
Wish I could do something to repay Alberto Milone.

---

