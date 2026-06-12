---
title: "SSH machine to machine - w/cross over cable"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by G4slight$ on 2008-05-06
I am attempting to administer a box by connecting it to
my ubuntu machine direclty (with a cross-over cable) and SSH'ing into it --

other box:

Management interface eth2

eth2: IP set to 10.6.6.6 
SSHd running

Crossover cable connected to Ubuntu box:

Note: all other ethernet cables on Ubuntu box disconnected, connecting from eth0

eth0 manually set to: 10.6.6.8
sSH server running

Attempt to SSH into 10.6.6.6 - No route to host 

Attempt to SSH from 10.6.6.6 to 10.6.6.8 -- no route to host -

How do I route traffic direct if I don't have a local DNS?  
I thought this SSH stuff was easy --
thanks for any help/suggestions /hate mail -
B.

---

### Post by cwgatling on 2008-05-06
First things first: can you ping from 1 machine to the other? If yes, the routing is ok.
Have you allowed the TCP 22 on your ssh server's firewall?
NMAP ('sudo apt-get install nmap') will let you see what ports are open on the server.

---

### Post by croto on 2008-05-06
Make sure you set the netmask to 255.255.255.0 on both ends. If that doesn't work, I think I would need the output of "route" and "ifconfig" on both computers.

---

### Post by timcredible on 2008-05-06
there's no routing involved here - routing is when you cross broadcast domains (ie. going from one subnet to another).  there's no DNS needed because you're not trying to resolve a name into an address.  most likely the cable is not an ethernet crossover cable (1-3, 2-6, 3-1, 6-2).  i would suggest buying a very cheap switch (probably $5US) and straight through cables and save yourself any layer 1 (cabling) issues.

---

### Post by croto on 2008-05-06
that's not entirely technically true. The computer should be connected to two subnets, the localhost subnet (127.0.0.0), and whatever other LAN you're connected to. So your host needs to do some routing decisions. When you ifconfig the NIC up, for example 
```

ifconfig eth1 192.168.1.200 netmask 255.255.255.0

```
you'll see the routing table gets a new entry:
```

192.168.1.0     *               255.255.255.0   U     0      0        0 eth1

```
which means that whenever you want to send a packet to 192.168.1.*, it should come out through the NIC eth1.

It is important that the subnet on both ends are the same, in order for each host to accept the packets coming from the other end.

---

