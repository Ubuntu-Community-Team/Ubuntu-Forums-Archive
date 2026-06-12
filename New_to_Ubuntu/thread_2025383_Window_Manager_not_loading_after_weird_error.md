---
title: "Window Manager not loading after weird error"
date: 2012-07-14
forum: New to Ubuntu
---

### Post by welshboy on 2012-07-14
Hi folks,

I finally took the plunge to go completely Linux based, and so installed 12.04 x64 on my dev box.  It was working fine, when all of a sudden, I was in Thunderbird, and it just dropped out of the Window manager for some reason, and I couldn't grab the error message quickly enough.

Everytime I boot now, I get a terminal log in, which is fine.  I can still use various things, however for some reason it just won't boot back in to the GUI mode.  My grub settings are correct, and I've installed the correct graphic card drivers.  

I was wondering if I could prevail upon you fine folks for some help?

My machine specs are:

Intel Dual Core 2.8Ghz processor
8GB DDR2 RAM
ATI Radeon HD6450
500GB Sata Hard Disk
Onboard sound card, blu-ray DVD/RW drive (SATA)

When this thing crashed, I had Thunderbird open, the Ubuntu software centre, a terminal window, and I was installing some new Java IDE as advertised in the Software Centre. 

I've installed the ATI Catalyst drivers for my card, and until now, it's been working really well.  I just don't know what's caused this, or how I could fix it.  

Any help would be most appreciated.

Many thanks

Welshboy

---

### Post by MG&amp;TL on 2012-07-15
Okay, what happens when you try and start the GUI?

```
sudo service lightdm start
```

---

### Post by mapes12 on 2012-07-15
Others may have a simpler solution but if it were my system I'd totally re install it. I keep all my files on a separate partition and not in /home. That way I can reinstall from scratch and not worry about keeping data safe. Once I have all the packages and tweaks how I like it then create a custom installation DVD using Remastersys. Then, when and if it crashes again it's a 20 minute job to reinstall from the custom DVD with everything as it was before.

---

