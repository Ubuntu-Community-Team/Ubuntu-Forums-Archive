---
title: "arp in vmware ubuntu"
date: 2011-10-10
forum: New to Ubuntu
---

### Post by chanakya_nani on 2011-10-10
ARP table in my vmware workstation 8 ubuntu is showing only either 1 or 2 addresses, whereas the same network connected to my host os windows 7 is showing a large list of the connected computer ip's. Is something wrong with ubuntu in vmware, why is it not showing all the users ip addresses in it.?

please help me with this problem.

Thanks.

---

### Post by ezramorris on 2011-10-10
> **chanakya_nani said:**
> ARP table in my vmware workstation 8 ubuntu is showing only either 1 or 2 addresses, whereas the same network connected to my host os windows 7 is showing a large list of the connected computer ip's. Is something wrong with ubuntu in vmware, why is it not showing all the users ip addresses in it.?

Hello. Welcome to Ubuntu forums!

The arp command only shows hosts which have previously been accessed. For example:

```
ezra@ezra-laptop:~$ arp
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.0.1              ether   a0:21:b7:xx:xx:xx   C                     wlan0

ezra@ezra-laptop:~$ ping 192.168.0.5
PING 192.168.0.5 (192.168.0.5) 56(84) bytes of data.
64 bytes from 192.168.0.5: icmp_req=1 ttl=128 time=38.6 ms
64 bytes from 192.168.0.5: icmp_req=2 ttl=128 time=2.21 ms
64 bytes from 192.168.0.5: icmp_req=3 ttl=128 time=2.56 ms
^C
--- 192.168.0.5 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 2.216/14.473/38.641/17.089 ms

ezra@ezra-laptop:~$ arp
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.0.5              ether   00:1e:65:xx:xx:xx   C                     wlan0
192.168.0.1              ether   a0:21:b7:xx:xx:xx   C                     wlan0
```

So the arp table only showed 192.168.0.5 after I pinged it.

Hope this helps.

---

### Post by ezramorris on 2011-10-10
By the way, if you did want to get a list of all the hosts on your local network, you can take a look at arp-scan. Install it via the Software Center or on the command line with:
```
sudo apt-get install arp-scan
```

Then you can do something like:
```
sudo arp-scan --interface=eth0 --localnet
```

You'll need to change eth0 to match your interface, found by running:
```
ip addr
```

---

