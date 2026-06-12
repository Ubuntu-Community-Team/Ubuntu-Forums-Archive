---
title: "Network interface disappears on laptop"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by timandjulz on 2008-09-16
Occasionally I will boot my desktop or laptop and the network interface will not connect.  "Network Settings" does not even show the network adapter.

I have tried ifup eth0 but it gives me this output:
```
eth0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
wmaster0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up eth0.

```

I cat'd /etc/network/interfaces and the device is defined.

Since this happens to both my desktop and laptop but not at the same time, there must be something going on with Ubuntu.

On my desktop, the problem occurs when I boot up.  On my laptop (at least this last time) it happened when I was running wireless and connected the network cable.

Any ideas?  Any help is appreciated!
Tim

---

### Post by Idefix82 on 2008-09-16
What does
```
lshw -C network
```
give you?

---

### Post by timandjulz on 2008-09-16
I am not sure if lshw acts different than lspci.  I ran lspci while the laptop was acting up and it told me I had an Intel 82573L gigabit controller.

I had to reboot and it is working now.  lshw lists the same network adapter.

So same problem exists... eventually I will reboot and my network adapter won't come up.  It happens just enough to piss me off.  :-)

---

