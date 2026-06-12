---
title: "[SOLVED] Nvidia Splash screen"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by ham213 on 2008-05-14
I am still a noob at this, so please bear with me.

I have the Nvidia driver installed on my machine and it seems to work fine.

Just the other day I saw someone else's Ubuntu system boot, and There was the coolest Nvidia splash screen.

My question is how do I get the super-cool Nvidia splash screen to show up on my system?

Here are my specs:
AMD 64 X2 3800
2GB PC3200 Dual Channel RAM
Nvidia 7900GT Video Card
Dual boot (M$ Winblows XP and Ubuntu 8.04)

Any help would be greatly appreciated.

Thanks!

---

### Post by Nepherte on 2008-05-14
Remove the "NoLogo" option line in /etc/X11/xorg.conf

---

### Post by hufferd on 2008-05-14
> **Nepherte said:**
> Remove the "NoLogo" option line in /etc/X11/xorg.conf

Hmmm I'm going to have to check that out myself thanks for the info! :guitar:

---

### Post by dublued on 2008-05-14
cool... didn't know about the NoLogo line.   mine started coming up by itself after i installed 'nvidia-settings'

---

### Post by ham213 on 2008-05-14
Thanks a ton!

There the Nvidia logo is in all it's glory!

---

