---
title: "Problem with Wireless D-Link AirPlus DWL G650+"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by harrylookalike on 2008-06-09
I can't get my Wireless card to work. I also have Windows installed on my laptop, and it works with windows, and I can see other wireless networks in the area with Ubuntu! But when I try to connect to the networks nothing happens, and the led on the wireless card does not blink for active...

I am not sure if this is enough info, please write me for more if necessary :) I just installed Linux Ubuntu yesterday and I really enjoy using it, so if I can just get my wireless card to work I can finally cut the bonds from Windows!

Anyone who can help?

Thank you :)

---

### Post by Het Irv on 2008-06-09
Do you have the CD that came with the wireless card? You may need to use the Windows Drivers to get the Wireless card to work.

Can you paste the output from ```
lspci
```

Just type the above command in the Terminal and paste what it spits out here in this thread.

---

### Post by harrylookalike on 2008-06-09
I don't have the CD, the card came with a cheap bought laptop from a friend of a friend :) But I do have the Windows driver in a folder in my Windows My Documents BACKUP directory on a removable harddrive, though I am unsure of how to use a windows based driver in Ubuntu? Furthermore it is late here in Denmark, and I don't have my removable harddrive with me until tomorrow, so I can't really check out how the driver files are managed at the moment :)

Here is what the terminal spat out:

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
03:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface


I hope it can help :)

---

### Post by Het Irv on 2008-06-09
NDISWrapper, its been a while since I used it, but there are plenty of How-To Threads on it.

---

