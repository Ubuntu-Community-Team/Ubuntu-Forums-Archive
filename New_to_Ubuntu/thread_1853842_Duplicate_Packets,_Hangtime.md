---
title: "Duplicate Packets, Hangtime"
date: 2011-10-03
forum: New to Ubuntu
---

### Post by Yellobes on 2011-10-03
I'm having trouble with duplicate packets on a single lan, and I believe that the trouble lies with a network misconfiguration, but I cannot, for the life of me, find the configuration files with the error. Other computers on the lan exhibit no problems. It's somewhere in this box.

Here's the sitch:

```

PING google.com (74.125.225.81) 56(84) bytes of data.
64 bytes from 74.125.225.81: icmp_req=1 ttl=52 time=3541 ms
64 bytes from 74.125.225.81: icmp_req=1 ttl=52 time=3574 ms (DUP!)
64 bytes from 74.125.225.81: icmp_req=1 ttl=52 time=3678 ms (DUP!)
64 bytes from 74.125.225.81: icmp_req=1 ttl=52 time=3717 ms (DUP!)
64 bytes from 74.125.225.81: icmp_req=2 ttl=52 time=3646 ms
64 bytes from 74.125.225.81: icmp_req=2 ttl=52 time=3677 ms (DUP!)
64 bytes from 74.125.225.81: icmp_req=2 ttl=52 time=3728 ms (DUP!)
64 bytes from 74.125.225.81: icmp_req=2 ttl=52 time=3784 ms (DUP!)
64 bytes from 74.125.225.81: icmp_req=3 ttl=52 time=3366 ms

```

etc.
So, I'm getting exactly 3 duplicates per response, accompanied by a nice 3 1/2 second lag.

I've looked through /etc/dhcp3/dhclient.conf but can't see anything there, seems to be all defaults.

```

sudo cat /etc/dhcp3/dhclient.conf
# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, domain-search, host-name,
	netbios-name-servers, netbios-scope, interface-mtu,
	rfc3442-classless-static-routes, ntp-servers;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

```

I'm using nm-applet to handle my connections, and I've tried messing with those settings, but I am unable to connect by hand anyway

```

sudo iwconfig eth1 essid 'X' key **:**:**:**:**:**:**:**

```

```

03:54:36.368039   eth1     Set ESSID:"X"
03:54:36.368410   eth1     Set Encryption key:{800}****-****-****-****
03:54:36.384640   eth1     New Access Point/Cell address:**:**:**:**:**:**
03:54:36.388369   eth1     Set ESSID:off/any
03:54:36.388704   eth1     New Access Point/Cell address:Not-Associated

```

*Edit: I guess this was because the underlying NetworkManager was probs still running in the background. *

---

### Post by Yellobes on 2011-10-03
[Somehow] my pingtimes are back in the ~[25-50]
I tried removing virtualbox and all associated packages, and that removed the network entry in ifconfig and perhaps helped with pingtime, but I'm still getting exactly 3 duplicates for every packet I send. I'm done for the night.

---

### Post by Yellobes on 2011-10-04
One thing I should have mentioned initially is, this is particular to one lan and one lan only. It isn't a global thing. I get what you'd normally expect elsewhere.

```

8 packets transmitted, 8 received, 0% packet loss, time 35481ms
rtt min/avg/max/mdev = 24.162/24.597/24.951/0.254 ms

```

It's paranoid, but: could someone have messed with my system and corrupted something somewhere? I booted somebody who was on my network a week ago ( the connection tops out at 150k ) and set up a MAC filter, ( the router is old, the only encryption available is wep ) quickly thereafter I got ~20 remote admin attempts on the router, though I have no reason to believe they got in, as the remote-admin feature of the router is/was off and the access list remains the same.

---

### Post by audiomick on 2011-10-04
You might like to look at a program called wireshark.
I can see it in synaptic on 11.04

I haven't used it. I saw these
[http://openubuntu.com/index.php/topic,1621.0.html](http://openubuntu.com/index.php/topic,1621.0.html)
[http://openubuntu.com/index.php/topic,1661.0.html](http://openubuntu.com/index.php/topic,1661.0.html)

What is written there suggests that it could help you answer those sort of questions about whether someone is messing around with your w-lan.

---

