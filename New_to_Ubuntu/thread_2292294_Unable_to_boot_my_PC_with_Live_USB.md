---
title: "Unable to boot my PC with Live USB"
date: 2015-08-26
forum: New to Ubuntu
---

### Post by dids2 on 2015-08-26
Hello,  After visiting an Ubuntu install party with my tour, but without being installed, I had precious advice from a volonteer (upgrading my RAM, my graphic card and my HDD) I tried the Live USB to install Ubuntu, but I'm still unable to root. what is happening: when starting the PC I call for Boot, I choose Boot from USB but it always start the windows OS  I've tried on another laptop, and it work, so I gess the problem is not with the USB kee. I've tried serveral USB port, but not all of them actually (3 out of 6) I've set the BIOS to boot from the USB device first.  I didn't found information that I was searching in the forum, but I might also haven't search right, or properly.  My PC configuration is: mother board VIA KT3V  CPU AMD XP 1700 3Mo RAM DDR PC2700 Graphic card Ge Force4 MX 440 64 Mo HD DMA 133/7200 60 Go MXT IDE connection OS Windows XP SP3  thanks for any information :)

---

### Post by Petro Dawg on 2015-08-26
Where did you get the Live USB?  Did you make it or was it given to you?  Better make sure your USB was made correctly.

---

### Post by Vladlenin5000 on 2015-08-26
If the live USB works in another computer then it's probably fine.
Your old system, on the other hand, might not boot from USB at all or only from an external optical drive or floppy, not from a USB flash stick. If you have only one USB option at BIOS then it's most likely the aforementioned scenario. Either burn a DVD or use a PLOP bootable CD: [https://www.plop.at/en/ploplinux/downloads/live.html](https://www.plop.at/en/ploplinux/downloads/live.html) (boot from the PLOP CD like any other with the USB stick already inserted; at the plop's menu you should find an option to boot a USB device).

---

### Post by dids2 on 2015-08-27
Hey folks, thanks for answering :) I've found my issue, while looking for information about the SMART ability of the motherboard. My USB Legacy Support was set as No Mice instead of All Device Thanks to my hoarding disorder, I kept my motherboard manual through 6 relocation since I bought it in 2003. So if anyone have question about this MS-6712 ATX Mainboard, feel free to ask :)  Once that done, I could run the boot and proceed a test of ubuntu on my PC! As a result, I realize I should definitively upgrade my graphical card!

---

### Post by Bucky Ball on 2015-08-27
Welcome and nice one. Please mark as solved. See the first link in my signature for how. Thanks. Good luck. :)

---

