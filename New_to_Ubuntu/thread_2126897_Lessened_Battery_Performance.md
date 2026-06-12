---
title: "Lessened Battery Performance"
date: 2013-03-18
forum: New to Ubuntu
---

### Post by iplunk on 2013-03-18
I've recently installed Ubuntu with a dual-boot configuration on my Dell Studio XPS laptop (the one with the abominable case design where having the screen up blocks heat ventilation).

I've noticed that, even with the wireless card disabled via hardware switch and the screen backlight on minimum, I get <50% battery life when running Ubuntu as opposed to Windows 7. Is there software I can use to tweak power setting, use less power for graphics card/cpu, etc?

The high power-usage and low ventilation is a bad combination, and I've recently only been able to boot Ubuntu (which I prefer) when I have an available power outlet

---

### Post by tgalati4 on 2013-03-18
If Intel processor then you can install *powertop* and follow its suggestions.  You can turn on *Dynamic Clock* for the graphics card to lower the GPU power usage.  Because the XPS are designed for power usage--I don't think you will find much savings.  They could have included an induction cook top--at least one feature that would work as designed.

Dell BIOS doesn't allow any tweaking, but you could research undervolting for an addition 3-5 watts power savings.  If you are dilligent, you can probably get to 80% on the Win7 battery life, but then you can't see the screen, and your machine will run like crap.

The battery on an XPS is really just to keep the time, and maybe RAM during sleep as you search for another power outlet.

---

