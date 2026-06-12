---
title: "dhcp server"
date: 2012-02-05
forum: New to Ubuntu
---

### Post by mustafa ibrahim on 2012-02-05
root@mustafa-sr1:/home/mustafa-sr1# vim /etc/dhcp3/dhcpd.conf
root@mustafa-sr1:/home/mustafa-sr1# /etc/init.d/dhcp3-server restart
* Stopping DHCP server dhcpd3 [fail] 
* Starting DHCP server dhcpd3 * check syslog for diagnostics.

default-lease-time 600;
max-lease-time 7200;

option subnet-mask 255.255.255.0;
option broadcast-address 10.0.0.255;
option routers 10.0.0.138;
subnet 10.0.0.0 netmask 255.255.255.0 {
range 10.0.0.10 10.0.0.200;
host server1 {
hardware ethernet 00:15:00:24:5c:b0;
fixed-address 10.0.0.11;
}
}

on syslog

Feb 5 22:22:15 mustafa-sr1 dhcpd: Wrote 0 deleted host decls to leases file.
Feb 5 22:22:15 mustafa-sr1 dhcpd: Wrote 0 new dynamic host decls to leases file.
Feb 5 22:22:15 mustafa-sr1 dhcpd: Wrote 0 leases to leases file.
Feb 5 22:22:15 mustafa-sr1 dhcpd: 
Feb 5 22:22:15 mustafa-sr1 dhcpd: No subnet declaration for eth0:138 (0.0.0.0).
Feb 5 22:22:15 mustafa-sr1 dhcpd: ** Ignoring requests on eth0:138. If this is not what
Feb 5 22:22:15 mustafa-sr1 dhcpd: you want, please write a subnet declaration
Feb 5 22:22:15 mustafa-sr1 dhcpd: in your dhcpd.conf file for the network segment
Feb 5 22:22:15 mustafa-sr1 dhcpd: to which interface eth0:138 is attached. **
Feb 5 22:22:15 mustafa-sr1 dhcpd: 
Feb 5 22:22:15 mustafa-sr1 dhcpd: 
Feb 5 22:22:15 mustafa-sr1 dhcpd: Not configured to listen on any interfaces!
[http://255.255.255.0/](http://255.255.255.0/)
&#8206;255.255.255.0
Like ·  · Unfollow Post · Share · 28 minutes ago
Mustafa Ibrahim on restart root@mustafa-sr1:/home/mustafa-sr1# /etc/init.d/dhcp3-server restart
* Stopping DHCP server dhcpd3 [fail] 
* Starting DHCP server dhcpd3 * check syslog for diagnostics.

---

### Post by Bodsda on 2012-02-05
loads 

of 

random text

with

no

question

---

### Post by mustafa ibrahim on 2012-02-07
why no question ?
really 
please 
i do not know what do u mean?

and i do no't know what is my problem?

---

### Post by Zill on 2012-02-07
> **mustafa ibrahim said:**
> why no question ?
really 
please 
i do not know what do u mean?

and i do no't know what is my problem?
We cannot *guess* what your system configuration is or what you are trying to do. eg.

1)  Which Ubuntu release you are using?
2)  What are you trying to do?
3)  Which applications have you installed or are trying to configure to achieve this?

---

### Post by mustafa ibrahim on 2012-02-08
installed ubuntu server i do not know how to know my release !!!

i am trying to install dhcp server and take attentions i make purge and remove to my dhcp server and still working good never mind but my problem now that i want to reserve ips 
and i did what i wrote above

---

