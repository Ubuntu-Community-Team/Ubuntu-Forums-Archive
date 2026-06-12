---
title: "[SOLVED] onboard AC97 sound stopped working"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by MattThLinuxNewb on 2008-10-15
Just today my onboard sound just stopped working for some reason. The sound manager gives me this error:

> The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

cat /proc/asound/cards returns this:
```
cat /proc/asound/cards
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 10
```

I haven't recently updated to a new kernel, or installed any new upgrades.

I've tried booting from both the Gutsy and Hardy Live-CDs and still get the same error.

I have a ASUS A8N-E motherboard which has given me nothing but problems, so I've a feeling it's a hardware problem. (e.g. it freezes frequently on boot, both before and after loading the kernel. Also, the onboard LAN recently stopped working then strangely fixed itself not long after...)

Help from someone with audio expertise would be great, I'd like to be sure it's a hardware problem before going out and buying a PCI sound card.

Regards,

Matt

---

### Post by MattThLinuxNewb on 2008-10-15
Ok it has started working again after shutting down the pc overnight, just like the onboard LAN did. Definitely a problem with my ASUS motherboard, sigh...

---

