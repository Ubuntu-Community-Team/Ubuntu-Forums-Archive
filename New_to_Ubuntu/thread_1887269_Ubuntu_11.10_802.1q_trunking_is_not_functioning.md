---
title: "Ubuntu 11.10 802.1q trunking is not functioning"
date: 2011-11-26
forum: New to Ubuntu
---

### Post by sergejcepurin on 2011-11-26
Hello, Chaps,

I've used Ubuntu 11.04 and Dynagen for emulation of virtual routers and made it possible to trunk multiple Vlans via single ethernet port down to the physical switch. Just can't find a clue why but recently I've upgraded ubuntu to 11.10 and now vlan trunking is not working for me. I'm not Ubuntu specialist and can't find a way to make it function as it did previously so your help is vital and much appreciated.

P.S.

Made following to enable 802.1q trunking:

sudo apt-get install vlan
sudo modprobe 8021q

To load module after reboot add to /etc/modules:

sudo  sh -c 'grep -q 8021q /etc/modules || echo 8021q >> /etc/modules'

sudo ifconfig eth1 mtu 1536

To make it permanent:

“/sbin/ifconfig eth1 mtu 1536” to /etc/rc.local

"lsmod | grep 8021q" brings me following output:

Module                  Size  Used by
8021q                  24173  0 
garp                   14602  1 8021q

The module is loaded so are there any problems with new release itself?

---

### Post by KiLaHuRtZ on 2012-03-11
I have the same problem.  Same config works on all my 8.04 (best release in my opinion), 10.10 and 11.04 systems.  I found the interface gets built but sysctl bitches about some keys not being valid.  In my senario, I use IPv6.  I think it is an order of operations that is causing this.  When I get time, I'm going to gather some output and file a bug on this.

Personally, I am dis-satisifed with Canonical and Ubuntu as of late.  They seem to be too busy wanting to takeover the world and run Ubuntu on everything versus just sticking with what you know.  By this I mean, fix and polish what is already there versus introducing more turds in the punchbowl...

---

