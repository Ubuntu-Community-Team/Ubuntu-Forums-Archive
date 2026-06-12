---
title: "VirtualBox Virtual Monitor"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by turbotuba on 2008-06-16
I can't figure out how to change the monitor size in my VM with VirtualBox. 
I have a 19" Real Monitor and I get about an 8" Virtual Monitor.  Can anyone help me make the Virtual monitor larger? My host machine is Ubuntu 8.04 and the VM i'm running is WinXP.

---

### Post by shifty_powers on 2008-06-16
can you not just right click on the desktop, go properties, then steeings, iirc, and set it to what you want?

I have the same set up, and i just adjust the resolution within windows...

---

### Post by NikoC on 2008-06-16
For better graphics performance you might want to install the Virtualbox guest additions:
Start up the virtual machine in a window
Under devices: Install guest additions
Your virtual os has to be completely booted and I think an internet connection is also necessary.

Hope this helps you out.

Cheers.

---

### Post by Jensss on 2008-06-16
Install VB Guest Additions and try Ctrl+F in the virtual machine.

---

