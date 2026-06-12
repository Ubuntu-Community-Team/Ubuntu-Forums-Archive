---
title: "Network problems"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by Contemporani on 2008-05-17
Hi!

I'm a newbie to the Linux world. I'm trying to make Ubuntu 8.04 work in a couple of computers to be able to change my entire network, learn and hopefully be part of the Ubuntu community soon.

Before joining these forums and posting this message I've read a lot of information and tried several things myself, but I can't make it work alone.

My network has several computers, NAS, printers, a VOIP system... I work with fixed IP addresses.

After installing Ubuntu 8.04 in two computers, they both can connect to the Internet with the options by default (roaming mode), wired and wireless.

If I select the manual mode and type the fixed IP addresses (plus subnet plus gateway) the computers have when using Windows (dual boot still), the Internet connection just does not work in any of the computers. Nor wired nor wireless.

I would like to work only with fixed IP addresses for several reasons: opening ports in the router, sharing devices...

If you have any clue of why it is happening and how to get connection selecting the IP addresses myself without using the 'roaming mode', please answer, I would be very grateful.

Please check below the attached result of IPCONFIG in different scenarios (HWaddr masked).

Thanks,

Contemporani

---

IFCONFIG WHEN CONNECTED WIRELESS (ROAMING)

eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fee0:447e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:321 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:356439 (348.0 KB)  TX bytes:37895 (37.0 KB)
          Interrupt:17 Base address:0xe000 Memory:c8218000-c8218fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1474 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1474 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78744 (76.8 KB)  TX bytes:78744 (76.8 KB)

IFCONFIG WHEN CONNECTED WIRED (ROAMING)

eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX    
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe9b:53b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:164 errors:0 dropped:0 overruns:0 frame:0
          TX packets:163 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:169912 (165.9 KB)  TX bytes:21349 (20.8 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX    
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3167 errors:0 dropped:0 overruns:0 frame:0
          TX packets:450 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:359397 (350.9 KB)  TX bytes:38343 (37.4 KB)
          Interrupt:17 Base address:0xe000 Memory:c8218000-c8218fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1474 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1474 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78744 (76.8 KB)  TX bytes:78744 (76.8 KB)

IFCONFIG WHEN SELECTED FIXED IP (NO CONNECTION)

eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX    
          inet6 addr: fe80::2c0:9fff:fe9b:53b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1482 (1.4 KB)  TX bytes:492 (492.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX    
          inet addr:192.168.1.251  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fee0:447e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:12 dropped:12 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:362317 (353.8 KB)  TX bytes:45030 (43.9 KB)
          Interrupt:17 Base address:0xe000 Memory:c8218000-c8218fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1485 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1485 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:80044 (78.1 KB)  TX bytes:80044 (78.1 KB)

---

### Post by RWells on 2008-05-17
I am a noob so use my info with care.

The way I did this.

First I log into my router and tell it to assign a static ip to the machine I want to have static ip,

Then on the machine in question.

system>Administration>Network

at this point point I have a conections tap which allows me to assign the static ip the router assigned.

Hope this helps a little , if nothing else maybe a free bump

Rusty

---

### Post by Aearenda on 2008-05-17
Contemporani, it would be useful to see the output from the following commands in static mode:
```
cat /etc/networks/interfaces
route
cat /etc/resolv.conf
```

The last one is where the DNS settings are saved. You haven't mentioned DNS - you need to set this as well when not roaming.

---

### Post by Contemporani on 2008-05-17
Thanks RWells and Aearenda for your quick replies.

Below the information requested by Aearenda (Please note that I stated as DNS the IP address of the router, like I do this in M$ Windows):

COMMAND: cat /etc/network/interfaces

auto lo
iface lo inet loopback

iface eth1 inet static
address 192.168.1.251
netmask 255.255.255.0
gateway 192.168.1.254
wireless-essid Water

auto eth1

iface eth0 inet static
address 192.168.1.251
netmask 255.255.255.0
gateway 192.168.1.254

auto eth0

---
COMMAND: route

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.254   0.0.0.0         UG    100    0        0 eth0

---
COMMAND: cat /etc/resolv.conf

### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4900
#
### END INFO

nameserver 192.168.1.254

---

### Post by Contemporani on 2008-05-17
I've just noticed that under the command "cat /etc/network/interfaces" it appears the same IP (192.168.1.251) twice. That's a coincidence because of the last configuration, I also tried different IP addresses in the same range.

---

### Post by RWells on 2008-05-17
Ok Im not reall sure whats going on there,

What is the address you use to log in to router?

---

### Post by Contemporani on 2008-05-17
The address of my router is 192.168.1.254, the same I use as DNS server and gateway. At least it is the way that always worked in M$ Windows O:-)

---

### Post by RWells on 2008-05-17
> **Contemporani said:**
> The address of my router is 192.168.1.254, the same I use as DNS server and gateway. At least it is the way that always worked in M$ Windows O:-)


