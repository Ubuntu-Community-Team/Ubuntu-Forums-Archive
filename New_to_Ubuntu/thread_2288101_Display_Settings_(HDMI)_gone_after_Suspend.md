---
title: "Display Settings (HDMI) gone after Suspend"
date: 2015-07-24
forum: New to Ubuntu
---

### Post by david414 on 2015-07-24
Hello, I'm new to this but I decided to use Linux more regularly @home (first).

So I installed Ubuntu 15.04 on my old Laptop (ACER Aspire 7730G - Graphics Gallium 0.4 on NV96) and use it on my big screen TV with the lid closed, via HDMI, with a wireless USB-Keyboard(Logitech K400r), like I did before but running Windows.

Runs very smooth so far except for when I go to suspend (Reboot works fine). On Wake Up there is no Signal on HDMI and when I open the lid it seems like the Display Settings are gone and I have to set them again (or reboot).

Went through a few Threads but didn't find quite the Problem I seem to have. Did anyone have a similar issue or can point me in the right direction? 
Much appreciated.

---

### Post by sgian on 2015-07-24
Sometimes the newer releases don't support older hardware that isn't as common anymore, to make room for drivers for newer hardware.  If you aren't happy with 15.04, I would suggest 14.04 LTS which is a long term support version of Ubuntu that will be supported for years and might support your laptop better since it is an older release.  Personally I don't use the suspend feature so I haven't run into that issue.

---

### Post by Vladlenin5000 on 2015-07-24
Hi and welcome.

I disagree with the previous post. It's in essence correct but entirely misses the point because a) that rarely happen, b) when it happens it has nothing to do with antiquity but with "rarity" and c) your hardware isn't so old or rare anyway, therefore not applicable.

That said, here's the problem:
```
ACER Aspire 7730G - [COLOR=#ff0000]Graphics Gallium 0.4 on NV96[/COLOR]
```

It's a Nvidia card (or integrated chip). It can be one of this:
```
GeForce 9400 GT, 9500 (GT, M G), 9600 (M GS, M GT), 9650M GT, 9700M GT  
 GeForce G 102M, GT 120  
 Quadro FX (380, 580, 770M, 1700M)
```

But the good news is it really doesn't matter. What matters is you most certainly need proprietary drivers for enabling the correct behavior. via HDMI or others.
Go to system settings > Software & Updates, find the rightmost tab, Additional Drivers. Select and apply the recommend proprietary driver from the list. Reboot. Test.

---

### Post by david414 on 2015-07-26
It's a GeForce 9600M GT indeed!

> **Vladlenin5000 said:**
> ...
What matters is you most certainly need proprietary drivers for enabling the correct behavior. via HDMI or others.
Go to system settings > Software & Updates, find the rightmost tab, Additional Drivers. Select and apply the recommend proprietary driver from the list. Reboot. Test.

Thank you so much, that was it. Work fine now.

---

### Post by Vladlenin5000 on 2015-07-26
You're welcome :-)

Please use the thread tools to mark this one as solved so future forum user may benefit.

---

