---
title: "Can't connect to wifi during peak times"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by bertwagner on 2008-09-19
Both my friend and I seem to be having the same problem with our Hardy installs (on two different laptops):

My university provides wifi in the dorms.  During the day time, my friend and I have no problem connecting to these networks.  However, later in the evening (when I suppose more students are using it), neither of us can connect to the internet.  Our status bars say that we are connected to the network (and getting 95% signal!), however no web pages load.  I have also tried pinging multiple sites during that time and am not able to reach an sites.

The problem seems to only be with us; our friends who have Windows and Mac laptops never have problems connecting and using the internet during these high use times.  

Any suggestions would be greatly appreciated, thanks!

---

### Post by bertwagner on 2008-09-19
So I tried to play around with more network settings but with no avail.  I also tried the following thinking it would help but I am still unable to load web pages:

```

bert@muffin:~$ sudo dhclient -r ra0
There is already a pid file /var/run/dhclient.pid with pid 5891
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/ra0/00:15:af:e5:1c:9f
Sending on   LPF/ra0/00:15:af:e5:1c:9f
Sending on   Socket/fallback
DHCPRELEASE on ra0 to 172.16.255.11 port 67
bert@muffin:~$ sudo dhclient ra0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/ra0/00:15:af:e5:1c:9f
Sending on   LPF/ra0/00:15:af:e5:1c:9f
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 172.16.20.146 from 172.16.20.3
DHCPREQUEST of 172.16.20.146 on ra0 to 255.255.255.255 port 67
DHCPACK of 172.16.20.146 from 172.16.20.3
bound to 172.16.20.146 -- renewal in 4339 seconds.
bert@muffin:~$ 

```

---

