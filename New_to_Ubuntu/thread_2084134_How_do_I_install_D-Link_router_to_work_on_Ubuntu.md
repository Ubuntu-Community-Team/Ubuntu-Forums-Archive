---
title: "How do I install D-Link router to work on Ubuntu"
date: 2012-11-14
forum: New to Ubuntu
---

### Post by Scomeau on 2012-11-14
I have hooked everything up and the router is working fine with the  modem but as soon as I try to install it on the computer through URL  address the book gave me, it won't find the IP address of the computer  or anything it needs to find :( I have been using Ubuntu for a while but still don't understand much. Any help would be nice :)

---

### Post by Gone fishing on 2012-11-14
You've plugged the router into the PC? Go to network manager remove any wired connections or set to DHCP in IPv4 settings IPv6 set to ignore. Plug in your router and check you have an address with ```
ifconfig
``` in a terminal. If you do all should be well. If not set a manual address in the same range as the router i.e if the router is 192.168.0.1 set the PC to 192.168.0.2 and see if you can ping the router ```
ping 192.168.0.1
```. If you can all should be well, if not reset the router to default by pressing the hidden button and repeat the above steps.

---

### Post by Bashing-om on 2012-11-14
nother thought -> I have cable modem and when I initially installed the router, would not connect. I had to use the "clone router MAC address" option ,in the router, for my isp to accept the connection.
[INDENT]just try'n to help <== BDQ

[/INDENT]

---

### Post by oldos2er on 2012-11-14
Closed, duplicate here: [http://ubuntuforums.org/showthread.php?t=2084138](http://ubuntuforums.org/showthread.php?t=2084138)
Please don't open more than one thread for each issue or question you may have.

---

