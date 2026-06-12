---
title: "dhcp configuration"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by ub007 on 2008-06-20
hello,

i just installed a dhcp server and configured the /etc/dhcpd.conf file.

default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.254;

subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.10 192.168.1.100;
range 192.168.1.150 192.168.1.200;
} 

its a stand alone server and havent connected any clients to it.How do i test whether the configuration works fine?

cheers,
David

---

### Post by Het Irv on 2008-06-20
I don't know if you can, DHCP is used for assigning IP addresses to computers in a network... so, to test you would need to set up a computer to look at your new server and see if it gets an IP address correctly.  Is the server always going to be standalone?  If so DHCP seems kinda pointless...

---

### Post by the_doc on 2008-06-20
Agreed, I think you're going to have to hook up at least one node to test the DHCP configuration.

---

### Post by ub007 on 2008-06-23
Hi,
yep,got the client PCs ready and a switch.
I tried configuring DHCP and finally got it to start(used random IPs and subnets),but its not yet functional.I've got 4 PCs(installed ubuntu server on one of them) and a switch.I'vent configured DNS yet.How do i set up this network?I wish to give a static IP to the server and other PCs to get their IPs via dhcp.could anyone help me with the condiguration....?
What steps to follow,what IPs to put and so on....

Cheers,
Davis

---

### Post by Het Irv on 2008-06-23
In the server you should be able to set a static IP on the server itself, (sorry I only know the GUI way to do this).  If you set the Default gateway to the Server's IP address.  That should get you working.

---

