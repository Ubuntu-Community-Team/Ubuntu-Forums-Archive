---
title: "Quagga Troubleshooting - Please Help!"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Doctor Gonzo on 2008-06-11
Hey guys, I wasn't sure where else to post this. I've been getting into the ins and outs of using Ubuntu (I got me Hardy Heron) while working on my research project.

At this point, I'm trying to install the open source routing suite Quagga and getting it to run - however, I haven't had any success.

I’m having incredible amount of difficulty getting Quagga to even start its daemons on Ubuntu 8.04. In the /etc/quagga directory I have set the following permissions:

-rw-r–r– 1 quagga quaggavty 850 2008-06-06 15:28 daemons
-rw-r–r– 1 quagga quaggavty 471 2007-11-21 13:41 debian.conf
-rw-r–r– 1 quagga quaggavty 438 2008-06-06 16:05 ripd.conf
-rw-r–r– 1 quagga quaggavty 438 2008-06-06 16:05 ripd.conf~
-rw-r–r– 1 quagga quaggavty 426 2008-06-06 16:04 zebra.conf
-rw-r–r– 1 quagga quaggavty 435 2008-06-06 15:41 zebra.conf~

I also have the daemons file as well as the configuration files for zebra and ripd edited reflecting sample configuration options. However, every time I try to start quagga, I get the following error:

reichsfuhrer@montgomery:/etc/quagga$ /etc/init.d/quagga restart
Stopping Quagga daemons (prio:0): (ripd) (zebra) (bgpd) (ripngd) (ospfd) (ospf6d) (isisd).
Removing all routes made by zebra.
Nothing to flush.
Loading capability module if not yet done.
Starting Quagga daemons (prio:10): zebraprivs_init: could not setgroups, Operation not permitted

It would be of immense help if you guys could throw some light on this and help me figure out how to get things going.

To provide some context, I'm trying to use the physical machine as a router and have virtual machines (set up using VMware Workstation 6) talk to each other across a point2point connection between two physical hosts which are to act as routers.

peace.

---

