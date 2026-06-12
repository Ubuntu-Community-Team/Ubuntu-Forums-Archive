---
title: "how to connect to wireless network?"
date: 2012-06-27
forum: New to Ubuntu
---

### Post by madmathman on 2012-06-27
Okay, this sounds like a newbie question.  

I installed ubuntu on a laptop.  I tried to connect to our home wireless network.  Yes, I selected our own network and used the correct password.  After about 3 seconds, the computer tells me that the network is disconnected.

Let's assume that the network and modem work, since I'm able to connect via another OS.

But back to ubuntu.  I opened up some of the widgets to edit the network configuration, and didn't know which of the details to start tweaking.  So I left them untweaked.

Any good ideas?

Thank you!

madmathman

---

### Post by ubudog on 2012-06-27
Hi madmathman, could you please post the output of:
```
sudo lspci -v
```
(run that in a terminal)

---

### Post by wildmanne39 on 2012-06-27
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by madmathman on 2012-06-28
Two people answered me.  Thank you.  My responses to both of them are here.

1.
ubudog asked me to post the response to sudo lspci -v
You probably don't want ALL of that response. There's a lot.
Here are the parts I expect you want.

12:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)
Subsystem: Dell Device 000e
Flags: bus master, fast devsel, latency 0, IRQ 17
Memory at fbb00000 (64-bit, non-prefetchable) [size = 16K]
Capabilities: [40] Power management version 3
Capabilities: [58] Vendor specific information: Len=78 <?>
Capabilities: [48] MSI: Enable- Count = 1/1 Maskable- 64bit+
Capabilities: [d0] Express endpoint, MSI 00
Capabilities: [100] Advanced error reporting
Capabilities: [13c] Virtual channel
Capabilities: [160] Device serial number 00-00-cb-ff-ff-11-f0-7b
Capabilities: [16c] power budgeting <?>
Kernel driver in use: brcmsmac
Kernel modules: bcma, brcsmac

13:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI E
xpress Gigabit Ethernet Controller (rev 03)
Subsystem: Dell Device 043f
Flags: bus master, fast devsel, latency 0, IRQ 45
I/O ports at e000 [size=256]
Memory at d0b04000 (64-bit, prefetchable) [size=4K]
Memory at d0b00000 (64-bit, prefetchable) [size=16K]
Expansion ROM at fba00000 [disabled] [size=128K]
Capabilities: [40] Power Management version 3
Capabilities: [50] MSI: Enable+  Count=1/1  Maskable- 64bit+
 Capabilities: [70] Express Endpoint, MSI 01
 Capabilities: [ac] MSI-X: Enable- Count=4 Masked-
 Capabilities: [cc] Vital Product Data
 Capabilities: [100] Advanced Error Reporting
 Capabilities: [140] Virtual Channel
 Capabilities: [160] Device Serial number 03-00-00-00-68-4c-e0-00
Kernel driver in use: r8169
Kernel modules: r8169
 

2.
Now for the response from wildmanne39.

cat /etc/lsb-release; uname-a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux ted-Vostro-3300 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux

lspci
(See content above, answering previous question)

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 004: ID 0c45:6450 Microdia

iwconfig
lo no wireless extensions.
eth0 no wireless extensions.
wlan0 IEEE 802.11abgn ESSID:off/any
Mode:managed Access Point: not-Associated Tx-Power=19 dBm
Retry long limit:7  RTS thr:off  Fragment thr:off
Power Management:off

rfkill list all
0: dell-wifi:Wireless LAN
soft blocked: no
hard blocked: no
1: phy0: Wireless LAN
soft blocked:no
hard blocked:no

lsmod
(There are plenty of these.  Which ones do you want? I'll list the ones that look likely.)
bnep           17923   2
rfcomm       38408   0
bluetooth   148839   10 bnep,rfcomm


Thank you!

madmathman

---

### Post by mapes12 on 2012-06-28
Pop this into a Google search and you will see many fixes:-

**broadcom corporation bcm43224 ubuntu**

---

### Post by wildmanne39 on 2012-06-28
Hi, I want to see all of:
```
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

