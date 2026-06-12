---
title: "Get MAC from DHCP server  (Cisco) )with IP Address"
date: 2012-03-13
forum: Programming Talk
---

### Post by aliahsan81 on 2012-03-13
Hi All,

I am going to make a script in Linux that will query DHCP server hosted on Cisco Switched for MAC ip binding. We have Vlans and we cant use ARP or Nmap. So is there any way I can achieve this.

---

### Post by aliahsan81 on 2012-03-14
Any one??

---

### Post by aliahsan81 on 2012-03-26
ANy one please help on this.

---

### Post by CynicRus on 2012-03-26
cat /proc/net/route

---

### Post by CynicRus on 2012-03-26
And use dhcp-client, for get ip from server.

---

### Post by Habitual on 2012-03-26
```
arp 
```
maybe?

---

