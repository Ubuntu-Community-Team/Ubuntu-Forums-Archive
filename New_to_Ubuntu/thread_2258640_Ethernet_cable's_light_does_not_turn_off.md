---
title: "Ethernet cable's light does not turn off"
date: 2014-12-29
forum: New to Ubuntu
---

### Post by newbie13 on 2014-12-29
This is weird but when I shutdown my laptop from ubuntu or kali, ethernet cable's light does not go off. Everything else like fan, usb ports, power leds shut down but ethernet cable's light stays on.

Earlier, both ethernet port and usb port used to stay on which was ok for me because I charge my phone from laptop most of the times. But now only ethernet stays on which is of no use. This does not happen when I shut down using windows. To turn off the light I have to either pull out the battery and put it back again or simply pull out the cable.

Any suggestions??

---

### Post by tgalati4 on 2014-12-29
Install *acpitool* and examine the power status:

```
sudo apt-get install acpitool
acpitool -w
```

---

### Post by newbie13 on 2014-12-29
Which one is power status?

```
ajinkya@Ajinkya-ubuntu:~$ acpitool
   Battery #1     : charged, 100.0%
  AC adapter     : on-line 
  Thermal info   : <not available>
ajinkya@Ajinkya-ubuntu:~$ acpitool -w
   Device    S-state      Status   Sysfs node
  ---------------------------------------
  1. SPB1      S5    *disabled  pci:0000:00:15.1
  2. XPDV      S5    *enabled   pci:0000:05:00.0
  3. OHC1      S3    *enabled   pci:0000:00:12.0
  4. OHC2      S3    *enabled   pci:0000:00:13.0
  5. OHC3      S3    *disabled
  6. OHC4      S3    *disabled
  7. EHC1      S3    *enabled   pci:0000:00:12.2
  8. EHC2      S3    *enabled   pci:0000:00:13.2
  9. EHC3      S3    *disabled
  10. XHC0      S3    *enabled   pci:0000:00:10.0
  11. XHC1      S3    *enabled   pci:0000:00:10.1
  12. KBC0      S3    *enabled   pnp:00:06
  13. PS2M      S3    *disabled  pnp:00:07



```

---

### Post by tgalati4 on 2014-12-29
The network card typically hangs off of the PCI bus, but sometimes off of the USB bus.

```
lspci
lsusb
```

You can turn off a device with the -W switch with *acpitool*.

> tgalati4@Mint17 ~ $ acpitool -w
   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. LID0	  S3	*enabled 
  2. SLPB	  S3	*enabled 
  3. HDEF	  S3	*disabled  pci:0000:00:1b.0
  4. PXSX	  S5	*enabled   pci:0000:**02:00.0**
  5. USB1	  S3	*enabled   pci:0000:00:1d.0
  6. USB2	  S3	*enabled   pci:0000:00:1d.1
  7. USB3	  S3	*enabled   pci:0000:00:1d.2
  8. EHC1	  S3	*enabled   pci:0000:00:1d.7
tgalati4@Mint17 ~ $ lspci | grep Ethernet
**02:00.0** Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)


So my network card hangs off of the PCI bus at slot #2:00.0.  I could turn it off with:

```
sudo acpitool -W 4
```

Yours will be different.

---

### Post by newbie13 on 2014-12-30
How to determine which one of them is hanging the PCI bus slot?

---

### Post by newbie13 on 2015-01-02
Update-
This only happens when charger is connected. When it is not, the light turns off automatically.

---

### Post by plucky on 2015-01-02
Just a thought,have you tried turning off WOL (Wake on Lan) in the Bios of the laptop?

Good Luck

---

