---
title: "how to create a firewall / dhcp box using Ubuntu?"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by Dugals on 2012-01-31
Hi
I want to use a laptop i have as a firewall, dhcp server etc.
Hopefully someone might be able to point me in the right direction.
 
the plan is to have the modem connected to the laptop's internal NIC, have it run as a DHCP server and have a switch connect to a gigabit PCcard that i have bought. alowing me to create VLAN's and assign ports on my managed switch - (like for the WAP) so i can seperate, control and monitor traffic.
 
I had some trouble getting PFsence on the laptop, though that sounds like it would be what i am after.
 
are there prgrams that will do the same job under ubuntu ? it seems stripped down to me, it will only allow one NIC to be active at a time and there does not seem to be many options for them.

---

### Post by Lars Noodén on 2012-01-31
You should be able to do that with Ubuntu.  I would suggest starting with Ubuntu Server edition since you will not need a GUI.  For DHCP, I would recommend highly looking at [dnsmasq](http://thekelleys.org.uk/dnsmasq/doc.html) since it is so easy to set up.

---

### Post by Cheesemill on 2012-01-31
You could set everything up yourself but it would be a lot easier to go with one of the distros specifically designed for this purpose.

I use [SmoothWall]("http://www.smoothwall.org/") for the virtual network on my VM host, I've also used it at several remote offices that I used to administrate.

You could also look at [Zentyal]("http://www.smoothwall.org/") (which is based on Ubuntu 10.04 LTS) if you want more features.

---

