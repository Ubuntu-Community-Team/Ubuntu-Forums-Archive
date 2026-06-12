---
title: "[SOLVED] Problem Connecting to Internet"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by getitright on 2008-10-10
My desktop was set up to dual boot XP and Ubuntu and I had no problems with connecting to the internet via an eth0 cable and an ADSL router. I then decided to remove XP and run the machine solely on Ubuntu. Since re-installing Ubuntu I am unable to connect to the internet.

I have tried both DHCP and Static IP Address in Network Settings to no avail. I am still able to connect wirelessly from a laptop.

Can anyone advise me please?

---

### Post by nothingspecial on 2008-10-10
Open a terminal and post the output of

```
lspci -v
```

---

### Post by dburnett77 on 2008-10-10
> **getitright said:**
> My desktop was set up to dual boot XP and Ubuntu and I had no problems with connecting to the internet via an eth0 cable and an ADSL router. I then decided to remove XP and run the machine solely on Ubuntu. Since re-installing Ubuntu I am unable to connect to the internet.

I have tried both DHCP and Static IP Address in Network Settings to no avail. I am still able to connect wirelessly from a laptop.

Can anyone advise me please?

Here's some info in the Ubuntu Doc section that may help:

[https://help.ubuntu.com/8.04/internet/C/connect.html](https://help.ubuntu.com/8.04/internet/C/connect.html)

---

### Post by getitright on 2008-10-10
Output of lspci -v:

01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
	Subsystem: ASUSTeK Computer Inc. Unknown device 004d
	Flags: bus master, 66MHz, medium devsel, latency 64
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	Memory at ff0e0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8026
	Flags: bus master, medium devsel, latency 64, IRQ 20
	I/O ports at d800 [size=256]
	Memory at ff9ffc00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

02:0a.0 Communication controller: Intel Corporation 536EP Data Fax Modem
	Subsystem: Intel Corporation Unknown device 1000
	Flags: bus master, medium devsel, latency 64, IRQ 5
	Memory at ff400000 (32-bit, non-prefetchable) [size=4M]
	Capabilities: <access denied>

---

### Post by dburnett77 on 2008-10-12
Just a note:
Ubuntu 8.10 is a bit flakey on NIC's right now, for some reason they've limited conncectivity because of harmful interaction against firmware.

8.04.1 doesn't display this behavior.

If that's not it; and you want to display more info, try:

sudo ifconfig

and 

sudo ifconfig eth0  *usually the std interface from what you've listed, thusfar.

If you get a MAC address, that's good.  If not, you've got a controller that you'll have to most likey get a wrapper for.
But, since it worked before your re-install, I'd say there's something screwey in the
/etc/netork/interfaces
configuration.

The two listed commands will yield more info.

---

