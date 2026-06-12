---
title: "Browsing lags until page fully loaded: But not on W7"
date: 2013-10-29
forum: New to Ubuntu
---

### Post by onyxogen on 2013-10-29
I have a problem regarding internet browsing on Ubuntu. I'm migrating from Windows 7 which is installed on the same machine so I can compare both OS.
One thing I notice which troubles me is the way browsers on Ubuntu do perform.
Let me describe the performance on Windows 7. Used browser: Firefox 24 or Chromium - doesn't matter.
I go to let's say imdb.com, the page starts to load for about 3 seconds. During this time I already can scroll smoothly and the browser is reacting to my input.

Same situation on Ubuntu, same browsers (also on Xubunbtu, Lubuntu...):
The page imdb.com loads in 3 seconds too. But during this time I cannot scroll smootly. The browser lags and jumps, sometimes freezes then speeds up etc. It's like CPU is on 100% and the UI runs on the same thread as the rendering engine. Once the page is loaded everything runs smoothly.

What's the problem here? This keeps me from using Ubuntu right now. Sounds strange but as I'm browsing most of my time this problem is very dominant.
Can anyone help me?

---

### Post by sotiris2 on 2013-10-29
Can you give us some specifications? Most importantly the GPU and whether or not you 've installed the proprietary drivers for it.

---

### Post by onyxogen on 2013-10-29
Of course. It's a Acer Aspire 1810TZ:
- Intel Pentium Dual Core SU4100 1.3 GhZ
- Intel GS45 Mainboard
- 4GB RAM
- Intel graphics Media Acc. (GMA) 4500M HD

I did not install any proprietary drivers for it.

---

### Post by sotiris2 on 2013-10-29
I do not think you actually do to install proprietary drivers for it since Intel's open source ones are pretty good.
Does your system behave smoothly in other operations? (Using the dash for example)
You can verify whether its a cpu load issue by running **top** on a terminal (alt+ctrl+t). Check if firefox or chromium is hogging up the cpu while rendering
. A bit of googling for firefox cpu issues suggesting trying disabling * Use hardware acceleration when available * from *Edit->Preferences->Advanced*

---

### Post by onyxogen on 2013-10-30
yes, it's CPU usage.But I found a switch in chrome flags to activate a second thread while loading. In combination with enforcing GPU rendering the browser now behaves like it does on Windows 7 . Great!

---

