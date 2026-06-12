---
title: "Eth0 and eth1 - External and Internal"
date: 2012-11-02
forum: New to Ubuntu
---

### Post by squoggy on 2012-11-02
Hi folks,

Absolute noob here...can anyone help as brain hurting..

Have installed Ubuntu server on PC with 2 network cards (eth0 and eth1).

eth0 from my PC goes to my SKY home broadband router.

My home router IP is 192.168.0.1 (network is 192.168.0.0/24)

So eth0 is External (out to the internet) and eth1 is internal (home LAN).

Can anyone explain in laymans terms the External/Internal terms a bit better please..

Have set eth0 (external) as a static IP 192.168.0.3 but when I set the eth1 (home LAN) as static in same range it says cannot be on same network.

Can anyone explain the internal/external eth0/eth1 and how i go about seperating the 2 for my server please....cheers...

S..

---

### Post by mips on 2012-11-02
> **squoggy said:**
> 
Have set eth0 (external) as a static IP 192.168.0.3 but when I set the eth1 (home LAN) as static in same range it says cannot be on same network.


You have to use a different subnet for eth1 ie 192.168.1.0 /24

See [http://ubuntuforums.org/showthread.php?p=8816077](http://ubuntuforums.org/showthread.php?p=8816077)

Whatever hangs of eth1 will then be use 192.168.1.0 address (static or dynamic if you setup a dhcp server for that segment). What you are trying to do is essentially creating a router out of your linux box.

---

### Post by squoggy on 2012-11-02
thanks for prompt response...Ok this is what I want to do but am confused..gotta learn somewhere :)

Am basically attempting to create a home server that is a domain controller at home - so other PC's/laptops can join the home domain.

At the moment, my main server PC has network cable going from eth0 to the home sky router.

Sky router is 192.168.0.1 and have set a static IP for my server 192.168.0.3 ( Servers have to have a static IP??)..

I also have got a cisco 24 port switch..

Should a network cable run from my server (eth0) to the switch then from the switch to the Sky router?

Am doing this step by step so please bear with me...

---

### Post by JKyleOKC on 2012-11-02
Since the Sky router is at 192.168.0.1, your "internal" subnet has to use something else for the third number, such as 192.168.1.x. You then set the IP for each device on the internal network to use the same first three octets so that they are on that subnet. You must either configure the devices to use static IPs, or if you want automatic DHCP assignment, install dhcp3-server on your controller and configure it to hand out addresses on that subnet.

I'm in the midst of doing just that, to help me troubleshoot a problem on my laptop by using Live CDs that look for DHCP configuration. The man page for the DHCP server isn't exactly friendly to newcomers, but it's certainly complete!

You'll have fun and frustration setting up your dual-NIC operation, but it can be done...

EDIT: Step by step-- First, connect eth0 to the Sky router via cable. The switch has nothing to do with it. Second, connect eth1 to the switch, and all other devices on your local network to the switch also. The Sky router will serve ONLY your eth0 NIC; its wireless feature can't be used as you are planning, so can be turned off. If you need wireless access to your local subnet, you'll need additional hardware connected to the switch to provide it. As I said above, frustration...

---

### Post by squoggy on 2012-11-02
Cheers for reply...top forum this am getting there..

Still qute confused about why the need for 2 network cards in a server?

If eth0 from the server is patched into the cisco 24 port switch, then the switch is patched into the sky home broadband router...why do I need a second network card?

Can I not just patch in any new clients into the cisco 24-port switch and then join domain?

Is not the sky router providing DHCP addresses to all new clients...

ahhh..confused myself again...

---

### Post by JKyleOKC on 2012-11-02
There really isn't any need for two NICs, unless you want to set the box up to act as a router. From your initial message I gathered that this is what you're trying to do.

However, if it is, then the newly-created router will insulate the local network from the Sky router. If you want the local network to work with the Sky router directly, its devices should not connect to the dual-NIC box.

I do run cascaded routers here; I connect to my ISP through a Motorola 3347 that provides wireless access (but this box connects to it via cable) on the 192.168.1 subnet, and this box uses an additional card to serve the 192.168.0 subnet and feed additional boxes. One machine at the other end of the house connects via wireless using 192.168.1 automatic addressing, while the other two in my home office use 192.168.0 via cable. The laptop can use both.

My purpose in having the additional router action on this box was to allow tighter firewall control than my original DSL modem could provide. Additionally, the original setup had no separate router in place; I didn't get one until I needed wireless access. Once set up, I simply kept using it after replacing the modem with the 3347.

What steered you to the dual-NIC setup in the first place? It's possible that you really don't need it -- tell us what your goal is, and we may be able to help steer you through the forest to get there...

---

### Post by squoggy on 2012-11-02
Hey cheers for response..well appreciated...

Here's what I want to do but may be getting ahead of myself..trying to learn this stuff...

Want an ubuntu server at home setup through a cisco switch acting as a Primary Domain Controller, so that any other PC's in my house can plug into the switch and join the domain...

A bit like at work with Active Directory but NOT Windows :)

Then I was gonna use the second NIC (eth1) as an Intrusion Detection port.

1 step at a time though :)

So up to now...

Got Ubuntu server connected to a port on the switch, then a cable from the switch to the router..

Ubuntu server has a static IP..

So basically, as of yet I do not need eth1 until I try to setup an intrusion detection on that port....?

Cheers

So here's what I've done.

---

### Post by JKyleOKC on 2012-11-02
> **squoggy said:**
> Want an ubuntu server at home setup through a cisco switch acting as a Primary Domain Controller, so that any other PC's in my house can plug into the switch and join the domain...

A bit like at work with Active Directory but NOT Windows

<snip>

So here's what I've done.So long as you plug into the switch rather than using wireless access, then you DO need both NICs. This box would need to be set up as a router and DHCP server. You could still install intrusion detection in it later.

The NIC with a 192.168.0.x address would connect to the Sky router via cable, while the one with the 192.168.1.x address would connect to the switch, also via cable. Wireless would not be available initially but could be added once the basic system is working.

Your /etc/sysctl.conf file would need to be edited to enable forwarding, and your firewall would also have to be configured to allow desired traffic to pass through. I would use basic iptables for this rather than any of the "simplified" firewall packages such as ufw or firestarter, since they are designed for conventional needs rather than for the special needs of a routing box. You also need the dhcp3-server package installed and configured. The routing box should have a static address on its 192.168.1 subnet; the convention would be 192.168.1.1 and the DHCP server should not assign this address at all. I set the range on mine to be 100-199 so as not to conflict with static IP addresses already existing. The DHCP server should be configured to hand out its own (192.168.1.1, for example) address as the gateway and as the dns-name-server. And of course the other boxes to be plugged into the switch should be set to get their IP addresses automatically.

That's the broad outline. I'm sure there are how-tos available that may or may not help with the details. Feel free to ask here when it gets too confusing.

To add wireless, first turn OFF the wireless capability in the Sky router; it would interfere with the added access point. Then acquire another wireless router or access point, and connect it to the switch by cable. Configure it to get an address in the 192.168.1 subnet automatically (or assign it a static address in that range that is outside the range assigned automatically) and if it has its own DHCP server configure that to use still another subnet range such as 192.168.2.x so that there's no conflict between it, your DHCP server, and the one in the Sky router.

To add intrusion detection, simply put it into the routing box using the IP address that connects to the Sky router. Most such programs hook into the iptables chains to check packets immediately upon receipt.

And to get a better view of what's going on, install the "wireshark" package and run it as root for a while to see the incredibly complex exchange of packets involved in a simple network access...

---

