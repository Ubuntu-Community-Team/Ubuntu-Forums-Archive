---
title: "Xubuntu wireless and mobile broadband setup"
date: 2012-11-05
forum: New to Ubuntu
---

### Post by Mazraq on 2012-11-05
Hi there,

I just downloaded xubuntu 12.10 as I was advised to that instead of Ubuntu because it's lighter. I can't seem to be able to activate my wireless. My computer is Lenovo X100e and the wireless driver model is Realtek 802.11bgn. I checked on the wiki and Realtek is one of those supported by Ubuntu. I don't seem to know what's going on! I also have a USB 3G mobile broadband that is working fine now Windows, but Xubuntu does not seem to be able to detect it when.I insert in my USB port. Your advice on both of these things is highly appreciated

---

### Post by newb85 on 2012-11-05
To give us more info about your wireless card/situation, please copy and paste the following to the terminal, and then copy and paste the output back to this thread.
```
sudo lshw -C network
```

Also, to give us more info about your USB 3G Broadband dongle, plug it in and do the same with
```
sudo lsusb
```

---

### Post by Mazraq on 2012-11-06
Thank you so much for your reply! So my 3GB has finally worked, but my wireless has not! Would really appreciate your help! I would really hate to have to switch back to Windows :(

Here is the result for the wireless, looking forward to hearing from you!

mazraq@mazraq-ThinkPad-X100e:~$ sudo lshw -C network
[sudo] password for mazraq: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: c8:0a:a9:05:55:b2
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
        capabilities: pm msi pciexpress msix vpd bus_master cap_list rom  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fw  ip=10.0.0.103 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:42 ioport:a000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff memory:d0020000-d003ffff
  *-network DISABLED
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 10
       serial: 90:4c:e5:e1:e3:76
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192se  driverversion=3.5.0-17-generic firmware=N/A latency=0 link=no  multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 ioport:b000(size=256) memory:d0300000-d0303fff
mazraq@mazraq-ThinkPad-X100e:~$

---

### Post by Mazraq on 2012-11-06
I should add that my computer does not actually have a physical switch for wireless! On Wondows, I would use Fn and F5 to turn it on and off.

Thanks again!

Moe

---

### Post by newb85 on 2012-11-06
> **Mazraq said:**
> 
  ***-network DISABLED**
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 10
       serial: 90:4c:e5:e1:e3:76
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192se  driverversion=3.5.0-17-generic firmware=N/A latency=0 link=no  multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 ioport:b000(size=256) memory:d0300000-d0303fff
mazraq@mazraq-ThinkPad-X100e:~$

I'm sure you already noticed that part.  That means your card is disable either by the hardware switch or by your Network Manager applet.

I would expect your hardware switch(Fn+F5) to work the same as in Windows.

I'm not familiar with Xubuntu or its Network Manager, but the one in Ubuntu will actually say "wireless is disabled by hardware switch" or "wireless is disabled", depending on which way it was disabled.

---

### Post by Impavidus on 2012-11-06
> **newb85 said:**
> 
I'm not familiar with Xubuntu or its Network Manager, but the one in Ubuntu will actually say "wireless is disabled by hardware switch" or "wireless is disabled", depending on which way it was disabled.
That is correct.  Left click on the network symbol in the xfce panel and it tells you wether wifi is enabled, disabled or disabled with the physical switch, right click to enable or disable it (if it works).

---

### Post by Mazraq on 2012-11-06
Thanks guys! Here is a picture of my xfce, and as you can see it says " wireless is disabled by hardware switch", but it's fainted so i can't click on it to change it :( I of course tried to press Fn+F5 many times but it's not doing anything!!

---

### Post by Linux_junkie on 2012-11-06
Within 'Network Connections' has it set up the Wi-Fi card under the Wireless tab?

---

