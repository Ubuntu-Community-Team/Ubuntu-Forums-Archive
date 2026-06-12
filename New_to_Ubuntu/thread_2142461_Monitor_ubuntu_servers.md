---
title: "Monitor ubuntu servers"
date: 2013-05-05
forum: New to Ubuntu
---

### Post by Panel on 2013-05-05
Hello

I am going to build ubuntu servers running ubuntu server.

I wonder what are avialable solutions for ubuntu to monitor few running servers.

I need to monitor:
Procesor/Ram usage
CPU/GPU temperatures
Fan speeds

It would be extremly helpfull to monitor all servers from one application/browser tab
I also need email alerts. 

It would be nice to have windows or web based client for monitoring

I preffer free.

---

### Post by Cheesemill on 2013-05-05
[Nagios]("http://www.nagios.org/")
[Cacti]("http://www.cacti.net/")
[Munin]("http://munin-monitoring.org/")
[Landscape]("https://landscape.canonical.com/")

If you could get away with only monitoring from a Linux machine you could set up conky to report the stats of remote machines.

---

