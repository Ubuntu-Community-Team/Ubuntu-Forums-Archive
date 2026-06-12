---
title: "How to find the IP-ADRESS of a machine using the MAC-ADDRESS within a Subnet"
date: 2009-05-19
forum: Programming Talk
---

### Post by codingfreak on 2009-05-19
Hi

Is there any tool or command where I can track down the IP-ADDRESS of a machine within the subnet using its MAC-ADDRESS ???

---

### Post by stroyan on 2009-05-19
You might find it in your system's ARP table.
grep $MAC /proc/net/arp
or
arp -n | grep $MAC

---

### Post by cdenley on 2009-05-19
```

sudo apt-get install arp-scan
sudo arp-scan 192.168.0.1/24|grep -i xx:xx:xx:xx:xx:xx

```

---

### Post by codingfreak on 2009-05-25
How can I update the ARP list ... ??

If I broadcast by using ping command as shown below 

> ping -b 192.168.1.225

Then will my arp list get updated with new active ip-addresses in the network ??

---