### Post by Zill on 2012-02-09
> **mustafa ibrahim said:**
> installed ubuntu server i do not know how to know my release !!!
You can find this from the following command:
```
cat /etc/lsb-release
```
> **mustafa ibrahim said:**
> i am trying to install dhcp server and take attentions i make purge and remove to my dhcp server and still working good never mind but my problem now that i want to reserve ips 
and i did what i wrote above
I do not run a dhcp server installation and so others may be able to give better answers to your queries.  However, as a starting point, I suggest that the Ubuntu documentation on [dhcp3-server]("https://help.ubuntu.com/community/dhcp3-server") may be of assistance.
> **mustafa ibrahim said:**
> 
Feb 5 22:22:15 mustafa-sr1 dhcpd: No subnet declaration for eth0:138 (0.0.0.0).
Feb 5 22:22:15 mustafa-sr1 dhcpd: ** Ignoring requests on eth0:138. If this is not what
Feb 5 22:22:15 mustafa-sr1 dhcpd: you want, please write a subnet declaration
Feb 5 22:22:15 mustafa-sr1 dhcpd: in your dhcpd.conf file for the network segment
Feb 5 22:22:15 mustafa-sr1 dhcpd: to which interface eth0:138 is attached. **
Feb 5 22:22:15 mustafa-sr1 dhcpd: 
Feb 5 22:22:15 mustafa-sr1 dhcpd: 
Feb 5 22:22:15 mustafa-sr1 dhcpd: Not configured to listen on any interfaces!
These errors seem to indicate that the wanted interface is not defined correctly in the config file /etc/dhcp3/dhcpd.conf.  I suggest you investigate this and edit the file appropriately.

If you still have problems then please explain *exactly* what you want to do, with an example, *and* what is actually happening.  It may also be useful if you could include your /etc/dhcp3/dhcpd.conf file (if you have no concerns about security of IP addresses, domains etc.)

I note that you appear to be logging in as root.  The Ubuntu documentation [RootSudo]("https://help.ubuntu.com/community/RootSudo") explains that sudo should be used instead.
> Enabling the Root account is rarely necessary. Almost everything you need to do as administrator of an Ubuntu system can be done via sudo or gksudo. If you really need a persistent Root login, the best alternative is to simulate a Root login shell using the following command...
```
sudo -i	
```
Hope this helps.  Good luck.

---

### Post by mustafa ibrahim on 2012-02-10
ok now i make that in vim /etc/dhcp3/dhcpd.conf
i wrote that # have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
option domain-name "example.org";
option domain-name-servers ns1.example.org, ns2.example.org;

default-lease-time 600;
max-lease-time 7200;

subnet 10.0.0.0 netmask 255.255.255.0 {
range 10.0.0.10 10.0.0.200;
option subnet-mask 255.255.255.0;
option broadcast-address 10.0.0.255;
option routers 10.0.0.138;
host server1 {
hardware ethernet 00:15:00:24:5c:b0;
fixed-address 10.0.0.11;
}
}


 then make rstart /etc/init.d/dhcp3-server restart
4 minutes ago · Like
Mustafa Ibrahim &#8206;/etc/init.d/dhcp3-server restart
* Stopping DHCP server dhcpd3 [fail]
* Starting DHCP server dhcpd3 * check syslog for diagnostics.
[fail]
4 minutes ago · Like
Mustafa Ibrahim and in sys log 3
Feb 10 16:00:18 mustafa-sr1 dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Feb 10 16:00:18 mustafa-sr1 dhcpd: All rights reserved.
Feb 10 16:00:18 mustafa-sr1 dhcpd: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Feb 10 16:00:18 mustafa-sr1 dhcpd: Wrote 0 deleted host decls to leases file.
Feb 10 16:00:18 mustafa-sr1 dhcpd: Wrote 0 new dynamic host decls to leases file.
Feb 10 16:00:18 mustafa-sr1 dhcpd: Wrote 0 leases to leases file.
Feb 10 16:00:18 mustafa-sr1 dhcpd:
Feb 10 16:00:18 mustafa-sr1 dhcpd: No subnet declaration for eth0:138 (0.0.0.0).
Feb 10 16:00:18 mustafa-sr1 dhcpd: ** Ignoring requests on eth0:138. If this is not what
Feb 10 16:00:18 mustafa-sr1 dhcpd: you want, please write a subnet declaration
Feb 10 16:00:18 mustafa-sr1 dhcpd: in your dhcpd.conf file for the network segment
Feb 10 16:00:18 mustafa-sr1 dhcpd: to which interface eth0:138 is attached. **
Feb 10 16:00:18 mustafa-sr1 dhcpd:
Feb 10 16:00:18 mustafa-sr1 dhcpd:
Feb 10 16:00:18 mustafa-sr1 dhcpd: Not configured to listen on any interfaces!

