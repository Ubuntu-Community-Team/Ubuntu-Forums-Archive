---
title: "Find laptop's IP address"
date: 2013-12-13
forum: New to Ubuntu
---

### Post by Cyber72 on 2013-12-13
How can I find the IP address assigned to my laptop? I can't connect to the internet and I think my BT home hub 2 may be blocking it. Is the laptop's assigned IP address a permanent address?

Please note I am not asking to find my IP address I am trying to find my laptop's IP address.

---

### Post by deadflowr on 2013-12-13
```
ifconfig
```
should be in there somewhere.

---

### Post by asus-user on 2013-12-13
> **Cyber72 said:**
> How can I find the IP address assigned to my laptop? I can't connect to the internet and I think my BT home hub 2 may be blocking it. Is the laptop's assigned IP address a permanent address?

Please note I am not asking to find my IP address I am trying to find my laptop's IP address.

in Terminal:
```
nm-tool
```

this gives the information in more understandable fashion and in detail :)

the assigned IP address is not Permanent if it was assigned by DHCP server. If you want to have the same IP and you know how it should look like (network mask and gateway), you can assigned it manually every time you connect to a different network (static IP), and this has nothing to do with your "real IP" over the Internet.

---

### Post by Cyber72 on 2013-12-13
Many thanks

---

