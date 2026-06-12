---
title: "Don't think ubuntu has installed my wireless card!"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by josh_melvin on 2008-05-20
I am using an acer aspire 3690 series laptop and i dont think ubuntu has installed my internal wireless card that came with it! i don't know anything about my wireless card. any help would be nice :)

---

### Post by littletinman on 2008-05-20
what kind of wifi card do you have? if you have an atheroes ar5007eg then i can give you lots of info. If not, i can't help.

---

### Post by josh_melvin on 2008-05-20
> **littletinman said:**
> what kind of wifi card do you have? if you have an atheroes ar5007eg then i can give you lots of info. If not, i can't help.

not sure what wireless card i have but on the back of my laptop it says:

contains transmitter module: BCMD4311MCG

---

### Post by littletinman on 2008-05-20
ok type this in the terminal under Applications>accessories>terminal


> lspci



Post what that says

---

### Post by avtolle on 2008-05-20
Looks like, from that description, a Broadcom card. To check it out, from the terminal (Applications-->Accessories-->Terminal) type lspci, and check for that section of the output that describes the wireless network interface. If it is a Broadcom card, as it appears, there are several threads about how to get the same going here in the Forum; do a search for them and see if they help.

---

### Post by littletinman on 2008-05-20
> lspci -v | less


post this

---

### Post by josh_melvin on 2008-05-20
it came up with this:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
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
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

---

### Post by littletinman on 2008-05-20
ok try what i just posted, but i think that this

> Broadcom Corporation BCM94311MCG wlan mini-PCI

is your card

---

### Post by littletinman on 2008-05-20
Ok we have a hit, try this link, this should work



> [http://ubuntuforums.org/showthread.php?t=769990&highlight=Broadcom+Corporation+BCM94311MCG](http://ubuntuforums.org/showthread.php?t=769990&highlight=Broadcom+Corporation+BCM94311MCG)

---

### Post by josh_melvin on 2008-05-20
i says:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Acer Incorporated [ALI] Unknown device 0090
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Acer Incorporated [ALI] Unknown device 0090
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at d0200000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 5088 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at d0300000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Unknown device 0090
        Flags: bus master, fast devsel, latency 0
        Memory at d0280000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

:

---

### Post by littletinman on 2008-05-20
ok we don't need that anymore, at least i don't think so. Just follow the link i gave you.  that should do it

---

### Post by avtolle on 2008-05-20
> **littletinman said:**
> Ok we have a hit, try this link, this should work
Good find, there; that should allow the OP to get the wireless card up and going. Of course, should there be any problems, post back with a description of any errors, etc., and we'll try to help.

---

### Post by littletinman on 2008-05-20
Exactly, btw, what version of ubuntu are you using? 64 or 32?

---

### Post by stchman on 2008-05-20
> **josh_melvin said:**
> I am using an acer aspire 3690 series laptop and i dont think ubuntu has installed my internal wireless card that came with it! i don't know anything about my wireless card. any help would be nice :)

Moral of the story.

Broadcom does not support Linux so don't buy their products.

If you have major problems getting that card working you can try installing a 3945ABG card.  They work with Linux well.

---

### Post by josh_melvin on 2008-05-20
> **littletinman said:**
> Ok we have a hit, try this link, this should work

I have been there and the download link it gives u takes you to a site that i dont understand how to work (when u come to download it says u have to enter a 4 digit word and then it has a pciture of a cat!!!???!!!)

---

### Post by littletinman on 2008-05-20
hmmm, so you don't see any letters? see i tried it and it said to type the letters that had a cat in them (little white cat). hmmm

---

