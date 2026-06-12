---
title: "bash script: alive host?"
date: 2012-03-07
forum: Programming Talk
---

### Post by conradin on 2012-03-07
Hi everyone, 
Im looking for a function, or program I can call via a script that will allow me to get the hostname, and IP of only alive hosts. When by alive, I mean hosts that are on the network and responding to ping type requests. When I poll the Domain name server, I get names and addresses which may not be currently active. 
Does anyone have a good idea for this?

---

### Post by Lars Noodén on 2012-03-07
Please give an example of what kind of input you want to provide and what kind of output you expect.

---

### Post by ofnuts on 2012-03-07
> **conradin said:**
> Hi everyone, 
Im looking for a function, or program I can call via a script that will allow me to get the hostname, and IP of only alive hosts. When by alive, I mean hosts that are on the network and responding to ping type requests. When I poll the Domain name server, I get names and addresses which may not be currently active. 
Does anyone have a good idea for this?
In theory this should be enough:
- "ifconfig <interface>" e.g. "ifconfig eth0" of "ifconfig wlan0"
- Retrieve the broadcast address (Bcast:")
- "ping -b  {broadcast_address} and check who answers

In practice due to firewalls plenty of hosts won't answer.

---

### Post by Lars Noodén on 2012-03-07
> **ofnuts said:**
> In theory this should be enough:
- "ifconfig <interface>" e.g. "ifconfig eth0" of "ifconfig wlan0"
- Retrieve the broadcast address (Bcast:")
- "ping -b  {broadcast_address} and check who answers


That looks interesting but for me it only returns the ping of a single host instead of what should be available on the subnet.  

What about [nmap](http://manpages.ubuntu.com/manpages/oneiric/en/man1/nmap.1.html)?

```

sudo nmap -sP 192.168.100.1-255

```

---

### Post by conradin on 2012-03-12
Thanks Lars,
nmap actualy works quiet well for what Im trying to do, I'll use that.

---

