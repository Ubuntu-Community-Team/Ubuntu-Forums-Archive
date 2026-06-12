---
title: "wireless router problem"
date: 2012-03-05
forum: New to Ubuntu
---

### Post by dtrapp on 2012-03-05
I have a problem with my wireless.
I just upgraded from 11.04 to 11.10 and now my wireless doesn't work.
My wireless was working in 11.04 and still works in windows 7

These are the responses I get from various commands 
**rfkill -list all**   I get no response; terminal goes back to the prompt
**iwlist**    tells me that the lo, eth1, ppo do not support scanning
**lspci -nnk | grep -iA2 net**
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard [1043:83a3]
	Kernel driver in use: r8169

Thanks for any help.

---

### Post by Diametric on 2012-03-05
Hi.

I might start here:

[https://help.ubuntu.com/11.10/ubuntu-help/net-wireless.html](https://help.ubuntu.com/11.10/ubuntu-help/net-wireless.html)

See if that gets you pointed in the right direction.

Good luck.

---

