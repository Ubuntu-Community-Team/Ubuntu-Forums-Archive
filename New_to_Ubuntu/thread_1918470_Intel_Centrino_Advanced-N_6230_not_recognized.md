---
title: "Intel Centrino Advanced-N 6230 not recognized"
date: 2012-02-01
forum: New to Ubuntu
---

### Post by chaoticmoss on 2012-02-01
I'm running Ubuntu 10.04 via Wubi and my Intel Centrino Advanced-N 6230 wireless card seems not to be recognized. I've found threads talking about this issue but I don't understand what I'm supposed to do. I can't find drivers for it.

I did this:
sudo apt-get install linux-backports-modules-wireless-lucid-generic
because the internet told me to but it seems not to have had an effect.

Please help!? I'd really appreciate it.

---

### Post by sudodus on 2012-02-01
> **chaoticmoss said:**
> I'm running Ubuntu 10.04 via Wubi and my Intel Centrino Advanced-N 6230 wireless card seems not to be recognized. I've found threads talking about this issue but I don't understand what I'm supposed to do. I can't find drivers for it.

I did this:
sudo apt-get install linux-backports-modules-wireless-lucid-generic
because the internet told me to but it seems not to have had an effect.

Please help!? I'd really appreciate it.
Try a new version of Ubuntu: Make a boot CD or USB drive and test if it works when you boot from that. Do not install until you know if it works.

The best method is to use the built-in drivers in the kernel, and new kernels have drivers for new cards or chips. An alternative is to use windows drivers via ndiswrapper, but you 'must be lucky' to get a stable connection that way.

There is a lot of information about wifi on the internet for example

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

[http://www.howtogeek.com/howto/43752/how-to-install-a-wireless-card-in-linux-using-windows-drivers/](http://www.howtogeek.com/howto/43752/how-to-install-a-wireless-card-in-linux-using-windows-drivers/)

---

