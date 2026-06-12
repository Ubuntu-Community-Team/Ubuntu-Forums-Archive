---
title: "[SOLVED] Intrepid Video Driver"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by Promaster91 on 2008-11-03
I am having some problems with Intrepid's video driver. It lags when scrolling and white bars appear on my screen during compiz effects. In Hardy, I had the ATI proprietary driver installed however in Intrepid no drivers come up under restricted drivers. How would I install ATI proprietary driver in Intrepid. I am using a ATI Radeon x1200 graphics card. Thanks.

---

### Post by crjackson on 2008-11-03
Hope someone chimes in with the magic bullet. I have the same issues on my laptop. I'm holding off on upgrading all of my ATI desktop systems until I get this resolved.

---

### Post by Promaster91 on 2008-11-10
I found a way to get back the ATI proprietary driver. First  
```

sudo apt-get install xorg-driver-fglrx

```
Then reboot. Then goto System>Admin>Hardware Drives. The proprietary driver should show up. Just install and reboot and there you go.

---

