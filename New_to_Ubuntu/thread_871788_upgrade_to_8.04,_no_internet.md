---
title: "upgrade to 8.04, no internet"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by MDF-3 on 2008-07-27
Upgraded to 8.04 can't connect to net, error firefox can't find server at mozilla. I have dsl ethernet, what is the normal set up thanks, beginner.

---

### Post by northern lights on 2008-07-27
> **MDF-3 said:**
> Upgraded to 8.04 can't connect to net, error firefox can't find server at mozilla. I have dsl ethernet, what is the normal set up thanks, beginner.
Are you behind a router or directly behind a dsl modem?

Can you post the output of ```
sudo lshw -C network and 
``````
ifconfig
```
Thank you.

---

### Post by MDF-3 on 2008-07-27
dsl modem no router

---

### Post by northern lights on 2008-07-27
Run ```
sudo dhcpclient eth0
```If that doesn't help, please post the requested outputs.

---

### Post by MDF-3 on 2008-07-27
Hi, sudo dhclient code says error no such device, siocsif no such device, etho error while getting interface flags no such device, bind socket to interface no such device. What device? By the way thanks for your help and time, i think i'm sorry i upgraded it was humming along just fine yesterday!

---

