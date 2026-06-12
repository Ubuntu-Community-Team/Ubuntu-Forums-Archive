---
title: "how to get a TP-Link TL-WN727N wireless USB adapter driver on ubuntu 12.04"
date: 2014-07-23
forum: New to Ubuntu
---

### Post by dardan2 on 2014-07-23
[COLOR=#000000]Hey guys. I'm new Ubuntu , I have a TL-WN727N wireless [/COLOR][COLOR=#009900 !important]_USB adapter_[/COLOR][COLOR=#000000] for my desktop and I can't get it to work. Please give me an advice ... thanku [/COLOR]:p

---

### Post by oldrocker99 on 2014-07-23
OK, you have a little work to do. Download the Windows driver for your adapter. Then, open a file manager and right-click the .exe file, and select "Extract here."

Then open a terminal and type
```
sudo apt-get install ndiswrapper dkms
```

Once it's installed, open it (it may be called "Windows Wireless Drivers"), and point it to the .inf file you extracted. It will link the driver to the kernel. You do need to reboot, then you can find out if the adapter is working. Dkms is installed to make kernel upgrades hassle-free, by the way.

Note that this **may not work**; some adapters work great with ndiswrapper and some don't. I ended up getting an Atheros adapter for my desktop box, since it is 100% Linux-compatible and needs no drivers.

Good luck! I hope it does work for you.

---

