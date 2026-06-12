---
title: "IP address problem with Security Onion and HomeHub"
date: 2012-05-29
forum: New to Ubuntu
---

### Post by j666gak on 2012-05-29
Hello,

The HomeHub (gateway) is set as the DHCP server, with a static DHCP reservation for the machine via MAC address.

However, EVERY time I boot the machine I have to use dhclient -r to release an IP and then dhclient again to renew the IP, this time it always gives the correct IP reservation. I have tried on the machine setting the NIC to Manual/DHCP/DHCP (Address Only) and none make any difference.

I don't why it keeps going this

Thanks

---

### Post by strask on 2012-05-29
This question made me curious and I've spent the past couple of hours trying to figure out what behavior would be different at boot time than when you issue the commands manually. But I can't figure it out. Hopefully someone else will have better luck, until then here's what I suggest:

1) Go into the Network-Manager configuration applet (System Settings -> Network -> Select the correct network -> Options) and make sure everything in there looks sane.
2) Give up and add the dhclient commands to /etc/rc.local so that they run at the end of the boot process for you.

---

