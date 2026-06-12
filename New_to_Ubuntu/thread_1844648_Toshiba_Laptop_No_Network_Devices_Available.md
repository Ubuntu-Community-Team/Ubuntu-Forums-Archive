---
title: "Toshiba Laptop: No Network Devices Available"
date: 2011-09-15
forum: New to Ubuntu
---

### Post by Bunnies on 2011-09-15
Hi, I just installed Ubuntu on my Toshiba Laptop but for some reason it will not let me access the Internet... or even my router.

I previously encountered this problem and resolved it by plugging in the ethernet cable to the router/laptop. This did not fix the current problem, however and I wonder if anyone else knows what it going on with it?

Any help would be appreciated. Thanks

---

### Post by Bunnies on 2011-09-15
I just did:
> lspci | grep Ethernet
06:00.0 Ethernet controller: Atheros communications AR8152 v1.1 Fast Ethernet (rev c1)

I attempted:
> sudo rmmod sky2
[sudo] password for ubuntu:
Error: Module sky2 does not exist in /proc/modules
Does Toshiba simply not have compatible drivers with Linux?

---

### Post by P05TMAN on 2011-09-15
What's the model of the Toshiba

---

