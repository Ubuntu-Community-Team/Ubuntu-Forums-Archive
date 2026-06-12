---
title: "Dual boot problem"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by Xinlitik on 2008-07-06
I'm trying to dual boot with the following settings:

SATA 1: Windows XP (installed second)

SATA 2: Linux (installed first)

I am stuck automatically booting to XP (couldnt find any options in BIOS to boot off the 2nd drive). Also, when I unplug the first, it gives a no boot device detected error at startup. (Also tried plugging 2nd drive into the 1st slot).

I tried booting ubuntu LIVE to configure the booting in grub, but the ubuntu loading screen bounced back and forth for a long time, finally leaving and repeating error messages like this:

319. 994238 Buffer I/O error on device sr0, logical block 19990

Whats the best way to get this going? Should I just redo it all installing linux second, or this is saveable?

thanks

---

### Post by bumanie on 2008-07-06
In terminal post the output of > cat /boot/grub/menu.lst The preferred method of installing a dual boot is to have windows installed first on the first disc, but some editing of the above list can often fix things.

---

### Post by bobpur on 2008-07-06
"The preferred method of installing a dual boot is to have windows installed first on the first disc, but some editing of the above list can often fix things."     --Bumanie

Back about 2 years ago, when I first got into linux, installing Windows first then linux was the way to get dual boot up and running. I don't believe you could edit GRUB then to fix problems. At least, I was so new that I didn't know it if there was. I still install Windows first and linux second. :)

---

### Post by bumanie on 2008-07-06
> Back about 2 years ago, when I first got into linux, installing Windows first then linux was the way to get dual boot up and running. I don't believe you could edit GRUB then to fix problems. At least, I was so new that I didn't know it if there was. I still install Windows first and linux second
Yeah, I do too, but there some 'map commands' that can be added to /boot/grub/menu.lst that sometimes 'trick' grub into looking for windows on a second drive, that's why I want to look at the list - it doesn't always work, but easier than installing from scratch, if it does work. It's worth a try.

---

### Post by Xinlitik on 2008-07-06
bumanie: I unfortunately cant reach the terminal...my computer automatically boots to windows, and for some reason it no longer will boot ubuntu LIVE.

I think I'll just format my linux hard drive and reinstall it. (making it the 2nd install)

---

### Post by red_team316 on 2008-07-06
Install linux 2nd. Also make your linux drive the SATA1 port and first in the BIOS boot order. That way your windows bootloader stays intact as well as the GRUB bootloader will have an option for booting to windows.

---

