---
title: "Problem installing wubi: Is it Toshiba or something else?"
date: 2012-08-27
forum: New to Ubuntu
---

### Post by rodtaylor on 2012-08-27
I have just recently bought a Toshiba Satellite P850/P855 laptop. I tried to install wubi from Ubuntu 12.04 by using a terminal code:

$ wubi.exe --force-wubi

It installed as usual. However, I realized that the wifi is not working. I bought an ethernet cable to see if any drivers should be installed first but it said that no proprietary drivers found. So I still can't have my Ubuntu running as I used to have on my Lenovo laptop. 

1. Is it because we can't install Ubuntu/Wubi on Toshiba?
2. Is there any way to get the wifi working?

Help please. Coz I really like Ubuntu.

Thank you.

---

### Post by gandaran on 2012-08-27
post the output of
```
sudo lshw -C network
```
so we can see the wireless chip brand and what driver is needed.

---

### Post by rodtaylor on 2012-08-27
Here is the output:


  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 05
       serial: b8:88:e3:15:51:7f
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:d000(size=256) memory:f2b04000-f2b04fff memory:f2b00000-f2b03fff
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:c000(size=256) memory:f7200000-f7203fff

Thanks before!

---

### Post by gandaran on 2012-08-27
> *-network UNCLAIMED
description: Network controller
product: Realtek Semiconductor Co., Ltd.
vendor: Realtek Semiconductor Co., Ltd.
big problem here! Realtek product but failed the chip model identification! (Realtek devices usually work out of the box in Ubuntu unless it's brand new stuff)
is the wireless switch on?
wireless card is enabled in BIOS? does it work on windows?
try this command and post the output too
```
rfkill list all
```
also can you check in windows the wireless card chip model information?

---

### Post by rodtaylor on 2012-08-27
Yes the wireless is switched on and it works perfectly on windows. 

Here is the output:
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

I checked on Device Manager in Windows and on the Network Adapters section, it shows:
- Realtek PCIe FE Family Controller
- Realtek RTL8723AE Wireless LAN 802.11n PCI-E NIC

Is this what you meant by Windows' wireless card chip model information?

Thanks!

---

### Post by gandaran on 2012-08-27
> Realtek RTL8723AE Wireless LAN 802.11n PCI-E NIC
yes this is what I wanted, now on google search use this [COLOR="Red"]Ubuntu RTL8723AE[/COLOR]
a quick search came up with this one that may help
[http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized)

---

### Post by rodtaylor on 2012-08-27
Wow, thanks!! It looks promising now! However, I can't seem to work on it now since I need to get the ethernet cable first from the office. I'll give it a go first thing in the morning and I will post the result. 

Thanks a lot Gandaran!

---

### Post by rodtaylor on 2012-08-28
Just a quick message to thank Gandaran for the replies. I am online with wifi now! Seems that the network is working just fine. I was worried about the reduced reception ability as in the link [http://askubuntu.com/questions/13963...not-recognized]("http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized") but it seems all fine with mine. 

Again, thanks a lot man!!

---

### Post by gandaran on 2012-08-28
> **rodtaylor said:**
> Just a quick message to thank Gandaran for the replies. I am online with wifi now! Seems that the network is working just fine. I was worried about the reduced reception ability as in the link [http://askubuntu.com/questions/13963...not-recognized]("http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized") but it seems all fine with mine. 

Again, thanks a lot man!!
glad you got it working.
try to remember you may have to install the driver again after every kernel update if you find wireless not working again, I'm not sure this driver works permanently, probably will need compiling again for every new kernel.

---

### Post by rodtaylor on 2012-08-28
Thanks for the heads-up! :)

---

