---
title: "I have 2 network interfaces should I have one or two dhcp client instances"
date: 2014-11-28
forum: New to Ubuntu
---

### Post by dvks on 2014-11-28
I run Ubuntu 12.04, with 2 network interfaces connected to two networks, each network has its own DHCP server (on the router).
My networking is controlled by the Network-Manager. The problem is that it is not consistent, sometimes I can see that it started two instances of the dhclient dhcp client each instance has its own leases file on /var/lib/dhcp but other times I can see only one instance and the leases file may have lease for both interfaces or only one of them. 
I verified that the /etc/network/interfaces file does not have any references to the interfaces and the /etc/NetworkManager/NetworkManager.conf    has the lines:  
[ifupdown]
managed=true

My questions:
1. Should I have multiple instances of the dhclient one per each network created/managed by the network manager
2. How can I force the network manager to regenerate/update the dhcp clients in case one is missing  
3. running the command:  "sudo dhclient -x"    or      "sudo dhclient -r "    doesn't have any effect and it doesn't stop or restart the dhclient instace(s) is there a way to stop or restart the dhcp client and force the dhcp server to generate a new lease?

---

### Post by nerdtron on 2014-11-28
Why do you connect to two different networks? I think the problem of inconsistency here is the default route which both DHCP leases tries to give you.

---

### Post by dvks on 2014-11-28
Thanks for your feedback,
there may be many reasons to have the system connected to two separate networks on separate NICs, for example one network is opened to the internet while the other network is only a local LAN with no exposure to the internet

---

### Post by Sef on 2014-11-29
> [COLOR=#000000]3. running the command: "sudo dhclient -x" or "sudo dhclient -r " doesn't have any effect and it doesn't stop or restart the dhclient instace(s) is there a way to stop or restart the dhcp client and force the dhcp server to generate a new lease?[/COLOR]

"sudo dhclient -r eth0"  just releases the ip address.

"sudo dhclient eth0" would renew the ip address.

Replace eth0 with eth1 or whatever the ip address is on.

---

### Post by SeijiSensei on 2014-11-29
Use [static addressing]("https://help.ubuntu.com/14.04/serverguide/network-configuration.html#static-ip-addressing") on at least one of the networks.  That gives you complete control over addressing and routing and will help avoid any conflicts.

---

