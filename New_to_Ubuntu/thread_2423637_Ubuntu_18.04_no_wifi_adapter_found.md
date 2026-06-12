---
title: "Ubuntu 18.04 no wifi adapter found"
date: 2019-07-26
forum: New to Ubuntu
---

### Post by tatusaalasti on 2019-07-26
when i try to connect to my wifi on my ubuntu client, all i see is 'no wifi adapter found, make sure you have a wifi adapter plugged and turned on'. i have tried following many tutorials on fixing this problem, but because i have no connection i can't install any packages. thanks in advance

---

### Post by SeijiSensei on 2019-07-26
Some machines like an HP laptop I own have a switch that turns the wifi off and on. On that machine it's in a location where I can accidentally turn it off during normal use.  Take a look at the support documents for your machine and see if you have a similar switch.

---

### Post by tatusaalasti on 2019-07-26
nope, wifi is working on my windows partition. also it's a hp destop, ryzen 5 2400g

---

### Post by poorguy on 2019-07-26
Sometimes to get the needed device drivers you need to connect to a wired Ethernet and then run the software updater and see if a driver for your wireless adapter downloads and installs.

---

### Post by SeijiSensei on 2019-07-26
Open a terminal and type "lspci". Do you see any entries that look like this?

```
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000 [Condor Peak]
```

Not that specific model, of course, but a "network controller" that is described as a wireless device.

---

