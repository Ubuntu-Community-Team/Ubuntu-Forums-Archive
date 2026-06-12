---
title: "Networking from the Command Line"
date: 2006-11-13
forum: Outdated Tutorials &amp; Tips
---

### Post by Haegin on 2006-11-13
This is just a guide to using the command line networking tools to set up your network. Firstly I will cover ifconfig which is for all network stuff and then 

I will cover iwlist and iwconfig for wireless networks. Finally I will cover how you can make it all permenant in /etc/network/interfaces.

***Ethernet (Wired)***
**ifconfig**
Ifconfig sets up all your basic network details such as your ip address, netmask and broadcast address. To list all the interfaces on the system just use
```
ifconfig
```
To bring an interface up or take it down again use
```
sudo ifconfig <interface> (up/down)
```
To set the ip address for that interface use
```
sudo ifconfig <interface> <ip address>
```
Note: you don't need to bring it up, specifying an ip address automatically brings it up.
To set the netmask and broadcast use
```
sudo ifconfig <interface> <ip address> netmask <netmask address> broadcast <broadcast address>
```
So for an example on my home network I would use
```
sudo ifconfig 192.168.1.2 netmask 255.255.255.0 broadcast 192.168.1.255
```

**route**
You may have noticed that we haven't setup a gateway yet. To do this you can use the route command.
```
sudo route add default gw <gateway>
```
This just sets the default gateway to the one you specified.

**/etc/resolv.conf**
The other thing we are missing is the dns servers which are set in the /etc/resolv.conf file so you can just
```
sudo nano /etc/resolv.conf
```
and add the nameservers you want to use, one to a line, in the following format.
```
nameserver <nameserver>
```
You can add as many as you want but most isps normally provide two (primary and secondary).

[b]dhclient[b]
Now this is all very well until you want to use dhcp to set up your network which so far I haven't told you how to do. You can use the dhclient program with 

a very simple
```
sudo dhclient <interface>
```
so for the first ethernet interface you would use
```
sudo dhclient eth0
```
and this will look for a dhcp server and tell you the ip address it is given and lets you know when it will expire.

***Wireless networks***
Wireless networks use exactly the same tools as wired networks to set the ip address and all the stuff we have already covered but they need a few more tools 

to connect to a wireless access point.

**iwlist**
The first tool you will want to use is iwlist which can scan for wireless networks nearby and will tell you all about them. To use this program just call
```
iwlist scan
```
and you will see it tell you about any networks that are broadcast in range of your wireless adaptor.

**iwconfig**
To configure the wireless adaptor to connect to the wireless network you can use iwconfig. To do this you will need the essid, the encryption key (if any), 

the channel and the mode. The essid and the channel are given to you when you run "iwlist scan" and the mode is almost always managed for all home routers 

but you can use auto if that doesn't seem to work. The command to use is
```
sudo iwconfig <interface> essid <essid> enc <encryption key> channel <channel number> mode <mode>
```
An example would look like this:
```
sudo iwconfig ath0 essid Home_Network enc a1b2c3d4e5 mode managed channel 6
```
Note that the order of the arguments does not matter as long as the interface is the first argument and the pairs are kept together (essid must be followed 

by the essid of the network etc)

Once you have configured the wireless and are connected to the wireless network you can use ifconfig and route or dhclient to assign an ip address to the 

interface and configure the network.

***Saving the settings***
Currently all the commands so far will be lost on reboot so we need a way to save them. All the networking details are saved in a file under /etc/network 

called interfaces. This file by default configures three ethernet interfaces (eth0, eth1 adn eth2), the lo interface, and two wireless interfaces (wlan0 and 

ath0). These are all brought up by default and each tries to use dhcp to get an ip address. Most people do not have three ethernet interface or both wireless 

interfaces so this will just slow down the system on startup as the computer tries to get an ip address on an interface that isn't there. To remove the 

interfaces you do not have just comment out the two lines for each interface you do not have by adding a hash (#) at the beginning of the lines.

The other thing this file is used for is saving the configuration for wireless and static ip addresses. Below is a sample file which I have edited and 

commented to explain the various options.

```

# /etc/network/interfaces -- configuration file for ifup(8), ifdown(8)

# The loopback interface - just leave it alone normally
auto lo
iface lo inet loopback

# The first network card - this will start on boot and use dhcp to get an ip address
auto eth0 # this line tells it to start on boot
iface eth0 inet dhcp # and this one tells it to use dhcp

#The second network card
#auto eth1 # do not start on boot
iface eth1 inet dhcp # use dhcp to configure it when it is started

auto ath0 # the wireless interface - start on boot
iface ath1 inet static # this interface has a static ip address
  address 192.168.0.2 # the ip address
  netmask 255.255.255.0 # the netmask address
  broadcast 192.168.0.255 # the broadcast address
  gateway 192.168.0.1 # the gateway
	# the wireless stuff is just wireless-(option from iwconfig)
	# the following is the same as the stuff above
  wireless-essid Home_Network
  wireless-enc a1b2c3d4e5
  wireless-channel 6
  wireless-mode managed
	# the nameservers are configured with dns options
	# these are the uk tiscali nameservers so dont use them if you are not in the uk and on tiscali
  dns-nameserver 212.74.112.66
  dns-nameserver 212.74.112.67

```

Finally if you do not use an interface much you can save a configuration for it and choose not to start it on boot so you can start it by using ifup as 

follows
```
sudo ifup <interface>
```
To prevent an interface from starting just comment out the auto line as shown in the second ethernet interface (eth1) in the example above.

This file is used by the networking service to configure the network interfaces and by ifup and ifdown to configure the interfaces when they are brought up 

or down manually by the user.

***The End***
I hope this has helped a few people and taught some people something (even if its only not to read my how-tos in future). If you have any problems then 

please post them in this thread. Don't email me as then other people with the same problem will have to ask again and i don't like repeating myself.

---

