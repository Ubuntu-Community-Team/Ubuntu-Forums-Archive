---
title: "Problem getting my third monitor working...."
date: 2013-08-12
forum: New to Ubuntu
---

### Post by agons on 2013-08-12
Hello all,
I got my dual monitor set up working fine in ubuntu 12.04 LTS  but since I had to re organize my desk areas i had to move all three of my monitor's to a single spot which works fine with windows but i can only seem to get two of the three for my ubuntu machine. It has the ability to use 3 but needs a display port active adapter to function in windows which i have. And when I i connect all three two DVI and one display port my monitors all go black, the computer is still working and when i have videos or music going they continue to play and i can use shortcuts from my keyboard to change volume/start/stop playback but i just have no video on my screen. anyone else have this issue?

---

### Post by The-Server-4dmin on 2013-08-12
I ended up running an old driver to get mine to work. I think the new drivers are buggy. What card and driver are you using?

---

### Post by agons on 2013-08-12
ati 6970

---

### Post by agons on 2013-08-12
Sorry took me a min to find the driver, its a HD 6970 card with the ati/amd proprietary FGLRX graphics driver (post-release updates)

---

### Post by QIII on 2013-08-12
I'm running the latest release driver from AMD's website.  DVI/DVI/DP, but an actual DP cable directly to the monitor.  No DP-to-DVI adapter, but that shouldn't matter.  I'm getting Eyefinity out to all three monitors.

It might be a pain, but it might be worth trying installation from the AMD website.  The -updates version *should *&#8203;work, but who knows.

---

### Post by agons on 2013-08-12
> **QIII said:**
> I'm running the latest release driver from AMD's website.  DVI/DVI/DP, but an actual DP cable directly to the monitor.  No DP-to-DVI adapter, but that shouldn't matter.  I'm getting Eyefinity out to all three monitors.

It might be a pain, but it might be worth trying installation from the AMD website.  The -updates version *should *&#8203;work, but who knows.


IM not running eyefinity does that change anything in ubuntu i assume it shouldn't.

---

### Post by DuckHook on 2013-08-13
> **QIII said:**
> It might be a pain, but it might be worth trying installation from the AMD website.  The -updates version *should *&#8203;work, but who knows.My 7970 would not support more than 2 monitors until I downloaded and installed the latest from AMD's website.

---

### Post by QIII on 2013-08-13
> **agons said:**
> IM not running eyefinity does that change anything in ubuntu i assume it shouldn't.

You don't have to "turn on" Eyefinity.  The technology is used when you use 3 or more monitors with the appropriate driver.

---

