---
title: "Install BCM4312 Network Controller Drivers"
date: 2012-02-04
forum: New to Ubuntu
---

### Post by ebeth on 2012-02-04
I've tried to do this myself, but I'm stumped.

I've upgraded my friend's Dell A90n Netbook to Ubantu 11.10.  The upgrade went great - I ended up overwriting the previous Ubantu version. 

The only issue I still have is I cannot connect it to a wireless network. I'm not sure what drivers/firmware it needs and, to make things even more interesting, I'll need to download the software on one computer (with working wireless) to the offending netbook.

This is the information on the controller:

                                  03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)  
     Subsystem: Broadcom Corporation Device [14e4:04b5]  
     Flags: bus master, fast devsel, latency 0, IRQ 17  
     Memory at f0200000 (64-bit, non-prefetchable) [size=16K]  
     Capabilities: <access denied>  
     Kernel driver in use: b43-pci-bridge  
     Kernel modules: ssb  
 

 04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)  
     Subsystem: Dell Device [1028:02b2]  
     Flags: bus master, fast devsel, latency 0, IRQ 43  
     I/O ports at 2000 [size=256]  
     Memory at f0610000 (64-bit, prefetchable) [size=4K]  
     Memory at f0600000 (64-bit, prefetchable) [size=64K]  
     [virtual] Expansion ROM at f0620000 [disabled] [size=128K]  
     Capabilities: <access denied>  
     Kernel driver in use: r8169  
     Kernel modules: r8169  
  
What drivers do I need?  What is the easiest way to get them installed?

---

### Post by PhibreOptix on 2012-02-04
Have you gone into additional drivers and activated the STA driver if it's there?

---

### Post by ebeth on 2012-02-06
Got it!  Tried a mobile wireless card to get online.  It worked, then I was able to update and get the additional drivers.

---

