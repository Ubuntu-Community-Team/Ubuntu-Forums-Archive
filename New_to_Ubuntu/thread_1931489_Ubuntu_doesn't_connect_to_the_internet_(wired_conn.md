---
title: "Ubuntu doesn't connect to the internet (wired connection)"
date: 2012-02-25
forum: New to Ubuntu
---

### Post by Pnemesis on 2012-02-25
I'd appreciate your help with this issue. Tried resetting my modem by unplugging it for a few seconds, but it doesn't work. I can connect with windows, but I want to use my ubuntu remix. I can only get connected when I type this in a terminal: sudo dhclient and this shows up: 

Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlan0/00:22:5f:65:f5:a0
Sending on   LPF/wlan0/00:22:5f:65:f5:a0
Listening on LPF/eth0/00:22:68:50:a1:83
Sending on   LPF/eth0/00:22:68:50:a1:83
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPREQUEST of 190.194.109.32 on eth0 to 255.255.255.255 port 67
DHCPACK of 190.194.109.32 from 190.194.96.1
bound to 190.194.109.32 -- renewal in 9336 seconds.
marya@marya-laptop:~$ 

Thanks in advance

---

### Post by josephmills on 2012-02-25
hi there in your terminal could you you enter in ```
lspci -nn | grep [eE]thernet
```
then paste that line here please thanks

---

### Post by kimberlite on 2012-02-25
Hi,

Have you checked at your "network manager" "wired settings" "IPv4 settings" to "automatic (DHCP)" option?

HTH:

K.

---

