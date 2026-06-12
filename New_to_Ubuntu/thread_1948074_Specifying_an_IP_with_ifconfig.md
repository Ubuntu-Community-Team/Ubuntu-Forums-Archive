---
title: "Specifying an IP with ifconfig"
date: 2012-03-27
forum: New to Ubuntu
---

### Post by NaN010101 on 2012-03-27
I'm setting up Deluge and I am at the point of wanting to specify the IP of my NIC so I can set up port forwarding on my router. (It's actually a VM so the NIC is a VMWare virtual adapter bridged to one of the 2 NICs on the host machine - but I don't think my problem goes that deep)

I do an ifconfig and I see a single adapter, eth0 (pulling 192.168.0.60) and my loopback. Now I know I could just use .60 for an IP but I've called the VM L33 and I damn well want my NIC to do what I say not the other way round : -) 

I read man ifconfig and it seems to say "ifconfig eth0 192.168.0.33" (or perhaps "ifcofig eth0 address 192.168.0.33" should set the IP (like filling in the address field under network adapters->properties in windows). When I use the word "address" I get "unknown host". With just the address data (ie and not the actual word "address"), I find I need "sudo ifconfig eth0 192.168.0.33" because otherwise it's permision denied. Problem is, that doesn't change anything.. I try "sudo ifconfig eth0 down" and it disappears from "ifconfig" then "sudo ifconfig eth0 192.168.0.33" and it causes the adapter to come back up but it's still pulling 192.168.0.60 from the dhcp server on my router. 

Also, the netmask seems to be defaulting OK(ie 255.255.255.0) so I'm going to pick my battles on that one but where to heck is my default gateway? Shouldn't I at least see 192.168.0.1 somewhere in that ifconfig info? It must be right or I wouldn't be posting this here but I don't like defaults.. especially if I decide to get that other host machine NIC into the mix..

I remember something about resolv.conf for my DNS server info (hopefully I'm going to be able to use 192.168.0.1 for that like in Windows) but am I in for a fight there too?

Any help appreciated.

--> UPDATE.. not sure what it is about posting here that makes me find my own answer.. Doh.. there's a gui that will work for everything

---

### Post by Dangertux on 2012-03-27
> **NaN010101 said:**
> I'm setting up Deluge and I am at the point of wanting to specify the IP of my NIC so I can set up port forwarding on my router. (It's actually a VM so the NIC is a VMWare virtual adapter bridged to one of the 2 NICs on the host machine - but I don't think my problem goes that deep)

I do an ifconfig and I see a single adapter, eth0 (pulling 192.168.0.60) and my loopback. Now I know I could just use .60 for an IP but I've called the VM L33 and I damn well want my NIC to do what I say not the other way round : -) 

I read man ifconfig and it seems to say "ifconfig eth0 192.168.0.33" (or perhaps "ifcofig eth0 address 192.168.0.33" should set the IP (like filling in the address field under network adapters->properties in windows). When I use the word "address" I get "unknown host". With just the address data (ie and not the actual word "address"), I find I need "sudo ifconfig eth0 192.168.0.33" because otherwise it's permision denied. Problem is, that doesn't change anything.. I try "sudo ifconfig eth0 down" and it disappears from "ifconfig" then "sudo ifconfig eth0 192.168.0.33" and it causes the adapter to come back up but it's still pulling 192.168.0.60 from the dhcp server on my router. 

Also, the netmask seems to be defaulting OK(ie 255.255.255.0) so I'm going to pick my battles on that one but where to heck is my default gateway? Shouldn't I at least see 192.168.0.1 somewhere in that ifconfig info? It must be right or I wouldn't be posting this here but I don't like defaults.. especially if I decide to get that other host machine NIC into the mix..

I remember something about resolv.conf for my DNS server info (hopefully I'm going to be able to use 192.168.0.1 for that like in Windows) but am I in for a fight there too?

Any help appreciated.

--> UPDATE.. not sure what it is about posting here that makes me find my own answer.. Doh.. there's a gui that will work for everything


Just a tip if you want the changes to be persistant (meaning through reboot or /etc/init.d/networking restart) you will need to edit your /etc/network/interfaces file and edit the appropriate stanza for the interface you wish to change.

Hope this helps in the future :-)

---

