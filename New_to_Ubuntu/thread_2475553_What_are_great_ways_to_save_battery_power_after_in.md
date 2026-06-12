---
title: "What are great ways to save battery power after installing Ubuntu for the first time?"
date: 2022-05-31
forum: New to Ubuntu
---

### Post by masteryoyogi on 2022-05-31
If I search the web for Ubuntu and battery consumption, I always run into the following recommendations posted between (2010 - 2020):


[LIST]
[*]Install TLP
[*]Install PowerTop alongside TLP
[*]Dim Screen brightness
[*]Disable Bluetooth if not in use.
[*]Use another desktop environment (haven't tried this yet)
[*]Change Power Settings to Power Savings
[/LIST]

Following some of these steps did help a bit.

**i have a few questions:**


[LIST=1]
[*]I sometimes find people saying to use PowerTop and TLP, and others say not use them both at the time. What's the right answer?
[*]For some reason it takes 10 to 15 mins for Ubuntu to calculate the remaining battery power. At some point I get the percentage but if I click it says:  "Estimating...". Eventually I get the remaining time. Is there a way to fix this?
[*]Is installing TLP enough, or do I need to set it up for it to work better? I've also made sure it starts when I boot up my computer.
[*]Are there any other recommendations I should consider for saving battery power? I'm pretty sure Ubuntu 22.04 doesn't come with these optimizations out of the box.
[/LIST]

Thanks! Oh I'll share my computer specs, just in case it helps:


[LIST]
[*]**Hardware:** HP HP Pavilion Laptop 15-eh0xxx
[*]**OS:** Ubuntu 22.04 LTS (64-Bit)
[*]**GNOME Version:** 42.1
[*]**Windowing System:** Wayland
[*]**Memory:** 16.0 GB
[*]**Processor:** AMD® Ryzen 7 4700u with radeon graphics × 8
[*]**Graphics:** AMD® Renoir
[*]**Disk Capacity:** 512.1 GB
[/LIST]

---

### Post by TheFu on 2022-06-01
I have an Intel Core i5 8th-gen laptop. No fancy GPU.  I have it set to suspend quickly (15m) and dim the display almost too fast (5min). It has an SSD, not a HDD and uses wired ethernet, seldom wifi and I have all BT stuff disabled in the BIOS. BT is too much of a security failure to be allowed.

I use Xorg, not wayland. Wayland breaks about 10 of my workflows still.

I don't have any power-whatever installed. The CPUs automatically throttle-back when not in use on battery power.  I'd take the laptop for half a day of use and even being very wasteful, there would be over 50% battery remaining.  I haven't used it on battery much since COVID, so I don't know how that has held up. Also, since it is usually plugged in, the power settings have changed to reflect that - it doesn't dim and only goes into standby after nightly backups finish.

Oh, and I don't use any DE.  Minimizing CPU use is part of power management, so use the lightest GUI/DE you can stand.  I use fvwm, but most people would find that too archaic. Using openbox would be a less good option, since fvwm to unlimited things that openbox can't imagine, but openbox was the WM under LXDE for a long time.

Don't know how useful any of this is for you.
Oh ... the power controls are in the /etc/systemd/logind.conf  file. The manpage for that file explains the available settings.  mate-power-preferences also has some settings, if you use the Mate DE. If you don't use Mate, it would be worth search in the local manpages on your system for the power management tool(s) already installed. Check those out.  You can use **apropos** or **xman** to search manpages.

---

### Post by mIk3_08 on 2022-06-02
> **masteryoyogi said:**
> If I search the web for Ubuntu and battery consumption, I always run into the following recommendations posted between (2010 - 2020):


[LIST]
[*]Install TLP
[*]Install PowerTop alongside TLP
[*]Dim Screen brightness
[*]Disable Bluetooth if not in use.
[*]Use another desktop environment (haven't tried this yet)
[*]Change Power Settings to Power Savings
[/LIST]

Following some of these steps did help a bit.

**i have a few questions:**


[LIST=1]
[*]I sometimes find people saying to use PowerTop and TLP, and others say not use them both at the time. What's the right answer?
[*]For some reason it takes 10 to 15 mins for Ubuntu to calculate the remaining battery power. At some point I get the percentage but if I click it says:  "Estimating...". Eventually I get the remaining time. Is there a way to fix this?
[*]Is installing TLP enough, or do I need to set it up for it to work better? I've also made sure it starts when I boot up my computer.
[*]Are there any other recommendations I should consider for saving battery power? I'm pretty sure Ubuntu 22.04 doesn't come with these optimizations out of the box.
[/LIST]

Thanks! Oh I'll share my computer specs, just in case it helps:


[LIST]
[*]**Hardware:** HP HP Pavilion Laptop 15-eh0xxx
[*]**OS:** Ubuntu 22.04 LTS (64-Bit)
[*]**GNOME Version:** 42.1
[*]**Windowing System:** Wayland
[*]**Memory:** 16.0 GB
[*]**Processor:** AMD® Ryzen 7 4700u with radeon graphics × 8
[*]**Graphics:** AMD® Renoir
[*]**Disk Capacity:** 512.1 GB
[/LIST]


For me, on my HP Elite laptop; Dim Screen brightness has a big help to save my laptop battery. And yes, "Disable Bluetooth if not in use"  can also reduce the consumption of my laptop battery. In my Linux Ubuntu Operating System I used light weight Unity DE. 
In this settings my battery can reach up to few hours of use. I can't determine the exact hours because I'm not use to monitor it. Linux Ubuntu Operating System has a power saving notification in my battery but I'm not so particular about it. Every time we had a power cut my UPS is very useful to power up my ISP router and it can power up an hour and a few minutes long. Glad to have those hours every time we had a power cut in our area. We still have Internet in that case. Using LAN instead of WiFi also has a big help.
Before when my Laptop was new my battery reaches up to 4 hours of use but now, I only use it for almost 2 and a half hour because maybe I am not too careful of using it or just maybe there's a deterioration of my battery when it gets old. Regards and cheers.

---

### Post by ActionParsnip on 2022-06-02
Make sure that you have the latest BIOS too. This can help

---

