---
title: "WiFi &amp; 8.04"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by GaryLittlemore on 2008-05-02
Since upgrading to 8.04 my WiFi has stopped working and I'm having to run wired.

Can anyone help a noob please?

---

### Post by tjwoosta on 2008-05-02
most likely your missing the right drivers for your wireless card

what is the model # and brand name for your card?   

if its an internal card you can usually find it by doing this command
```
lspci
```

if its an external card you usually find it by doing this command 
(although ive heard of people finding internal cards here too)
```
lsusb
```

---

### Post by GaryLittlemore on 2008-05-02
Don't know that this means, but this is what it said:

Bus 001 Device 001: ID 0000:0000 

It's an external Belkin G card F5D7010uk

---

### Post by GaryLittlemore on 2008-05-02
I thought mine was an external cos it plugs into the side of my laptop, but I've just ran the 'lspci' code and this is what I got:

00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
00:0a.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1
06:00.0 Ethernet controller: Belkin Unknown device 701f (rev 20)

---

### Post by tjwoosta on 2008-05-02
yea sry i guess external is pci (mine is usb)

but anyway im guessing this is your card
> 
06:00.0 Ethernet controller: Belkin Unknown device 701f (rev 20)


now if ubuntu says its unknown its because you dont have the correct drivers, so your going to probably need to use ndiswrapper and get a windows driver for that card

i wish i could help you out more but ive never actaully had to use ndiswrapper although ive heard of alot of people who use it with sucesss

try searching google for "F5D7010uk driver ubuntu" or something along those lines, chances are someones already had your problem and solved it already

hope that helps

---

### Post by GaryLittlemore on 2008-05-02
Can anyone else shed some light on this?

---

### Post by Tom--d on 2008-05-02
Do lspci -n and post the outcome.

---

### Post by Tatty on 2008-05-02
ndiswrapper info : [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

wifi troubleshooting : [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by MattBD on 2008-05-02
> **GaryLittlemore said:**
> Don't know that this means, but this is what it said:

Bus 001 Device 001: ID 0000:0000 

It's an external Belkin G card F5D7010uk

That's strange, I have the same card, but it works fine, but the manufacturers sometimes change the chipset without changing the model so that could be why.

If there's no driver for it, you'll need to use ndiswrapper to install the Windows driver. You can install ndisgtk which is a graphical front end for ndiswrapper and should make it easier.

---

### Post by GaryLittlemore on 2008-05-02
> **Tom--d said:**
> Do lspci -n and post the outcome.

00:00.0 0600: 1002:cab0 (rev 13)
00:01.0 0604: 1002:700f (rev 01)
00:02.0 0c03: 10b9:5237 (rev 03)
00:06.0 0401: 10b9:5451 (rev 02)
00:07.0 0601: 10b9:1533
00:08.0 0703: 10b9:5457
00:0a.0 0607: 1217:6933 (rev 01)
00:0a.1 0607: 1217:6933 (rev 01)
00:0c.0 0c00: 104c:8026
00:10.0 0101: 10b9:5229 (rev c4)
00:11.0 0680: 10b9:7101
00:12.0 0200: 100b:0020
01:05.0 0300: 1002:4336
06:00.0 0200: 1799:701f (rev 20)

---

### Post by GaryLittlemore on 2008-05-06
**Bump*** :biggrin:

---

### Post by Tiede on 2008-05-06
Do as MattBD suggested, and install ndisgtk.
Once you're done, there shoud be an entry in System->Administration called Windows Wirelss Drivers.
Click on it, give your credentials, select Add new device, browse to the windows folder where your card's driver is and select the related .inf file --mine was /windows/802bg/bcmwl5a.inf, for example. (I have a Broadcom 802.11 card)
Hopefully, this will give you back wireless.

---

### Post by GaryLittlemore on 2008-05-09
> **Tiede said:**
> Do as MattBD suggested, and install ndisgtk.
Once you're done, there shoud be an entry in System->Administration called Windows Wirelss Drivers.
Click on it, give your credentials, select Add new device, browse to the windows folder where your card's driver is and select the related .inf file --mine was /windows/802bg/bcmwl5a.inf, for example. (I have a Broadcom 802.11 card)
Hopefully, this will give you back wireless.

Thanks M8, I have my WiFi back.

---

