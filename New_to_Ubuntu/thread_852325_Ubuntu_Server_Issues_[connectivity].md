---
title: "Ubuntu Server Issues [connectivity]"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by dreadh3ad on 2008-07-07
I want to familarize myself with Ubuntu server 7.10.  The initial setup and installation went just fine.  However I am having internet issues.  

My computer is sitting behind a Verizon Fios router and receives an IP from the DHCP server.  When the machine reboots it will receive a new IP address.  

I want the ability to log into this machine through the outside internet.  Can somebody point me in the right direction?  Should I give this machine a static IP or is there another option?

I attempted to set up a static ip address for the machine but lost internet connectivity.  However I have no problems when relying on DHCP.  I suspect I may have the netmask or gateway address wrong and or DNS.  

When I am using DHCP, how can I obtain the gateway, netmask and DNS information?

---

### Post by jamesrfla on 2008-07-07
To find your IP address info from your DHCP server type ifconfig into command line. You do need a LAN static IP for the server. When you set that up try going into your routers configuration and try reserving that IP address for your server.

---

### Post by Cypher on 2008-07-07
You should get yourself a router and plug that into into the FIOS router. Then, give your PC a static IP address and connect it to the router. On the router create a route to pass along specific ports of traffic to your PC.

You can then use services like [http://dyndns.org](http://dyndns.org) and [http://no-ip.org](http://no-ip.org) to create a name you can remember. Most new routers will have the facility to keep your account on either of these services updated with your latest DHCP IP address should the router/FIOS modem get power-cycled..

---

### Post by dreadh3ad on 2008-07-07
> **Cypher said:**
> You should get yourself a router and plug that into into the FIOS router. Then, give your PC a static IP address and connect it to the router. On the router create a route to pass along specific ports of traffic to your PC.

You can then use services like [http://dyndns.org](http://dyndns.org) and [http://no-ip.org](http://no-ip.org) to create a name you can remember. Most new routers will have the facility to keep your account on either of these services updated with your latest DHCP IP address should the router/FIOS modem get power-cycled..

Why do I need two routers?

---

### Post by tab1293 on 2008-07-07
If you are trying to connect from over the internet from an outside machine and you are behind. a router, you want the router to have a static IP as well. Depending on your ISP, static IPs aren't handed out to regular customers. 

About the computer having a static IP, your best bet would be to open up the a terminal and type in:
```
ifconfig <Your network device>
```
This will list information about your network connection. Once you have the info you need, open up Ubuntu's network manager and configure a static IP address based on this information.

Make sure from the outside machine you are connecting to the routers IP. You also have to forward the port that you are connecting to. You can check the routers IP and forward the port within the routers web configuration page.

Good Luck.

---

### Post by Cypher on 2008-07-07
> **dreadh3ad said:**
> Why do I need two routers?
If it is really a router, then it should be able to get a DHCP address from Verizon that is Internet accessible and hand out DHCP'ed address on a local network to your PC, like 192.168.1.x or something..

If that is the case, then you don't need another router and everything else I've said still stands..

---

### Post by dreadh3ad on 2008-07-07
Ok,

Lets say I cannot get a static IP address from Verizon.

I need to: 
[LIST]
[*]Sign up for No-Ip
[*]Configure my router to work with no-ip and update when the router's Ip changes
[*]Tell my router to reserve a specific IP for the server
[*]Port forward all traffic from the router to the server
[/LIST]

Do I have this right?

I was looking at ifconfig last night and couldnt isolate the gateway address and netmask.  Can somebody show me where that is with an example?

---

### Post by jamesrfla on 2008-07-07
Yeah sign up for No-ip or Dyndns that has more domain names to pick from. And the rest is right. Good Luck!!

---

### Post by tab1293 on 2008-07-07
You don't have to tell your router to reserve a certain IP for your server, when you configure a static IP for the server on you LAN (By using ifconfig and Ubuntu's network manager) the router will automatically read the config.

---

### Post by dreadh3ad on 2008-07-07
Network Manager?  I was just editing the /etc/network/interfaces file as per the server documentation.

---

### Post by matt79 on 2008-07-07
I would just set your server to a static ip address. That is how I set mine up.


BTW I asked verizon for a static ip address when I first set up my server and they said it was only for business.

You might have to do port forwarding on your router also. From what I know verizon blocks most of their costumers (like me) from incoming connections on port 80. 

if you got any questions feel free to email me.

---

### Post by hrod beraht on 2008-07-07
When you run *ifconfig*, the netmask will show up as 'mask', and will undoubtedly be 255.255.255.0

After that, just sudo nano /etc/network/interfaces:

[INDENT][COLOR="SeaGreen"]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.xxx
netmask 255.255.255.0
gateway 192.168.1.1
broadcast 192.168.1.255
network 192.168.1.0
[/COLOR][/INDENT]
xxx being the address you wish to assign to the server. And after you save that file, don't forget to change that address at your router to tell it to send all http:, SSH, or whatever traffic to that address.

And you also need to restart networking:
[INDENT][COLOR="SeaGreen"]sudo /etc/init.d/networking restart
[/COLOR][/INDENT]

Bob

---

### Post by dreadh3ad on 2008-07-07
Where do i get 'network' & 'gateway' from?

---

### Post by Cypher on 2008-07-07
The Network and Gateway would just point to your router's internal IP address..

---

### Post by matt79 on 2008-07-07
> **dreadh3ad said:**
> Where do i get 'network' & 'gateway' from?

Not sure what you mean. Network should refer to your computer and server set up. Your local network is what you would call everything from your router to the inside of your location. Gateway is what would be considered the base ip address. Normally it is something like :192.168.1.1". It is sort of the gate between your local network and the internet (the big network)

---

### Post by dreadh3ad on 2008-07-07
> **hrod beraht said:**
> 

[INDENT][COLOR="SeaGreen"]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.xxx
netmask 255.255.255.0
gateway 192.168.1.1
broadcast 192.168.1.255
network 192.168.1.0
[/COLOR][/INDENT]

Bob 

What I meant specifically is where do you get the gateway and network address from.  The server documentation did not list network.  I checked my router last night.  (Dont have access atm at work) And I had what i thought was a very different gateway address beginning with 73.  I will check again when I get home.

---

### Post by matt79 on 2008-07-10
The 73 is most likely your IP address that your ISP gives you. What you need to do is link your 73 ip address to your local server address the 192.168.1.xxx.

---

