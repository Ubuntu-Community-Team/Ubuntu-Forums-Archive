---
title: "Multicast Ubuntu Log Question"
date: 2023-03-16
forum: New to Ubuntu
---

### Post by bhubunt on 2023-03-16
Hi,
On an Ubuntu log I came across a section I don't understand. In this Ubuntu log, posted on Pastebin, it says my private laptop is joining Multicast (line 126): [https://pastebin.com/2dKhsAGe](https://pastebin.com/2dKhsAGe)

(avahi-daemon: Joining mDNS multicast group on interface enp0s25.IPv4 with address 192.168.1.19).

When I googled address  192.168.1.19, I hit a page saying that this address relates to my router, see thumbnail.

However, I do not have a router and I also do not have a server. I just use a commercial modem, no router, and I only use desktop versions of Ubuntu on a private laptop, not a company or work laptop.

---

### Post by MAFoElffen on 2023-03-16
In your logs here:
```

07:56:02 nm-dispatcher: req:2 'dhcp4-change' [enp0s25]: start running ordered scripts...
07:56:02 dhclient: bound to 192.168.1.19 -- renewal in 1698 seconds.
07:56:02 avahi-daemon: Registering new address record for 192.168.1.19 on enp0s25.IPv4.
07:56:02 NetworkManager: <info>  [1678953362.5293] policy: set 'Wired connection 1' (enp0s25) as default for IPv4 routing and DNS
07:56:02 avahi-daemon: New relevant interface enp0s25.IPv4 for mDNS.
07:56:02 NetworkManager: <info>  [1678953362.5292] manager: NetworkManager state is now CONNECTED_SITE
07:56:02 whoopsie: [07:56:02] Cannot reach: https://daisy.ubuntu.com
07:56:02 avahi-daemon: [COLOR=#ff0000]Joining mDNS multicast group[/COLOR] on interface enp0s25.IPv4 with address 192.168.1.19.
07:56:02 NetworkManager: <info>  [1678953362.5253] dhcp4 (enp0s25): state changed unknown -> bound
07:56:02 dhclient: DHCPACK of 192.168.1.19 from 192.168.1.1

```
Refer to this definition:
> 
Multicast. Multicasting is defined as a single source sending to multiple recipients on a network when the receiver broadcasts a signal for acceptance.

Translation:
Your network connection is handled by Network Manager via DHCP from your router, which is 192.168.1.1. Your computer (the DHCP client) sent out a multicast call out on the network 192.168.1.0 from the Ethernet device 'enp0s25' and was answered by your router, which is your DHCP server on your network. The router answered and assigned your enp0s25 port with an IP address of 192.68.1.19...

You can confirm that by doing these two commands:
```

ip a | grep 'inet ' | grep 'dynamic'
ip r

```
Where you will see with the first command that the IP device enp0s25 assigned with it's IP address (192.168.1.19). 

In the second command, it will show the default route to your router in the first line, which starts with "default via", showing the gateway IP (192.158.1.1) and your computers device (ens0p25). The second line showing your Network ID (192.168.1.0) and from your Network device, enp0s25 (192.168.1.19).

Try it and see. Does that explanation help show you that 'all is well', and that what is there is normal output?

---

### Post by bhubunt on 2023-03-16
> **MAFoElffen said:**
> In your logs here:
```

07:56:02 nm-dispatcher: req:2 'dhcp4-change' [enp0s25]: start running ordered scripts...
07:56:02 dhclient: bound to 192.168.1.19 -- renewal in 1698 seconds.
07:56:02 avahi-daemon: Registering new address record for 192.168.1.19 on enp0s25.IPv4.
07:56:02 NetworkManager: <info>  [1678953362.5293] policy: set 'Wired connection 1' (enp0s25) as default for IPv4 routing and DNS
07:56:02 avahi-daemon: New relevant interface enp0s25.IPv4 for mDNS.
07:56:02 NetworkManager: <info>  [1678953362.5292] manager: NetworkManager state is now CONNECTED_SITE
07:56:02 whoopsie: [07:56:02] Cannot reach: https://daisy.ubuntu.com
07:56:02 avahi-daemon: [COLOR=#ff0000]Joining mDNS multicast group[/COLOR] on interface enp0s25.IPv4 with address 192.168.1.19.
07:56:02 NetworkManager: <info>  [1678953362.5253] dhcp4 (enp0s25): state changed unknown -> bound
07:56:02 dhclient: DHCPACK of 192.168.1.19 from 192.168.1.1

```
Refer to this definition:

Translation:
Your network connection is handled by Network Manager via DHCP from your router, which is 192.168.1.1. Your computer (the DHCP client) sent out a multicast call out on the network 192.168.1.0 from the Ethernet device 'enp0s25' and was answered by your router, which is your DHCP server on your network. The router answered and assigned your enp0s25 port with an IP address of 192.68.1.19...

You can confirm that by doing these two commands:
```

ip a | grep 'inet ' | grep 'dynamic'
ip r

```
Where you will see with the first command that the IP device enp0s25 assigned with it's IP address (192.168.1.19). 

In the second command, it will show the default route to your router in the first line, which starts with "default via", showing the gateway IP (192.158.1.1) and your computers device (ens0p25). The second line showing your Network ID (192.168.1.0) and from your Network device, enp0s25 (192.168.1.19).

Try it and see. Does that explanation help show you that 'all is well', and that what is there is normal output?

