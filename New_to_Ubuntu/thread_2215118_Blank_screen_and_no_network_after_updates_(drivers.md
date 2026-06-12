---
title: "Blank screen and no network after updates (drivers and kernel?)"
date: 2014-04-04
forum: New to Ubuntu
---

### Post by raulcb on 2014-04-04
This happens after a ubuntu basic updates. On Ubuntu 13.10.

I was using Nvidia propietary driver (the recomended one). The kernel now is 3.11.0-18-generic i 686. Maybe there was also a kernel update?

In the login screen, the network dialog says NO NETWORK DEVICES AVAILABLE.
After loggin in, it goes to a black screen, only with the mouse.

After a long search, because I'm just a Ubuntu user and not a command line expertise, I learned that ctrl+alt+F1 opens a dialog, so I could get some info:

[LIST]
[*]Wireless card is a Ralink RT2561/RT61 revB 802 11g 
[*]Ethernet controller: Atheros AR8121/AR8141 Gigabit or fast Ethernet 
[/LIST]
BUT BOTH APPEARS AS UNCLAIMED NETWORK

As I have no connection, I couldn't try any of the possible solutions that I've read here or at the Ubuntu Forums...

Some advice or help, please?

Thanks a lot!

---

### Post by monkeybrain20122 on 2014-04-04
Can you boot into the previous kernel? (at boot screen hold the shift key, when the boot menu appears, go to advanced options ... and choose an older kernel). If everything works in the old kernel you can be sure that it is caused by kernel update. If that is the case, just delete the updated kernel and its headers from synaptic (there are 4 packages)

---

### Post by raulcb on 2014-04-05
Thanks a lot! It was so easy! Worked! I'm on Ubuntu from 2008, and still a newby... I tryed this before because I've ridden a post, but I was unable to enter the Grub menú...

---

