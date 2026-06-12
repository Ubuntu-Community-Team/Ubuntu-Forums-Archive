---
title: "Ethernet not working"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by TheShagg on 2008-09-08
I am trying to connect my other box to the internet using ifdown and ifup, while the ubuntu live CD is running with the wired mode set to DHCP.   Upon ifup, it can't get a DHCP lease.  This computer I am on right does it just fine on the same live CD, with the same network cable.  The two computers are on the same desk, next to each other.

The computer that is failing to DHCP has an ECS  p4vxasd2+  motherboard (known to be a pain, even for windows users).  I am trying to use its on-board Ethernet interface.

I assume this is a driver issue, but I'm a newb and I don't know what to do next :confused:

Thanks for any help.

---

### Post by iaculallad on 2008-09-08
On the computer that's failing to obtain an IP address, try running the commands below:

```
sudo dhclient -r
sudo dhclient
sudo /etc/init.d/networking restart
```

---

### Post by TheShagg on 2008-09-08
Same problem: "No DHCPOFFERS received"

---

### Post by iaculallad on 2008-09-08
> **TheShagg said:**
> Same problem: "No DHCPOFFERS received"

First start is try to configure a static IP for that machine to eliminate other problems.

---