---

### Post by collisionystm on 2012-02-10
Okay

Lets see here...

First Check ```
/etc/default/dhcp3-server
```make sure the line, INTERFACES= looks like this

> INTERFACES=""We will leave it that way for now.

You need to figure out
What is providing DNS
What is your router address
What is your broadcast?
If you have an ip address of 10.0.0.0/24 then your broadcast should be 10.0.0.255

Put the DNS ip where i put DNS
Put the router IP where I put ROUTER

Now, your /etc/dhcp3/dhcpd.conf


option domain-name-servers DNS;
option netbios-name-servers DNS;
option netbios-dd-server DNS;
option netbios-node-type 8;
subnet 192.168.16.0 netmask 255.255.240.0 {
        range 10.0.0.10    10.0.0.200;
        option routers ROUTER;
        option broadcast-address 10.0.0.255;
        option subnet-mask 255.255.255.0;
}


Restart dhcp server after making changes

```
sudo service dhcp3-server restart
```"You shouldn't need to worry about it - the  DHCP server will check whether the address exists on the network before  allocating it.  Do man dhcpd.conf and look at the IP Address Conflict Prevention section.  Provided the device will respond to an ICMP Echo Request, you don't need to do anything.
  Note: A conflict may arise if a device gets the IP address via DHCP initially, followed by the static address being allocated."
