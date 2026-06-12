---
title: "Problem with wireless card after upgrade"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by waterspider on 2008-04-29
i just upgrade recently from 7.10 to 8.04 but i cant find my wireless network card, and when i run the lspci command it gives me this output-

00:0c.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. WL-103b Wireless LAN PC Card
	Flags: bus master, fast devsel, latency 32, IRQ 11
	Memory at e4000000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
pls help me

---

### Post by kesman on 2008-04-29
Check system->administration->hardware drivers. You may need to install a restricted driver for your wlan.

---

### Post by waterspider on 2008-04-29
i have done that but it will say" NO PROPRIETORY ARE IN USE IN THIS SYSTEM

---

