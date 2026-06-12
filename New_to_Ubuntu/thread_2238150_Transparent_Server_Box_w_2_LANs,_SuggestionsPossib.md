---
title: "Transparent Server Box w/ 2 LANs, Suggestions/Possibility? (BUILD)"
date: 2014-08-06
forum: New to Ubuntu
---

### Post by matthew48 on 2014-08-06
Good Morning All,
      I have just started using Ubuntu and have realized what a power house it would make as a dedicated transparent server.  I share my internet connection with my neighbors and wish to cache their connection but leave mine uncached, for the time being, connecting directly to the modem.  Currently I have a modem connected to a router and another router connected to that router as an AP on different local IPs (192.168.1.1 vs 192.168.3.1).  As I understand it, I would build a transparent server/squid box that would go between my modem and my router.  It would need to have 3 gigabit network cards, a core i5, 16GB ram and an ssd for cache in order to do everything I could possibly ask of it correct?  3 network cards since 1 is WAN, 1 is cached LAN and the other is uncached LAN routed directly to the WAN, is this possible?  I would have 1 router connected to the cached LAN port and the other connected to the uncached LAN port.  Would that work?   And if so, could you point me to how to configure the LAN ports.  All the configs I have ever seen for Ubuntu with network control only mention an Eth0 as WAN and a Eth1 as LAN.  I hope I am clear enough.  Thank you for your help, I really appreciate it.    



Matthew

---

### Post by SeijiSensei on 2014-08-06
Your hardware suggestion are overkill.  I manage a 8 GB gateway at a client site that runs Squid for over 200 users while also scanning all their inbound email.  Hardly breaks a sweat.  

I'd put the Squid box behind the final router that connects upstream to the Internet.  So you would assign eth0 an address in the router's subnet.  If the router has its "LAN" connection as 192.168.1.1, you would use 192.168.1.2 on eth0.  You can have additional Ethernet connections just by defining eth2, eth3, etc.  You probably want to use static addressing on this box by adding stanzas to /etc/network/interfaces like this:

```

auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet static
address 192.168.2.1
netmask 255.255.255.0

auto eth2
iface eth2 inet static
address 192.168.3.1
netmask 255.255.255.0

```
Notice only the interface pointing upstream has a "gateway" entry.

If you go the transparent route, then you can differentiate between you and your neighbors by only redirecting their traffic through the proxy.  You'll need an iptables rule like this:

```
/sbin/iptables -t nat -A PREROUTING -p tcp -j REDIRECT --to-port 3128 -s 192.168.3.0/24 --dport 80
```

That routes traffic coming from 192.168.3.0/24 through the Squid cache, but leaves traffic from 192.168.2.0/24 alone.

---

### Post by matthew48 on 2014-08-06
Thank you Sensei!  I will give it a try afterwork.  If I could ask you one more question though, if you were building a squid box what hardware would you use.  I was thinking an ssd to handle large cache files such as videos and updates, and a lot of ram to handle all the smaller cache files.  The i5 to handle multiple requests at one time, between the 5 houses we could have roughly 30 concurrent users pulling YouTube vids and larger cached files. Thank you for your help.

---

### Post by SeijiSensei on 2014-08-08
Many video files are distributed with HTTP [headers that disable caching]("http://tools.ietf.org/html/rfc2616#section-14.9") to discourage copyright infringement.  Squid will ignore those.  I manage a caching gateway that has over 200 users.  Our total cache size is about 9 GB.  

Usually all the cache is kept in one directory, and Squid distributes the stored objects across an array of subdirectories beneath that.  I've never tried to split up the caching locations.  There may be some directives in squid.conf that enable this, but I've never used them.  On that gateway we have just a single hardware RAID1 array with two 7200 rpm SATA drives.  Even scanning every downloaded object with [SquidClamAV]("http://squidclamav.darold.net/") doesn't seem to impose much of a performance penalty when it is used with clamd.  While this is a server that has dual Xeons, it's also busy scanning all the organization's mail for spam and viruses.

---

