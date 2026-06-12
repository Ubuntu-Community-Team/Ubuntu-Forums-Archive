---
title: "Belkin wireless problems"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by drkemprd on 2008-07-11
I searched around and installed the software through the package manager.. Still no wireless
 I get this:
06:00.0 Ethernet controller: Belkin Unknown device 701f (rev 20)
	Subsystem: Belkin Unknown device 701f
	Flags: medium devsel, IRQ 11
	I/O ports at 1c00 [disabled] [size=256]
	Memory at 1c000000 (32-bit, non-prefetchable) [disabled] [size=512]
	Capabilities: <access denied>
The power light on the card isn't on.. 
Help anyone?

---

### Post by drkemprd on 2008-07-11
and I'm running Xubuntu 8.04.1

---

### Post by ubume2 on 2008-07-11
What kind of wireless device do you have? A card? USB device? What is the device number?

Report the results of iwconfig.

> **drkemprd said:**
> I searched around and installed the software through the package manager.. Still no wireless


What software did you install?

---

### Post by drkemprd on 2008-07-11
iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

Belkin fsd7010 laptop wireless card.. I installed ndistk,ndiswrapper-common, and ndiswrapper-utils-1.9 through the package manager..

---

### Post by drkemprd on 2008-07-11
I got it, had the wrong driver installed...

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"1121"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:F8:40:16:8C   
          Bit Rate=54 Mb/s   Tx-Power:46 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:100/100  Signal level:-31 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by ubume2 on 2008-07-12
So do you have wireless now?

---

