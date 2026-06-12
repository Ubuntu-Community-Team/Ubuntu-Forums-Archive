---
title: "ntwork won't come back on, wiredbroadband."
date: 2011-09-26
forum: New to Ubuntu
---

### Post by artyone on 2011-09-26
I moved my computer into a new spot and after firing up I got some intermittent disconnection to the broadband modem but now it won't come back on.

Oh, I'm still on 10.04

I got lots of stuff happening at system/admin/network tools

Devices has stuff for protocol, ip address, prefix and scope.
                                 IPv6     ::_            128          Host
                                 IPv4    _ _ _.0.0.1  _ _ _.0.0.0

(numbers are the address of my service provider?)

Ping has  5 packets trans and received at 100% to IPv4 address.

Netstat has tcp and tcp in listen state and udp has 2 sets of numerals, 4 and 5 digits long. Same IPv4 address (as all below use)

Traceroute has three times at .156, .083 and .029ms

Port Scan has a port number, state open and service IPP.

Routing table info returns nada.

Multicast info has
interface
lo _ _ _.0.0.1
eth1 as above
lo ip6-allnodes
eth1 ip6-allnodes

system/preferences has automatic ticked for proxy and connections has wired connection1 with auto ticked... eth1 is gone now.

From the above info I would surmise that the connection from the server to modem to the network card is actually working but for some reason the connection from the network card to the operating system isn't working.

The icon on the top right which is supposed to be two arrows has all enabled but the edit connections won't allow a click. I must have turned something off or changed a default somewheres... please help this silly man!:confused:

If the connection is still into the card I have the option of just reloading the operating system to Ubuntu studio 11.04 as I've saved everything I want from the hard drive. I was going to do it anyways but didn't want to until I know it's broadband connected... and the new install will default to a new connection.

---

### Post by the.phantom on 2011-09-26
i am no expert !

but
how about just trying your live cd and see if that works
would narrow down a "cockpit trouble" pretty quick

and if it works then see the network settings and check yours on the hard drive

D

---

