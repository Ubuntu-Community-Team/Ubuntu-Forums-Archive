---
title: "Bridging"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by shoaibi on 2008-08-17
Scenario:
A. Router: 10.0.0.138
B. Machine 1: 10.0.0.1 Ubuntu 8.04LTS USB Port (eth1)
   Ethernet Port (eth0) being used for bridging.
C. Machine 2: No IP. Windows XP Professional. Ethernet port.

I asked question in #ubuntu, and thanks to Flannel i got it working using iptables by following: [https://help.ubuntu.com/community/Internet/ConnectionSharing?action=show&redirect=InternetConnectionSharing#Ubuntu%20Internet%20Gateway%20Method%20(iptables](https://help.ubuntu.com/community/Internet/ConnectionSharing?action=show&redirect=InternetConnectionSharing#Ubuntu%20Internet%20Gateway%20Method%20(iptables))
Now the thing is i have installed dnsmasq and want to use that instead...
But:
```

 sudo /etc/init.d/dnsmasq restart
 * Restarting DNS forwarder and DHCP server dnsmasq                                                                                                          
dnsmasq: failed to create listening socket: Address already in use
 * failed to start
14:34:50] shoaibi@cosp-hq ~ $ cat /etc/dnsmasq.conf
interface=eth0
dhcp-range=10.0.0.10,10.0.0.25,72h 
# even tried with 192.168.0.100,192.168.0.250,72h

```

---

