---
title: "Network Interface - Allow Virtualbox Only"
date: 2012-06-18
forum: New to Ubuntu
---

### Post by jkurtisr32 on 2012-06-18
What's up,

So I've got my server running Virtualbox, and one of the virtual machines within the server is running my router software (DD-WRT). The server and the VM both have two network interfaces:

For the server:
eth0 and eth1

For the VM:
WAN and LAN

Everything is working fine at this point, except that I am still able to access the server from eth0 (which is the same interface as WAN on the VM). For security, I only want to be able to access the VM from eth0.

Is it possible to only allow Virtualbox to talk to eth0 and block all other traffic?

Thanks,
Kurt

---

### Post by jkurtisr32 on 2012-06-19
> **jkurtisr32 said:**
> What's up,

So I've got my server running Virtualbox, and one of the virtual machines within the server is running my router software (DD-WRT). The server and the VM both have two network interfaces:

For the server:
eth0 and eth1

For the VM:
WAN and LAN

Everything is working fine at this point, except that I am still able to access the server from eth0 (which is the same interface as WAN on the VM). For security, I only want to be able to access the VM from eth0.

Is it possible to only allow Virtualbox to talk to eth0 and block all other traffic?

Thanks,
Kurt

Well **** me, I solved the issue. Apparently, through some kind of black magic, the host server (eth0) interface does NOT need to be connected in order for the VM equivalent (WAN) to work, although (obviously) the cable still needs to connected.

I still think that this is completely ****** that this can work.

---

