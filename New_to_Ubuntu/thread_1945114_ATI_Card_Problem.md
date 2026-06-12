---
title: "ATI Card Problem"
date: 2012-03-22
forum: New to Ubuntu
---

### Post by JonasDeMoor on 2012-03-22
Hi,

I'm new to Ubuntu(I come from Windows 7) and I installed Ubuntu 11.10 a few days ago. In the past, I already had problems with my video card, so I thought that maybe the problem has been solved now. 

When I use the open-source drivers for my ATI card, it all runs very smooth, but my laptop (Acer Aspire 8920G) 's fan is spinning fast and the laptop becomes hot. So I installed the official ATI drivers from the "Additional Divers" menu. I rebooted and now the laptop is very quiet but when dragging windows, scrolling and typing, it all lags

If anyone know a fix for this please let me know. 
(I'm totally new to Linux and  Ubuntu so no very difficult methods please)

[B][I]System Specs
***********
Acer Aspire 8920G
- CPU: Intel Core 2 Duo @ 2.00GHz
- GPU: ATI Radeon HD 3650 512 MB
- RAM:4Gb
- OS: Dual-boot: Windows 7 and Ubuntu 11.10 [/I][/B]

---

### Post by 2F4U on 2012-03-22
You could try this:

[http://www.ubuntuvibes.com/2011/10/how-to-fix-lag-issues-with-ati.html](http://www.ubuntuvibes.com/2011/10/how-to-fix-lag-issues-with-ati.html)

---

### Post by tbhatia4 on 2012-03-22
> **JonasDeMoor said:**
> Hi,

I'm new to Ubuntu(I come from Windows 7) and I installed Ubuntu 11.10 a few days ago. In the past, I already had problems with my video card, so I thought that maybe the problem has been solved now. 

When I use the open-source drivers for my ATI card, it all runs very smooth, but my laptop (Acer Aspire 8920G) 's fan is spinning fast and the laptop becomes hot. So I installed the official ATI drivers from the "Additional Divers" menu. I rebooted and now the laptop is very quiet but when dragging windows, scrolling and typing, it all lags

If anyone know a fix for this please let me know. 
(I'm totally new to Linux and  Ubuntu so no very difficult methods please)

[B][I]System Specs
***********
Acer Aspire 8920G
- CPU: Intel Core 2 Duo @ 2.00GHz
- GPU: ATI Radeon HD 3650 512 MB
- RAM:4Gb
- OS: Dual-boot: Windows 7 and Ubuntu 11.10 [/I][/B]
there is some issue with the new release of the additional drivers of ati 
even i had this
just disable that driver and reboot 
yoursystem will be good as new

---

### Post by Mark Phelps on 2012-03-22
The default open-source Radeon drivers are NOT going to help your overheating problem as they don't include that feature.

As to the AMD drivers, the latest 12.x version (it's either 12.2 or 12.3, don't remember which) claims to have improvements over the earlier versions.

Take a look at the download on the AMD Linux Driver page and see if the Linux version there is newer than the one you have.

If so, that could improve your situation.

---

### Post by JonasDeMoor on 2012-03-22
Thank you all for the very fast replies: I will try these things. 

I used Wubi to install Ubuntu and it installed the 64-bit version, maybe that's the problem beacuse my Windows 7 is 32bits and it came originally with Windows Vista 32bits.

Maybe I will try installing it with a Live-cd.

Thanks again for the very fast replies: I've posted this only one hour ago :KS

---

