---
title: "driver for laptop video"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by chaddiesel on 2008-07-21
I am having a problem with my laptop video. I have been running it on the standard driver that always comes up "vesa". I decided to find the correct driver for the intel 945 card that is in the laptop.

After I did this the graphics were working but the resolution was horrible(everything was too big). After getting one resolution that made the screen go black I rebooted. The computer always boots and tries to use the "correct" driver for the card but fails to do so. I get the "run in low graphics mode" window and I can tell it to run on the "vesa" driver through there but it is very time consuming.

How can I get this thing to work like it used to? I don't care about using a better driver for the graphics card. The old standard driver was working fine.:confused:

---

### Post by sdennie on 2008-07-21
You could try rebooting the machine into recovery mode (the option from the grub menu).  When the menu comes up, choose xfix.

---

### Post by Bachstelze on 2008-07-21
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

will revert your X configuration to how it was originally. I believe the correct driver for you chipset is "intel" (at least it is for my 915).

---

