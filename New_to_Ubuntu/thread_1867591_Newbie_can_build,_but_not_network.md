---
title: "Newbie can build, but not network"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by tombo887 on 2011-10-23
I have a home built PC currently running Ubuntu 10.04 LTS.     

I installed an Encore 802.11g wireless PCI adaptor, but the drivers will not install.
My solution was to get a LAN cable and attempt to use the network connection to share the wireless access to the web I have via AirPort on my Macbook.
Is second scenario actually possible?  Many hours are escaping me....

OR Would there be an easy way to modify the Windows drivers on the PCI card install disk to run on Linux???

Thanks.

---

### Post by LowSky on 2011-10-26
open terminal, please type ```
lspci
``` please post results.

most cards work out of the box, some need the driver, and its available form ubuntu's repos, but it needs a network connection to install. also using a newer version of Ubuntu can sometimes have the proper driver already added.

Also a normal ethernet cable would not work, you need a crossover cable for your second idea.

---

