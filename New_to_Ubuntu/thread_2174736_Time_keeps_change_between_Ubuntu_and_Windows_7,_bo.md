---
title: "Time keeps change between Ubuntu and Windows 7, both are on different hard drives"
date: 2013-09-15
forum: New to Ubuntu
---

### Post by ImTroyMiller on 2013-09-15
Here's what I have for hardware...
Gigabyte 970A-D3 Rev 3.0 motherboard
NVidia GeForce GTX 650 Ti Boost video/graphics card
AMD FX 6300 Six Core Processor
32gb of RAM(4x8gb sticks) Corsair Vengence
Asus DVD/Blu-Ray
1tb Hard Drive "00RKKA0"(With Windows 7 Professional)
1tb Hard Drive "07ZF5A0"(With Ubuntu 12.04 Precise Pangolin)
75gb Hard Drive "00FLA1"(No OS)

The time in Windows 7 leaps forward seven hours, then I correct it and boot Ubuntu, and Ubuntu's time is seven hours behind. Their are at a tug-o-war. I did a search and read that it's due to BIOS settings, but didn't find a direct answer.

---

### Post by radiowave911 on 2013-09-15
Sounds like they are fighting over the system hardware clock.  Are you, by chance, plus or minus 7 hours from UTC?

---

### Post by sanderj on 2013-09-16
> **ImTroyMiller said:**
> Here's what I have for hardware...
Gigabyte 970A-D3 Rev 3.0 motherboard
NVidia GeForce GTX 650 Ti Boost video/graphics card
AMD FX 6300 Six Core Processor
32gb of RAM(4x8gb sticks) Corsair Vengence
Asus DVD/Blu-Ray
1tb Hard Drive "00RKKA0"(With Windows 7 Professional)
1tb Hard Drive "07ZF5A0"(With Ubuntu 12.04 Precise Pangolin)
75gb Hard Drive "00FLA1"(No OS)

The time in Windows 7 leaps forward seven hours, then I correct it and boot Ubuntu, and Ubuntu's time is seven hours behind. Their are at a tug-o-war. I did a search and read that it's due to BIOS settings, but didn't find a direct answer.

Ubuntu stores the time in UTC time in the BIOS, Windows in local time.

Workaround:

open /etc/default/rcS for editing, and uncomment the line "UTC=yes" (or set to "UTC=no")

---

### Post by ImTroyMiller on 2013-09-16
^That solved it.  Thank you.

---

