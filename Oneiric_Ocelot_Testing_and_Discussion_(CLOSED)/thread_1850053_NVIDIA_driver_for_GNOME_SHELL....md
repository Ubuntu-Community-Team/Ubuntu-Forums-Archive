---
title: "NVIDIA driver for GNOME SHELL..."
date: 2011-09-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by samialtas on 2011-09-25
Hey guys, when I install a proprietary NVIDIA driver, I can't log in to GNOME SHELL. Rather than GNOME SHELL, it logs in to Unity 2D. I only tried the drivers which are in the Ubuntu repos. **Do you know a driver version which works with GNOME SHELL in Ubuntu 11.10?**

---

### Post by sgage on 2011-09-25
> **samialtas said:**
> Hey guys, when I install a proprietary NVIDIA driver, I can't log in to GNOME SHELL. Rather than GNOME SHELL, it logs in to Unity 2D. I only tried the drivers which are in the Ubuntu repos. **Do you know a driver version which works with GNOME SHELL in Ubuntu 11.10?**

The current version, cleverly labeled "nvidia-current", works fine for me on a 32-bit system with an 8500 GT card. The version is 280.13. Something else seems to be going on. Can you log into Unity 3D? If not, you might have a problem with your drivers not being properly installed.

---

### Post by VinDSL on 2011-09-25
> **sgage said:**
> The current version, cleverly labeled "nvidia-current", works fine for me on a 32-bit system with an 8500 GT card. The version is 280.13. 

**Something else seems to be going on.**[...]
Agreed!

I'm currently running the setup, as described above - except with a 7600 GT card.

Last week, I was successfully running GS, using IgnoreABI on Xserver 1.11 and Nvidia 285.03 (Xorg-Edgers PPA)

Something else is going on...  ;)

---

### Post by samialtas on 2011-09-26
When I install nvidia-current, I can't log in to GNOME SHELL again. My graphics card is NVIDIA 9600M GS. Please help me guys.

---

### Post by VinDSL on 2011-09-26
Are you trying to run GS in Natty or the Oneiric dev release?

---

### Post by samialtas on 2011-09-26
> **VinDSL said:**
> Are you trying to run GS in Natty or the Oneiric dev release?

In 11.10 beta. BTW, my problem is solved. Disabling Compiz tearing fix **compiz --replace --loose-binding** helped me to log in to GNOME Shell again... :D

---

### Post by sgage on 2011-09-26
> **samialtas said:**
> In 11.10 beta. BTW, my problem is solved. Disabling Compiz tearing fix **compiz --replace --loose-binding** helped me to log in to GNOME Shell again... :D

I'm glad you got sorted out. I don't understand how compiz figures into it though - Gnome Shell doesn't use compiz.

---

### Post by effenberg0x0 on 2011-09-26
> **sgage said:**
> I'm glad you got sorted out. I don't understand how compiz figures into it though - Gnome Shell doesn't use compiz.

The current compiz in my setup (Oneiric 64-bit fully updated) is Compiz  0.9.5.94ub1 and it does not support the --loose-binding option. 

Wild guessing: I think it tries to run compiz --sm-disable or something just to make sure compiz is not the WM. It will then receive a warning message  "compiz (core) - Warn: Unknown option '--loose-binding'" since this command-line option is set and it does not exist anymore. Maybe it gets confused at this point.

Regards,
Effenberg

---

### Post by samialtas on 2011-09-28
> **effenberg0x0 said:**
> The current compiz in my setup (Oneiric 64-bit fully updated) is Compiz  0.9.5.94ub1 and it does not support the --loose-binding option. 

Wild guessing: I think it tries to run compiz --sm-disable or something just to make sure compiz is not the WM. It will then receive a warning message  "compiz (core) - Warn: Unknown option '--loose-binding'" since this command-line option is set and it does not exist anymore. Maybe it gets confused at this point.

Regards,
Effenberg

Thanks guys. I learnt that Gnome Shell uses Mutter rather than Compiz or Metacity. So the commands that work for Compiz make Mutter and Gnome Shell stop.

But now I have vsync and hsync problem which sucks...

---

