---
title: "drivers assistance plz :)"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by feedmeh8 on 2008-04-29
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     T8100  @ 2.10GHz
stepping	: 6
cpu MHz		: 2101.000
cache size	: 3072 KB
physical id	: 0
siblings	: 2



am totally new to ubuntu HARDY. and am wandering how i go about getting the drivers i need. particularly for WoW. 

thnx :D

oh.. the above is all i could find on my system... im trying to find where the system info is at:p will edit in some more info if i do

---

### Post by spiderbatdad on 2008-04-29
posting the result of the command lspci might be helpful. There used to be a few tutorials on setting up WoW to run under wine.
[http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

---

### Post by feedmeh8 on 2008-04-29
thanx much :) here are results 

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 11)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)


i got WoW installed through wine after a lot of frustrating trial and error lol . but it is verry glichy and slow and verry twilight-zoney. im thinkin its a driver problem. i dont know what else it could be as it ran beautifully on xp

---

### Post by spiderbatdad on 2008-04-29
not sure what driver to recommend for this card. Do you have desktop effects like compiz running? I'm sure you would want to disable effects while playing WoW. 
What driver are you currently using? 

does the command ```
glxinfo | grep rendering
``` return "direct rendering: YES?

---

### Post by feedmeh8 on 2008-04-29
thanx again for help :) 

yes the command came back positive how do i know what driver i am using? 

ye i have some compiz stuf running but even if its off i still get the gliched out graphics

---

### Post by spiderbatdad on 2008-04-29
I meant disable desktop effect under system>>preferences>>appearances...You probably knew that. :P
You might also try posting in the gaming forum. I don't know if you'll get immediate responses, but the ones you get may be on target.
Try to give some info...like include lspci...

[http://ubuntuforums.org/forumdisplay.php?f=93](http://ubuntuforums.org/forumdisplay.php?f=93)

---

### Post by mivo on 2008-04-29
Did you play WoW with this integrated Intel video chipset before smoothly? In Windows, I mean. It's not really designed for gaming. :)

---

### Post by feedmeh8 on 2008-04-29
ye it worked really well with xp. everything was maxed with mo problem

---

