---
title: "my usb ports are dead"
date: 2013-02-10
forum: New to Ubuntu
---

### Post by farrington on 2013-02-10
After running the executable "/simpleTest" form ARToolkit all  my usb ports are dead.How can I bring up all my usb ports with out  rebooting.(If I reboot everything works fine") (I'm using Ubuntu 12.04  x86_64) 
  This is what dmesg output:
 [ 2530.971291] simpleTest[3162] trap int3 ip:7f6cf75a6fdb sp:7fff8e7361b0 error:0 
[ 2549.995411] simpleTest[3167] trap int3 ip:7ff4d3a1dfdb sp:7fffd8939fb0 error:0 
[ 2597.303809] simpleTest[3173]: segfault at 7fd7042fe302 ip 00007fd7029a7e90 sp 00007fff1c510370 error 4 in libdricore.so[7fd7028c7000+23f000]
 [ 2597.392659] xhci_hcd 0000:00:14.0: Signal while waiting for configure endpoint command [ 2597.392700] usb 3-2: Not enough bandwidth for altsetting 0 
[ 2597.392704] xhci_hcd 0000:00:14.0: WARN Set TR Deq Ptr cmd with unknown completion code of 24. 
[ 2597.393239] xhci_hcd 0000:00:14.0: ERROR no room on ep ring 
[ 2597.393246] xhci_hcd 0000:00:14.0: ERR: No room for command on command ring 
[ 2602.397131] xhci_hcd 0000:00:14.0: xHCI host not responding to stop endpoint command.
 [ 2602.397142] xhci_hcd 0000:00:14.0: Assuming host is dying, halting host. 
[ 2602.397172] xhci_hcd 0000:00:14.0: HC died; cleaning up 
[ 2602.397244] usb 3-2: USB disconnect, device number 2 
[ 2602.489521] xhci_hcd 0000:00:14.0: Slot 1 endpoint 14 not removed from BW list!

---

### Post by sudodus on 2013-02-10
What is ARToolkit?

I suppose that you run it again after reboot, and it stops the USB ports again.  What is ARToolkit doing?

---