Ok I feel real over my head here but, somthing doesnt seem right to me about that, I thought the router would only assign addresses higher than itself?

Have you logged into the router itself and told it to assign a static ip to the machine in questioin?

---

### Post by Contemporani on 2008-05-17
Well, the DHCP server is off in the router, I assign all IP addresses manually.

I didn't change the IP address of the router given from the manufacturer, which is the highest of the range (254). If the DHCP server was on, all assigned IP addresses would be obviously lower :-)

---

### Post by RWells on 2008-05-17
> **Contemporani said:**
> Well, the DHCP server is off in the router, I assign all IP addresses manually.

I didn't change the IP address of the router given from the manufacturer, which is the highest of the range (254). If the DHCP server was on, all assigned IP addresses would be obviously lower :-)


Ok I dont understand this enough to do you any good.

I have DHCP on,so this will be the differnce between you system and mine.

Why do you have DHCP off?

Rusty

---

### Post by Contemporani on 2008-05-17
Since all my network has static IP addresses, I simply don't need a DHCP server. :)

---

### Post by RWells on 2008-05-17
> **Contemporani said:**
> Since all my network has static IP addresses, I simply don't need a DHCP server. :)

Ok I probabley dont understand this as well as you.
All my network has static ip addresses, but my router says I have to have DHCP.

On my system the router assings the static ip addresses, after I choose what address I want for each machine.


Rusty

---

### Post by Contemporani on 2008-05-17
Thank you very much for your help, Rusty. I'm afraid my problem needs to be attacked from a different angle :)

---

### Post by Contemporani on 2008-05-17
Oops.

I forgot to explain that the only peculiarity of my network is that the router doesn't support NetBIOS (Windows WINS settings), but I have no clue if this affects Ubuntu.

Any suggestions of how to solve my problem are very welcome :)

---

### Post by jediborger on 2008-05-17
I just had your same issue with a fresh install of Hardy myself. I've seen this before and NetworkManager doesn't like to play with manual configurations. You should disable nm-applet, the network applet in the system tray. Go to System-Preferences-Sessions and uncheck Network Manager. Log out and log back in. Now go to System-Administration-Network make sure your settings are correct, uncheck the check box and check it again. This will refresh the config and if all goes well your network should be up. Hope this helps.

---

### Post by Aearenda on 2008-05-17
Sorry it has taken me so long to reply, it's been night here and next I need to go out! However...

I see two things in your config:
1. The IP address clash needs to be fixed - it won't work like that unless only one interface is up at a time, but you have both of them in 'auto'.
2. Likewise, only one interface should have an active gateway address. If both interfaces are to be up, then one of them needs the gateway removed.

I don't understand jediborger's comment - disabling nm-applet only disables the network manager UI, not the core service, so I don't see how this changes anything. I usually completely uninstall network manager on machines where it is not to be used. I have heard it said that WiCD copes better with this kind of setup, but I have never tried it.

Lack of WINS should not cause the problem described here - it is a name resolution service, like DNS, not a transport.

---

### Post by Contemporani on 2008-05-18
Thanks jediborger for your reply.

Unfortunately your solution did not solve the problem. I will keep trying :)

---

### Post by Contemporani on 2008-05-18
Thanks again, Aearenda.

It's great that you spend your free time in solving problems, sure I won't complain if you need some sleep :D

Answering your post, I've already changed the IP addresses manually into 192.168.1.251 and 192.168.1.249. They cannot work at the same time because one is a wireless connection and the other one is a wired one and the Network Manager only allows one at the time (if I'm not wrong).

Also thanks for the educational note of WINS, it helped not to take it out on the router.

If I misunderstood your post, please note that today is my second day in the Ubuntu world ;)

---

### Post by Aearenda on 2008-05-18
I hope you are enjoying Ubuntu! Apart from this problem, of course :-)

Network manager only works with network interfaces that are set in to 'roaming mode', which means their settings are absent from /etc/network/interfaces. In your case, I don't think Network Manager should be doing anything with these interfaces. This is why you should either remove one of the gateway settings, or remove one of the 'auto' settings and manage things so that only one interface is enabled at once.

---

