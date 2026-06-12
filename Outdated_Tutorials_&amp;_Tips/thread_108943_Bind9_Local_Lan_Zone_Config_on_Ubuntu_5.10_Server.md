---
title: "Bind9 Local Lan Zone Config on Ubuntu 5.10 Server"
date: 2005-12-27
forum: Outdated Tutorials &amp; Tips
---

### Post by kjburrell on 2005-12-27
After many hours of trying to configure bind for a zone on my home network, i finally managed to get this to work ( nslookup returns the address for the names).  I initially had trouble with syntax etc, even though I had copied examples online.  I removed all the comments to make debugging the syntax easier.

BIND9 install worked as a caching server without any changes after installation according to the HowToForge *ISP-Server Setup - Ubuntu 5.10 "Breezy Badger"*

You can use /var/log/syslog for checking that the config is good on starting dhcp daemon (/etc/init.d/bind9 start)

Config Files in /var/lib/named/etc/bind

named.conf has an include file of named.conf.local (named.conf not altered)

**This is the contents added to the named.conf.local**

zone "myexample.net" IN {
type master;
file "/etc/bind/zone.net.myexample";
}[B]

This is the newly created file zone.net.myexample[/B]

$ORIGIN myexample.net. ;
$TTL 1D
@ IN SOA myserver.myexample.net. hostmaster.myexample.net. ( 
200512271
8H
4H
4W
1D
)
;
@ IN NS myserver.myexample.net. ;
@ IN NS myserver2.myexample.net.;
;
myserver IN A 192.168.10.100;
myserver2 IN A 192.168.10.100;
;
myexample.net. IN A 192.168.10.100;
mypc1 IN A 192.168.10.150;
mypc2 IN A 192.168.10.151;
mypc3 IN A 192.168.10.152;
mypc4 IN A 192.168.10.153;
mypc5 IN A 192.168.10.154;

---