Hi,
Thanks very much for your valued comments.

However, I do *not* have a router and I do *not* have a server.

I am not on any networks, either.

I am just a regular internet customer and use a run-of-the-mill modem provided by my internet provider, without a router that I am logged into.  

Hence my surprise when  a google search indicated that the IP address is linked to the use of a router.

Since I don't have a router, what other logical explanation could there be for this code?

---

### Post by MAFoElffen on 2023-03-16
Well... That may well be.

Your modem is providing a route to your ISP, so is considered to also be a router to the outside world. And since you have not asked how to setup a static IP address, it is also acting as your local network's DHCP server. <-- That is a networking term for the service provided. Your ISP modem is a multi-purpose, multi-function device. That is how basic networking works...

Also, network 192.168.1.0 is a private class C network range. So...

*** Did you do the commands from a terminal to investigate for yourself and to be able to provide more information?

Post back the results of the output from those two commands wrapped within CODE Tags, and I will explain further.

---

### Post by TheFu on 2023-03-16
> **bhubunt said:**
> Hi,
Thanks very much for your valued comments.

However, I do *not* have a router and I do *not* have a server.

I am not on any networks, either.

I am just a commercial internet customer and use a run-of-the-mill modem from my internet provider, without a router that I am logged into. I also don't code. 

Hence my surprise when  a google search indicated that the IP address is linked to the use of a router.

Googling is good, but sometimes it leads to the wrong determinations.

MAFoElffen is 100% correct, as usual.

If you connect to the internet, then you do have a router in the building. That's how networking works.

Your Linux system is running a number of servers. "Servers" aren't just hardware, they can be either hardware or software or the combination of either. Every Linux system runs a number of server software processes. It is part of the core way that most computers work.  Your phone has a number of servers running too, BTW.

End users don't typically log into routers. Connecting via an ethernet cable or wifi is sufficient.  It isn't important as a typical home or small business router will work with any device that connects (ethernet cable or wifi), provide the local and internet access and provide a LAN IP (via running a DHCP server).  This is why any device in almost any home will just work after being connected to a live network port.

mDNS is a LAN-only way for systems on the same LAN to find each other using a name, not an IP.  It is enabled by default on almost all Linux desktops regardless of distro. Usually, it is handy in a modern office/home so that different computing devices (printers, streaming sticks, cameras, and other computers, tablets, phones) can all "see" each other on the network. It doesn't matter if there aren't any other devices or not. mDNS broadcasts using the "network" IP that "I'm here, here's my name, IP, and the services I can provide".  Most people want this. They want computers to find each other so they can easily communicate through approved methods they both understand.  

On Linux, mDNS is usually provided by the **avahi** daemon/service. [https://manpages.ubuntu.com/manpages/focal/man8/avahi-daemon.8.html](https://manpages.ubuntu.com/manpages/focal/man8/avahi-daemon.8.html)  It is most handy for me when connecting to printers. They seem to pre-configure themselves, before I ask.

The IP range that is being reported (192.168.x.x) is for private LAN use only. No internet connected network device, like the router that your ISP provided to you, will send packets outside the LAN with that IP, or on that entire subnet.  There are some other subnets that are used by larger organizations which behave the same; 10.x.x.x/8 and 172.16.x.x/16 are examples. Don't worry, you don't need to know this, though it can be helpful knowledge when visiting hotels or businesses if you connect a computer into their network.

---

### Post by bhubunt on 2023-03-16
Thanks for the explanations. Answer number 2 above only referred to using a personal router, hence my inference that the code line applied to the use of a personal router, as did the google search result I posted in post number one. 

Here are the answers to the command lines

```
 inet 192.168.1.19/24 brd 192.168.1.255 scope global dynamic noprefixroute enp0s25 
```



```
 default via 192.168.1.1 dev enp0s25 proto dhcp metric 100 
192.168.1.0/24 dev enp0s25 proto kernel scope link src 192.168.1.19 metric 100 
```

So this is the IP range of private lan, not a subnet. I guess then I can close this thread.

---

### Post by TheFu on 2023-03-16
> **bhubunt said:**
> Thanks for the explanations. Answer number 2 above only referred to using a personal router, hence my inference that the code line applied to the use of a personal router, as did the google search result I posted in post number one. 

Here are the answers to the command lines

```
 inet 192.168.1.19/24 brd 192.168.1.255 scope global dynamic noprefixroute enp0s25 
```



```
 default via 192.168.1.1 dev enp0s25 proto dhcp metric 100 
192.168.1.0/24 dev enp0s25 proto kernel scope link src 192.168.1.19 metric 100 
```

So this is the IP range of private lan, not a subnet. I guess then I can close this thread.

A private LAN **is** a subnet.

Also, the way to mark a thread solved is to use the Thread Tools button near the top of the page (on the right).  Only the person who created the Thread can use that. Humans will see the change in subject. The forum system has a separate "SOLVED" flag that is used for searches. It is a DB value, so getting SOLVED into the DB field is very helpful.

---

### Post by bhubunt on 2023-03-19
> **TheFu said:**
> 

Also, the way to mark a thread solved is to use the Thread Tools button near the top of the page (on the right).  Only the person who created the Thread can use that. Humans will see the change in subject. The forum system has a separate "SOLVED" flag that is used for searches. It is a DB value, so getting SOLVED into the DB field is very helpful.

There are still some lingering questions. So the issue has not been solved yet.

---

