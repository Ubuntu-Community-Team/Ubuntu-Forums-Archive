---
title: "find the IP of the DHCP server"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by neill on 2008-09-23
hi

my ubuntu box eth0 interface gets its IP from a DHCP server on my LAN

short of guessing or pinging ranges, what command can i enter in a terminal to get the IP of that DHCP server ?

ta

/neill

---

### Post by perlluver on 2008-09-23
> **neill said:**
> hi

my ubuntu box eth0 interface gets its IP from a DHCP server on my LAN

short of guessing or pinging ranges, what command can i enter in a terminal to get the IP of that DHCP server ?

ta

/neill

If I read this right, you can type ifconfig in the terminal to get the IP address.  If not feel free to correct me.

---

### Post by mrtomcef on 2008-09-23
open terminal and type ifconfig.
you should get a readout like so:
> tom@tom-laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:15:af:6b:a3:2f  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fe6b:a32f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:123052 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39868 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:111718090 (106.5 MB)  TX bytes:4584510 (4.3 MB)

if I rememer correctly the Bcast is the IP of your DHCP server/router

---

### Post by neill on 2008-09-23
ifconfig gives me the IP of eth0, the broadcast IP and the netmask but not the IP of the DHCP server that actually 'handed out' that address

it's *that* DHCP IP I'm after

(the stuff that in the advanced tab in the network interface tab in XP)

ta

/neill

---

### Post by neill on 2008-09-23
i thought the broadcast address is the broadcast packets to all IPs on the subnet (?)

/neill

---

### Post by bodhi.zazen on 2008-09-23
LOL

```
sudo dhclient
```

You can also :

```
tail -n 15 /var/lib/dhcp3/dhclient.*.leases
```

where * = your interface, eth0 in the OP request.

---

### Post by neill on 2008-09-23
See that what we fumbling n00bs need ..

The BIG boys dun step'd up with **the** answer !

:lolflag:

---

