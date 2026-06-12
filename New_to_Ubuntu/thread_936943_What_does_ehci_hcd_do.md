---
title: "What does ehci_hcd do ?"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by oldtechy on 2008-10-03
I have loaded Ubuntu 8.04 as a second system on an existing pc. The base unit runs an MSI 915P/G Neo2 board with a 3 GHz pentium, 512MHz mem and a sata disc. The system is up and running but a few mysteries remain.
   Firstly, the usb would not respond to flash memory sticks until I read a hint to do 'rmmod ehci_hcd'. Magic, it runs fine, but I have to do this each time I boot up. On advice, I tried blacklisting the module 'ehci_hcd' but this does not help at all. It seem funny that one has to install a module and then remove it to get the usb to work. Any suggestions please.

---

### Post by cmnorton on 2008-10-03
Here's a starting place:

[http://ubuntuforums.org/showthread.php?t=89266](http://ubuntuforums.org/showthread.php?t=89266)

---