[http://serverfault.com/questions/289831/exclude-ip-address-from-dhcp-pool](http://serverfault.com/questions/289831/exclude-ip-address-from-dhcp-pool)


Here is what I would do. Set the scope of IP's to 10.0.0.25-10.0.0.254

Put all your servers and routers in the 10.0.0.1-10.0.0.24 range.

---

### Post by savanna on 2012-02-10
-> No subnet declaration for eth0:138 (0.0.0.0).

Replace 10.0.0.0 with appropriate address.

---

### Post by collisionystm on 2012-02-10
> **savanna said:**
> -> No subnet declaration for eth0:138 (0.0.0.0).

Replace 10.0.0.0 with appropriate address.


post the output of

cat /etc/network/interfaces

---

### Post by mustafa ibrahim on 2012-02-11
thanks a lot 

# vim /etc/default/dhcp3-server

 Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0:138"




then 
 /etc/init.d/dhcp3-server restart
then 
root@mustafa-sr1:/home/mustafa-sr1# /etc/init.d/dhcp3-server restart
dhcpd self-test failed. Please fix the config file.
The error was:
Internet Systems Consortium DHCP Server V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
bad range, address 10.0.0.25 not in subnet 192.168.16.0 netmask 255.255.240.0
root@mustafa-sr1:/home/mustafa-sr1#


so i changed my subnet like 
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
#option domain-name "example.org";
#option domain-name-servers ns1.example.org, ns2.example.org;

default-lease-time 600;
max-lease-time 7200;
option domain-name-servers DNS;
option netbios-name-servers DNS;
option netbios-dd-server DNS;
option netbios-node-type 8;
subnet 10.0.0.0 netmask 255.255.255.0 {
range 10.0.0.25 10.0.0.254;
option routers 10.0.0.138;
option broadcast-address 10.0.0.255;
option subnet-mask 255.255.255.0;
}

then i make restart to my dhcp service 
 /etc/init.d/dhcp3-server restart

then 
i find that 
root@mustafa-sr1:/home/mustafa-sr1# /etc/init.d/dhcp3-server restart
 * Stopping DHCP server dhcpd3                                           [fail]
 * Starting DHCP server dhcpd3                                                   * check syslog for diagnostics.
                                                                         [fail]
root@mustafa-sr1:/home/mustafa-sr1#

so i opend sys log and i find in 
# tailf /var/log/syslog
Feb 11 15:03:37 mustafa-sr1 dhcpd: Internet Systems Consortium DHCP Server V3.1.                                                                              3
Feb 11 15:03:37 mustafa-sr1 dhcpd: Copyright 2004-2009 Internet Systems Consorti                                                                              um.
Feb 11 15:03:37 mustafa-sr1 dhcpd: All rights reserved.
Feb 11 15:03:37 mustafa-sr1 dhcpd: For info, please visit [https://www.isc.org/so](https://www.isc.org/so)                                                                              ftware/dhcp/
Feb 11 15:03:39 mustafa-sr1 dhcpd: Internet Systems Consortium DHCP Server V3.1.                                                                              3
Feb 11 15:03:39 mustafa-sr1 dhcpd: Copyright 2004-2009 Internet Systems Consorti                                                                              um.
Feb 11 15:03:39 mustafa-sr1 dhcpd: All rights reserved.
Feb 11 15:03:39 mustafa-sr1 dhcpd: For info, please visit [https://www.isc.org/so](https://www.isc.org/so)                                                                              ftware/dhcp/
Feb 11 15:03:39 mustafa-sr1 dhcpd: Internet Systems Consortium DHCP Server V3.1.                                                                              3
Feb 11 15:03:39 mustafa-sr1 dhcpd: Copyright 2004-2009 Internet Systems Consorti                                                                              um.
Feb 11 15:03:39 mustafa-sr1 dhcpd: All rights reserved.
Feb 11 15:03:39 mustafa-sr1 dhcpd: For info, please visit [https://www.isc.org/so](https://www.isc.org/so)                                                                              ftware/dhcp/
Feb 11 15:03:39 mustafa-sr1 dhcpd: Wrote 0 leases to leases file.
Feb 11 15:03:39 mustafa-sr1 dhcpd:
Feb 11 15:03:39 mustafa-sr1 dhcpd: No subnet declaration for eth0:138 (0.0.0.0).
Feb 11 15:03:39 mustafa-sr1 dhcpd: ** Ignoring requests on eth0:138.  If this is                                                                               not what
Feb 11 15:03:39 mustafa-sr1 dhcpd:    you want, please write a subnet declaratio                                                                              n
Feb 11 15:03:39 mustafa-sr1 dhcpd:    in your dhcpd.conf file for the network se                                                                              gment
Feb 11 15:03:39 mustafa-sr1 dhcpd:    to which interface eth0:138 is attached. *                                                                              *
Feb 11 15:03:39 mustafa-sr1 dhcpd:
Feb 11 15:03:39 mustafa-sr1 dhcpd:
Feb 11 15:03:39 mustafa-sr1 dhcpd: Not configured to listen on any interfaces!

 so     help me i do not know the problem !!!!!!

---

### Post by mustafa ibrahim on 2012-02-12
please help

---

### Post by collisionystm on 2012-02-12
> **mustafa ibrahim said:**
> please help

post the output of 

cat /etc/network/interfaces

---

### Post by mustafa ibrahim on 2012-02-12
cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.2
        netmask 255.255.255.252
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 10.0.0.138
##############################################################################
auto eth0:138
iface eth0:138 inet static
 address 10.0.0.138
 netmask 255.255.255.0
# gateway 10.0.0.138
auto eth0:2
iface eth0:2 inet static
 address 10.0.2.1
 netmask 255.255.255.0
# gateway 192.168.1.1
#####################################

auto eth0:5
iface eth0:5 inet static
 address 10.0.5.1
 netmask 255.255.255.0
# gateway 192.168.1.1
####################################
auto eth0:7
iface eth0:7 inet static
 address 10.0.7.1
 netmask 255.255.255.0
 #gateway 192.168.1.1
####################################
auto eth0:6
iface eth0:6 inet static
 address 10.0.6.1
 netmask 255.255.255.0
 #gateway 192.168.1.1
####################################
#auto eth0:11
#iface eth0:11 inet static
# address 10.0.11.1
# netmask 255.255.255.0
 #gateway 192.168.1.1

---

### Post by collisionystm on 2012-02-13
why do you have so many interfaces?

---

### Post by mustafa ibrahim on 2012-02-14
really i was thinking of disabling net cut
do u have any answer to stop net cut?????????
and what do u see about my dhcp server??????????????

---

### Post by mustafa ibrahim on 2012-03-02
hello 
any answers please

---

### Post by Zill on 2012-03-02
mustafa ibrahim:  In an effort to solve your problem several questions have been asked in this thread.  Also, several suggestions have been made.

Unless you are willing to fully respond to *all* the points raised then I doubt if anyone can help you further.

---

