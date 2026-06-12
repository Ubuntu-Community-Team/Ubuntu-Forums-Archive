---
title: "Memory problem..."
date: 2013-04-29
forum: New to Ubuntu
---

### Post by Erik The Pope on 2013-04-29
So I've got this homebuilt computer (ASUS P5E3 Premium mb, Intel SSD + 2 other HD's, NVidia video & Creative X-Fi Elite sound). I've loaded several versions of Ubuntu, Ubuntu Studio & Dream Studio on it and with 2 sticks of OCZ DDR3-1800 (P/N OCZ3P1800GK) it runs fine. (BTW, I'm a complete newbie with Ubuntu but was a prof computer tech for years with Win) I have 2 other sticks of identical memory (not bought together tho) and if I put them in the same slots, it will also run fine. If I add either set into the remaining 2 slots, it won't boot at all. I've got a CD with KDE Partition Mgr 1.0.3 that has Memtest86+ and I've run that on both sets & all 4, for a couple hours, and it says no errors. This is the 64 bit version & it seems memory size should be no problem. Color me confused, dudes! Little help here?

---

### Post by DuckHook on 2013-04-29
Have you checked BIOS? Since it's a new rig, it's probably EUFI and they might have obscure settings that enable/disable memory slots in weird ways. Or perhaps you have a wonky BIOS altogether? Would you consider updating it or would this void your warranty? Or perhaps its a wigged mobo with bad slots? Though unlikely, check to make sure that you haven't maxed out your mobo capacity. Don't know anything about your mobo, but if it maxes out at 16 GB and you've got 8GB sticks, then it will only accept two. Lastly, it is just possible that you have mismatched RAM/CPU/mobo combo. Does both mobo and CPU support 1800 speed? If so, is RAM the right timing? Are you overclocking? You may have had better luck posting in the HW forum, but you're here now and the mods frown on double-posting. You might ask them to move this thread for you, though.

---

### Post by Mark Phelps on 2013-04-30
You need to check the motherboard documentation for supported memory speeds using 4 sticks.  Sometimes, you have to throttle back when all four memory slots are in use -- that was the case in an older ASUS motherboard I once had.

---

### Post by Erik The Pope on 2013-04-30
Sorry, I thought I had mentioned that the sticks were 1 GB each, total of 4. I think this MB can to up to 64 GB so I doubt that I'm running into MB memory problems. Also, this used to be my regular XP computer & it ran fine for years but it doesn't have EUFI bios. I have looked at the slots and they seem to be identical, no broken contacts that I can see. I suppose the other two have a problem but I think it would show up with Memtest. BTW, not O/C'd either. I will also look into updating the BIOS. How do you do that with Ubuntu? And I thought this was going to be easy...

---

### Post by Erik The Pope on 2013-04-30
Looked at the manual: The mb will support 8 GB of ram. Said something about XMP profiles & only using two memory modules so I will check that. Anything else?

---

