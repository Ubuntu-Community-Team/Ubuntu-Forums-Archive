---
title: "installing a wifi driver from usb"
date: 2012-12-08
forum: New to Ubuntu
---

### Post by riosingh on 2012-12-08
Hi Guys,
after my dell insparon mini, just wend dead slow due to being riddled with virus' i decided to install ubuntu 12.10.
so basically i inslalled it and at the same time wiped windows.

now the problem I have is i cant connect to the wifi, after arseing about on the net I came to a uneducated conclusion that I need a driver for the wireless thingy.

so I followed the instructions in the help menu, and found out the make and model of my wireless thingy, its a realtek rtl8101e.
so then on my bros desktop i downloaded the linux driver from the realtek website, on to a USB stick.

and now i havent got a clue how to install the driver from USB stick to the netbook.

---

### Post by gandaran on 2012-12-08
> rtl8101e
are you sure this is the wireless card? looks more like it is the ethernet controller.
post the output of this code 
```
sudo lshw -C network
```

---

### Post by riosingh on 2012-12-08
*-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:24:e8:ee:db:d5
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:f0610000-f0610fff memory:f0600000-f060ffff memory:f0620000-f063ffff
rio@rio-netbook:~$

---

### Post by squakie on 2012-12-08
If you open network manager, does it show a wireless adapter and say "firmware is missing"?

---

### Post by mlentink on 2012-12-08
> **gandaran said:**
> are you sure this is the wireless card? looks more like it is the ethernet controller.


+1 AFAIK the Realtek is your ethernet controller. Ubuntu ships drivers for the Broadcom 4312 standard. Go to Ubuntu Software Center and select 'Edit' from the menu and then the Option 'Software sources'. Then go to the Proprietary Drivers tab on the right. See if it lists your card.

---

### Post by riosingh on 2012-12-08
> **squakie said:**
> If you open network manager, does it show a wireless adapter and say "firmware is missing"?

if i select network in settings, there are two options wired, or network proxy.
wired says cable unplugged and gives a hardware address, and network proxy just has a load of unpopulated proxy boxes

---

### Post by riosingh on 2012-12-08
> **mlentink said:**
> +1 AFAIK the Realtek is your ethernet controller. Ubuntu ships drivers for the Broadcom 4312 standard. Go to Ubuntu Software Center and select 'Edit' from the menu and then the Option 'Software sources'. Then go to the Proprietary Drivers tab on the right. See if it lists your card.

software sources has 5 tabs Ubuntu software, other software, updates, authentication and additional drivers.

if I click on additional drivers it says No proprietary drivers are in use.

---

### Post by gandaran on 2012-12-09
you will need to connect with wired internet and update the package list
```
sudo apt-get update
```
then in additional drivers you will find the Broadcom  BCM4312 802.11b/g LP-PHY wireless driver ready for activation.

if you don't have wired internet then try find the  BCM4312 802.11b/g LP-PHY driver in **.deb** package format, .deb's install with a double click.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20No%20Internet%20access)

---

### Post by mlentink on 2012-12-09
You might want to peruse this: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by riosingh on 2012-12-09
Ok.
I found a cable in the modem box (wifi modem, if thats what its calked feel free to correct me)
I pluged the netbook in and through the software centre I installed additional drivers.
Then I went to the system settings, andcin the software bit I activated it.

I then unplugged the modem cable, and the wifi would turn on for 5 sec blasts, and deactivate again.

So now I've reinstalled ubuntu from the pendrive, with the network cable plugged in.
Reinstalled additional drivers.

And gone back into software source, into additional drivers. Snd cheaked the uding broadcom box. Applied the changes. 

And whoop whoop,  with the modem cable unpluged I have WIFI.

Thank for all your help guys. I would have not beenvsble to do this without you.

---

### Post by mlentink on 2012-12-09
I'm sure I speak for all of us if I say we're glad to help, that's what the community is for. 
Would you mind marking your thread as 'solved'? Please see the 'Thread Tools' above.

---

### Post by riosingh on 2012-12-09
ok thread marked as solved,
from my netbook through the wifi:guitar:

---

