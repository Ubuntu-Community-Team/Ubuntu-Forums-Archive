---
title: "Set fix IP for Ubuntu running on VMWare Player"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by peterlauri on 2008-11-04
Hi,

How can I setup so that the Ubuntu that I have running on VMWare Player always gets the same IP? I use the NAT method for my network interface.

/Peter

---

### Post by dustman on 2008-11-04
So, you're asking whether how to set the same IP address in Ubuntu (a static IP address) or how to set VMWare to assign the same IP address to the Ubuntu machine?

Cheers!

Radu

---

### Post by wizard10000 on 2008-11-04
> **peterlauri said:**
> How can I setup so that the Ubuntu that I have running on VMWare Player always gets the same IP? I use the NAT method for my network interface.

This is easy - create a MAC reservation for the VM on your router.

First, get the MAC address of the VM - ifconfig will give you this.

Then, assign that MAC address a static IP address on your router - note that some routers won't allow you to do MAC reservations, though - I've seen Linksys and Belkin routers that wouldn't but in those cases I just set the IP lease to 'forever'.

Another option is to give the VM a static IP that's outside the DHCP scope of the router but on the same subnet.

Good luck!

---

### Post by Sarmacid on 2008-11-04
You have to edit your **/etc/network/interfaces** file to read like this
```
auto eth0
iface eth0 inet static
        address 172.16.1.2
        netmask 255.255.255.0
        network 172.16.1.0
        broadcast 172.16.1.255
        gateway 172.16.1.1
```

Just need to adjust it to your needs.

---

### Post by dustman on 2008-11-04
maybe he doesn't have a router :).

I had a similar problem since on my server I am running Ubuntu in VMWare, with windows being the host operating system. I don't have a router, but a static IP address. What I had to do was to forward the traffic coming on port 80 using a 3rd party software, then I set a static IP address from Ubuntu (instead of DHCP), then forward the traffic in VMWare towards the Ubuntu virtual machine using [[COLOR="Blue"]this[/COLOR]]("http://benrobb.com/2007/01/20/howto-port-forward-to-your-virtual-machine/") method (and to the static IP I set from Ubuntu).

So, peterlauri, please answer what's your problem...in details :D

---

### Post by superprash2003 on 2008-11-04
presuming you want to setup static ip.. simple way to do this is [http://prash-babu.blogspot.com/2008/09/internet-works-on-one-pc-but-not-on_12.html](http://prash-babu.blogspot.com/2008/09/internet-works-on-one-pc-but-not-on_12.html)

---

