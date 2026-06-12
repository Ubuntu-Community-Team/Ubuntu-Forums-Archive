---
title: "Ubuntu doesn't boot when CD / DVD drive is connected"
date: 2015-12-05
forum: New to Ubuntu
---

### Post by kiam on 2015-12-05
I installed Ubuntu 14.04.3 LTS on an old system with a new harddrive today. At first it wouldn't install at all, but just froze with an error very similar to the one mentioned [here]("http://askubuntu.com/questions/228927/boot-failure-failed-command-identify-packet-device"), but without the [COLOR=#111111][FONT=Consolas]ata8: hard resetting link.
[/FONT][/COLOR]After disconnecting my CD / DVD drive, it finally managed to install. 

After some more problem solving (like Ubuntu freezing when trying to shut down), I can't find out how to fix the issue with the CD drive. When it's connected, Ubuntu just won't boot, and freezes at a purple screen.
The system I put the new drive in is an Acer Aspire M3920-e4012u, and [this]("http://www.webstore.be/product/caviar-blue-320gb-1") is the harddrive I'm using.

Can this be solved, or am I forced to leave out the CD drive?

---

### Post by cariboo on 2015-12-05
Check the cable connections to the CD/DVD drive. My system was taking a long time to boot, and stayed at the BIOS splash screen a lot longer than normal. I reseated the SATA and Power cables, and it is now working as it should.

---

### Post by kiam on 2015-12-05
I'm still not sure what the issue actually is, but I doubt it was the cable, since I unplugged and replugged it several times. I did end up fixing it, though I'm not sure it's the best solution. 

The drive was originally connected to a separate chip, and connecting it directly to the standard SATA ports on the motherboard instead fixed the issue. As far as I can tell, the drive works just fine.

---

### Post by dellboy56 on 2015-12-05
Press your bios key to get into bios and there should be a thing like boot from cd/dvd usb etc click that and you should be able to boot into live environment or you should be able to straight up install

---

### Post by Vladlenin5000 on 2015-12-05
> **dellboy56 said:**
> (...) and you should be able to boot into live environment or you should be able to straight up install

... or not. Most old BIOS do NOT boot optical drives connected to addon SATA cards. Even when that option is available, usually as "other...", it doesn't work or seldom works depending on what's actually connected to the addon card.
The symptom suggests exactly that and the same has been experienced in many boards.

---

