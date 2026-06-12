---
title: "WIFI and Ethernet NO connection"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by sthitaprajna on 2012-10-31
Hello all,

Just installed  Ubuntu 12.10 on my old macbook. I am using another  computer to  troubleshoot through. I can't seem to get the driver for my  wireless  card to work nor can I hook up to ethernet directly. 

Here is some information from the lspci -nnk | grep -iA3 net code:

 00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP79 Ethernet [10de:0ab0] (rev b1)
              Subsystem: NVIDIA Corporation Device [10de:cb79]
              Kernel driver in use: forcedeth
              Kernel modules: forcedeth
  --
  03:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
              Subsystem: Apple Inc. Device [106b:008d]
              Kernel driver in use: b43-pci-bridge
              Kernel modules: ssb

I  followed a few posts with no success, totally lost, any information on a direction I can take would be greatly   appreciated. Thanks!

---

### Post by sthitaprajna on 2012-11-01
So far I have followed this post:
 [https://help.ubuntu.com/community/BroadcomSTA%28Wireless%29](https://help.ubuntu.com/community/BroadcomSTA%28Wireless%29) 

for model # 14e4:432b

Downloaded and installed** b43fwcutter** to firmware directory, rebooted. Still no luck yet. Any help out there?
[B]
[/B]

---

### Post by Yezinki on 2012-11-01
Try installing it's firmware b43 installer along with b43-fwcutter.

---

### Post by Hadaka on 2012-11-01
Hi, per the link you posted you need the STA driver
[14e4:432b]

---

### Post by sthitaprajna on 2012-11-01
Okay, b43sta and firmware b43 installer. Where can I get those? I have no internet connection from my machine so I can't get them from the terminal like many threads describe. 

I've also mosied around NVIDIA website for ethernet driver and can't seem to find it either. I've spent hours looking around for both, am I missing something here?

---

### Post by Yezinki on 2012-11-01
> **sthitaprajna said:**
> Okay, b43sta and firmware b43 installer.

From synaptic manager.

---

### Post by sthitaprajna on 2012-11-01
The synaptic manager did not come installed. 

Maybe I can rephrase my question. Where can I get these drivers from my Windows based computer then transfer to my Ubuntu computer via usb drive. I can't download anything from my Ubuntu computer b/c it does not even connect by ethernet.

---

### Post by Yezinki on 2012-11-01
See if this works?

---

