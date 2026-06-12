---
title: "Newbie help setting screen resolution"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by fawzley on 2008-08-14
Just loaded ubuntu on dell 470 with NVIDIA  Quadro FX 360M the screen resolution is 640x480; unable to increase resolution to workable setting. and because screen is so large most controls are off screen and not accessable.

Do I need a driver? 32 or 64bit?

Please advise.

---

### Post by fahadsadah on 2008-08-14
A driver would be a good idea, but optional.
Open a terminal, and type.
```
sudo dpkg-reconfigure xserver-xorg
```

Follow the instructions, till you get to the screen res bit. Do that, then finish.

Reboot

---

### Post by Keith Hedger on 2008-08-14
also try getting a proprietary driver which should work better use System->Administration->Hardware Drivers

---

