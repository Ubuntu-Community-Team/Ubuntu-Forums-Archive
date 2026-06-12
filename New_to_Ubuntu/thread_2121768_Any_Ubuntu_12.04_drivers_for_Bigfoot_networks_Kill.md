---
title: "Any Ubuntu 12.04 drivers for Bigfoot networks Killer Wireless-N 1103 (3 antenna)"
date: 2013-03-03
forum: New to Ubuntu
---

### Post by 007casper on 2013-03-03
Any drivers for Bigfoot networks Killer Wireless-N 1103 (3 antenna)

OS - Ubuntu 12.04

please advise. Thank you.

---

### Post by carl4926 on 2013-03-03
Can you post result of
```
lspci -nnk | grep -iA2 net
```

---

### Post by 007casper on 2013-03-03
lspci -nnk | grep -iA2 net
> 
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9300 Wireless LAN adaptor [168c:0030] (rev 01)
	Subsystem: Bigfoot Networks, Inc. Killer Wireless-N 1103 Half-size Mini PCIe Card [AR9380] [1a56:2001]
	Kernel driver in use: ath9k
	Kernel modules: ath9k
04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8161 Gigabit Ethernet [1969:1091] (rev 10)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1477]

---

### Post by carl4926 on 2013-03-03
Are you sure your wireless isn't working
What is showing in the Network Manager?

---

### Post by carl4926 on 2013-03-03
Some info that might be relevant
[http://linuxwireless.org/en/users/Drivers/ath9k](http://linuxwireless.org/en/users/Drivers/ath9k)

---

### Post by 007casper on 2013-03-03
It works... but the connection constantly drops.  And I am pretty much next to the router.  It is weird.  When I was on windows 8, it flew.

thanks for the link.  I am checking it out.

---

### Post by carl4926 on 2013-03-03
> **007casper said:**
> It works... but the connection constantly drops.  And I am pretty much next to the router.  It is weird.  When I was on windows 8, it flew.

thanks for the link.  I am checking it out.

You might check compat-wireless
[http://paste.opensuse.org/78916162](http://paste.opensuse.org/78916162)

---

### Post by 007casper on 2013-03-03
thank you so much

---

