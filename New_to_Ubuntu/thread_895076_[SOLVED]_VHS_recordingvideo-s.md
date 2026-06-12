---
title: "[SOLVED] VHS recording/video-s"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by Joseph5000 on 2008-08-19
I'd like to record some old VHS to my harddrive to burn. I have a Video-S cable, but ubuntu doesn't see it, or I don't know how to make it see. Any suggestions out there. thanks a lot.

joseph

---

### Post by halitech on 2008-08-19
do you have an actual tv tuner card or just a regular video card with S-video out capabilities?

---

### Post by Joseph5000 on 2008-08-19
Good Question, How do I figure that out?

---

### Post by halitech on 2008-08-19
open a terminal (Applications - Accessories - Terminal) and type in ```
lspci
``` and post the results back here

---

### Post by Joseph5000 on 2008-08-19
OK, Here is the reply

joseph@ubuntujoseph:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
02:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
joseph@ubuntujoseph:~$

---

### Post by halitech on 2008-08-19
ok, I'm guessing you have a laptop with built in Intel graphics chip but I dont see any other card for bringing video in so I would have to say you have an S-video out capability

here's mine:
```
daryl@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)
02:0a.0 Multimedia audio controller: Ensoniq ES1370 [AudioPCI] (rev 01)
02:0b.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
[color="red"]02:0c.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)[/color]
daryl@ubuntu:~$
```

the info in red is my tv tuner card

---

### Post by Joseph5000 on 2008-08-19
You are saying that I can't record from an external source??

---

### Post by halitech on 2008-08-19
not unless you have a USB device you didn't mention that is for recording from S-video

---

### Post by Joseph5000 on 2008-08-19
Hello confusion!
I have an S-video port on the back of the laptop and was hoping to copy some VHS so I can bring it into DVD. Maybe mt laptop is too old. Do you have any suggestions what else I can do?
It is deeply appreciated

---

### Post by halitech on 2008-08-19
in most cases, the S-video is for output only. There are external devices that connect by USB cable to a computer (not just for laptops) but you will need some kind of port that is designed for bringing data in and not sending data out in order to record from VHS

---

### Post by Joseph5000 on 2008-08-19
OK, I needed to go to the store anyways. Thank you very much.

Joseph

---

### Post by halitech on 2008-08-19
no problem, just make sure it is compatible with Linux before you buy anything

---

### Post by TransitMan on 2008-08-19
> **Joseph5000 said:**
> Hello confusion!
I have an S-video port on the back of the laptop and was hoping to copy some VHS so I can bring it into DVD. Maybe mt laptop is too old. Do you have any suggestions what else I can do?
It is deeply appreciated

Your S-video is OUTPUT only, not INPUT.

You need a separate card or USB capable device to record VHS to the hard drive for burning. Since you are running a laptop, your only choice is a USB device capable of signal INPUT, either by cable connection, S-video or RCA connections.

BTW, the laptop is not too old. It is not configured for what you want, and I don't think you'll find one on the market to do what you want. Purchasing a USB device will be your only option.

---

