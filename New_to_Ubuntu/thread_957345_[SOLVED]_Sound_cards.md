---
title: "[SOLVED] Sound cards"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by sprogmeister on 2008-10-24
Please help! I installed virtual box on to Hardy. Upon restarting I lost the graphics card and sound card. The graphics are sorted now but I am still told that the sound card doesn't exist, but I know it does as I can use it if I use the past generic version of hardy. Can anyone tell me how to get the sound back up and running please?

---

### Post by Crandom on 2008-10-24
Type this command into a terminal:```
lspci
```and paste it here please.

---

### Post by sprogmeister on 2008-10-24
Thanks

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0a:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

---

### Post by Crandom on 2008-10-26
Its saying it exists:
> 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
and that card should work automatically. It looks to me like a driver problem or human error. This may sound stupid, but are you sure that the sound isn't muted by the keyboard, or your speakers are working, or that the cable is unplugged? I sometimes forget that I press the mute key on my keyboard and it doesn't show up in GNOME.

Anyway, sorry for forgetting your thread. The PM acted as a reminder. This should bump itself up to the top level now, with lots of people to see it.

---

### Post by sprogmeister on 2008-10-26
Thanks for the reply. The only time I can get it to work is by going to the generic version. It all happened when I installed VM ware and restarted, the graphics and sound failed to work. I have the graphics back but no sound. I have checked all possibilities, but the sound icon tells me there is no sound device. Any ideas on what I can do?

---

