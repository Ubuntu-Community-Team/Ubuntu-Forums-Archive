---
title: "WIFI on Ubuntu 8.10"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by Wantingtolearn on 2008-11-06
I have a Compaq Presario C500, yeah I know kinda crudy, and formally I had Ubuntu 8.04 which recognised my wireless card, 8.10 does not seem to pick it up automatically, I tried the backports, and rebooted and nothing.   I am not sure what else to try please help.

---

### Post by stephanvaningen on 2008-11-06
Please include the result of this command in the thread:
 ```
lspci
```
as well as this after a boot:
 ```
dmesg | tail
```

---

### Post by Wantingtolearn on 2008-11-06
The first part:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
06:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


Not sure how you would like me to do the second, should I boot up as normal and immediately do the command?  Thank you in advance.

---

### Post by LowSky on 2008-11-06
this should help, FYI you Wifi card is this model BCM4311 (Rev 01) 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by igknighted on 2008-11-06
I used that card for a long time, and with the release of Ibex (and if you have all the updates, it was backported to Hardy), there is a brand new (and much better!) driver.  It is listed in the hardware drivers application as Broadcom STA.  See the link for it here: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php).  This should give you far less headache and much better range than the older b43/mcm43xx drivers did.

Oh, to activate it, make sure you are online and open system-administration-hardware drivers and select broadcom STA and click activate.  It needs to download some firmware, then restart, and you should be good to go.

---

### Post by stephanvaningen on 2008-11-06
> **igknighted said:**
> Oh, to activate it, **make sure you are online** and ...
nice one there ;-)

This indeed requires that you have a connection via LAN cable on that same computer at that moment.

---

### Post by Wantingtolearn on 2008-11-06
So, i followed igknighted's advise to start, the new driver was installed, but I am not seeing any available connections in WIFI Radar or network connections.  Should I set up a new wireless network, and if so how do i go about doing that?  Thank you, everyone.

---

### Post by stephanvaningen on 2008-11-06
You don't have to set up a new wireless network, it should be seen in the list of wireless networks when you left-click the network icon in the 'system tray' (<- is it also called like this in ubuntu? ;))

You find no wireless networks at all he? (Because otherwise possibly your network's SSID might not be 'broadcasted') -- sorry, maybe a stupid question.

If you afterwards go to System -> Administration -> 'Hard Drivers', do you see the driver indeed enabled, or still there and the button 'Enable' clickable? If so, the driver could not be installed...

---

### Post by igknighted on 2008-11-06
Any reason you are not using network manager?  It's the default for network connections because it is the best, I would use that first.

---

