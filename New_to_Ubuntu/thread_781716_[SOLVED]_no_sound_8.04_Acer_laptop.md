---
title: "[SOLVED] no sound 8.04 Acer laptop"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by raequin on 2008-05-04
resolved

Opening an mp3 file works --- at least Totem shows visualizations.  No sound comes out though.  I'd appreciate if you could help me get sound.  Here is the result from lspci:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
0a:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0a:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0a:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
0a:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
0a:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by northern lights on 2008-05-04
What distribution are you running?

Have you checked whether anything's muted in alsamixer?

Can you also post the output of ```
cat /proc/asound/cards
```

Thanks

---

### Post by raequin on 2008-05-04
I just installed Hardy Heron.

Here's the output you requested.

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0500000 irq 22

---

### Post by northern lights on 2008-05-04
mkey -

the device is definitely configured it's in /proc.

Are you sure the surround is up and not muted in "alsamixer"?

Intel High Definition Audio has been rather problematic in Gutsy (and earlier, obviously), but should be working out of the box in Hardy.

It was working in our Dell D630 since Hardy Alpha5.

If it's not as easy as a muted channel you could read through [the "HdaIntelSoundHowto"]("https://help.ubuntu.com/community/HdaIntelSoundHowto") and f*ck around, but that was not written for Hardy...

---

### Post by kwacka on 2008-05-04
Also ensure that 'External Amplifier' is NOT selected in alsa mixer.

---

### Post by raequin on 2008-05-04
resolved

Thanks.  I downloaded gnome-alsamixer because I did not know how to check the external amp and surround muting otherwise.

I never did find external amp.  Surround was muted, and I unchecked that, now my sound works.

---

