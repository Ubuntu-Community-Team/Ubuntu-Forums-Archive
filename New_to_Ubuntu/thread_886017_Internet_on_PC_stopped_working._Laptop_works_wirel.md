---
title: "Internet on PC stopped working. Laptop works wirelessly."
date: 2008-08-10
forum: New to Ubuntu
---

### Post by capricon on 2008-08-10
Internet on PC stopped working(Connected via ethernet). Laptop still works wirelessly  on the Netgear router.

Please help. 

Ran - dmesg | grep eth and go the following.
[B]
[COLOR="Red"]eth0: no IPv6 routers present[/COLOR[/B]]

```

linux-bglm:/home/arsa # dmesg | grep eth
Parsing all Control Methods:
Table [DSDT](id 0001) - 508 Objects with 49 Devices 121 Methods 14 Regions
Parsing all Control Methods:
Table [SSDT](id 0002) - 1 Objects with 0 Devices 1 Methods 0 Regions
Parsing all Control Methods:
Table [SSDT](id 0003) - 5 Objects with 0 Devices 3 Methods 0 Regions
Initializing Device/Processor/Thermal objects by executing _INI methods:.
Executed 1 _INI methods requiring 0 _STA executions (examined 53 objects)
eth1: RealTek RTL8139 at 0xdeea0800, 00:03:25:1c:6e:53, IRQ 10
eth1:  Identified 8139 chip type 'RTL-8101'
eth1: link down
ADDRCONF(NETDEV_UP): eth1: link is not ready
ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
eth0: no IPv6 routers present
ADDRCONF(NETDEV_UP): eth0: link is not ready
ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
ADDRCONF(NETDEV_UP): eth0: link is not ready
ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
eth0: no IPv6 routers present
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=224.0.0.251 LEN=64 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=44 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=224.0.0.251 LEN=370 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=350 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=224.0.0.251 LEN=260 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=240 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=224.0.0.251 LEN=370 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=350 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=224.0.0.251 LEN=370 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=350 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=224.0.0.251 LEN=340 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=320 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=224.0.0.251 LEN=182 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=162 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=224.0.0.251 LEN=182 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=162 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=224.0.0.251 LEN=64 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=44 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=224.0.0.251 LEN=182 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=162 
eth0: no IPv6 routers present
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=224.0.0.251 LEN=64 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=44 
SFW2-INext-DROP-DEFLT IN=eth0 OUT= MAC= SRC=192.168.1.3 DST=224.0.0.251 LEN=64 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=44 

```

---

### Post by nicedude on 2008-08-11
Looks to me like maybe your Ethernet connection was set up as IPv4 address and then due to installing something network managing related or maybe just a system update it is now setting up as an IPv6 address which your router can't handle. One Test/Solution is to use ifconfig at command line to configure the interface by hand so you can see if I am right. If you know what your routers LAN IP is ( not your internet IP address but the router LAN address which will be something like 192.168.0.1 or 192.168.1.1 ) then you could easily run the following command in a terminal

sudo ifconfig eth0 inet 192.168.0.6 

just change the 192.168.0 part to what your router uses and the 6 should be cool unless you have more than 5 computers hooked up to the router. 90+% of all home routers use either 192.168.1 or 192.168.0 as the base address for your local network but you cn always google your model # or look with another PC at the network and see what it is using.

then you would need to run a command to register the connection with the router I think. I think you can just use dhclient program to do that like follows

sudo dhclient eth0

then if I am correct you would be connected to the internet again. If that works though you will need to do some research and change your network interfaces file located at /etc/network/interfaces

mine looks like the following, although yours may be different

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
auto lo eth0
iface lo inet loopback

You can view and edit your interfaces file with the following command but first I will give you a command to back it up so you still have a copy of the original in case something goes wrong.

THIS WILL BACK IT UP
sudo cp /etc/network/interfaces /etc/network/interfaces.bak

THIS WILL LET YOU EDIT IT
sudo gedit /etc/network/interfaces

and make sure whatever is in yours doesn't include inet6 and if it does change those references to inet - so you go back to IPv4 addressing system instead of IPv6.

Hope I am right and this helps you out or at least gets you on the right track but I am 99% sure its a IPv6 problem and your router just doesn't support the new IPv6 standard

Nicedude

---

### Post by capricon on 2008-08-11
Thanks.
I tried all you said


sudo ifconfig eth0 inet 192.168.1.1
etc still not working.

Ran ifconfig from my laptop and getting the following info. Dont know if it helps

```
eth0      Link encap:Ethernet  HWaddr 00:0E:35:94:BE:43  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe8f::20e:35f5:fe9f:be43/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4568 errors:1 dropped:1 overruns:0 frame:0
          TX packets:3928 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:3223633 (3.0 Mb)  TX bytes:784144 (765.7 Kb)
          Interrupt:10 Base address:0x2000 Memory:e0200000-e0200fff 

eth1      Link encap:Ethernet  HWaddr 00:04:25:1F:6E:53  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x4800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:74 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4420 (4.3 Kb)  TX bytes:4420 (4.3 Kb)

```

---

### Post by nicedude on 2008-08-12
First thing I see in your ifconfig output is that there are 2 ethernet connections eth0 & eth1 - unless you have 2 wired network inteterfaces then this is wrong for a start. More info could help as well and at the end of this I will list some things that could help. Also you shouldn't have run that command using 192.168.1.1 as that would give your Ethernet adapter an IP that would be a router address not a client address, I will try to explain. Home network routers have a base address that is assigned to them, most home routers will use 192.168.0.1 or 192.168.1.1 as the base address for the router. The router will then assign client machines that you connect to it via Ethernet cable an address of their own, the router will just assign an address one number higher on the same network range, for example if your router is using 192.168.0.1 then the first machine plugged in would be given an address of 192.168.0.2 the next would get 192.168.0.3 and so on. This assignment of addresses is called DHCP and your router will only assign and talk to devices usually 25-50 numbers past its own by default, so the max for the example above would be something like 192.168.0.50. if your PC's Ethernet is assigned an IP address outside that range then your router won't listen to it no matter if you do assign the PC an IPv4 address.

Now I am still most certain that your main reason your Ethernet stopped working is due to your router not handling an IPv6 ( the new standard not yet fully adopted and not supported by all routers ) address but what I was trying to get you to do is run commands to first assign your Ethernet interface an IPv4 ( the standard for years ) and then tell it to talk to the router ( with a dhcp registration command ). Why your PC suddenly started using an IPv6 when it was using IPv4 ( I am assuming since you said it did work ) I don't know, but would like to.

To find out what your Routers settings are I would recommend connecting to it via wireless ( you said it is working right? ) and then open Firefox web browser, then in the address bar at top (not google etc but the address bar) clear out what ever is there and type 192.168.0.1 and hit enter. You should be given a prompt for name and password, if not then try 192.168.1.1 but my netgear routers have always been (192.168.0.1). Once you get the login window you enter your credentials ( if you have never changed this then it would be ( name -> admin )( password -> admin or password ) you should also change the router password once logged in as leaving it as default is a big security risk. Once you are logged into your routers configuration interface you can look at all your settings. Somewhere in these settings will be one called "address reservation" with it you can enter a mac address ( the one for your wired network adapter ) yours should be 00:0E:35:94:BE:43 from what I see in your iwconfig. Then assign that machine a static IP say 192.168.0.5 and then if you were to assign your Ethernet card to that IP as well ( like you tried before only with 192.168.0.5 at the end ) then it should work ( but they have to be the same on both the PC & router to work).

Here are some things that would maybe help me help you further if you can't get any further with the above advice.

1. More system info - basically how many network adapters are present? 

2. Use this command to make a copy of your network interfaces file on your desktop & then open it and copy and paste the contents of it here. Here is a command to do that, after you run this there will be a new file on your desktop called interfaces.txt. I can probably just mod it for you when we figure out what your routers base IP address is

cp /etc/network/interfaces ~/Desktop/interfaces.txt

3. More info on the "it stopped working" statement. Did it work before and if so did it seem to work correctly? Do you know if it stopped directly after a system update or did you install anything new that is at all network related? I would like to know this since I would just like to know what caused the behavior.


Above all don't worry you be figuring this out soon and you will have learned some stuff in the process :-)

nicedude

---

### Post by capricon on 2008-08-12
Thank you again.

1. More system info - basically how many network adapters are present?
 
My router is connected by wire/ethernet cord to my PC and wirelessly to the laptop.
There is only one ethernet adapter on the PC (part of motherboard).
 
2. Use this command to make a copy of your network interfaces file on your desktop & then open it and copy and paste the contents of it here. Here is a command to do that, after you run this there will be a new file on your desktop called interfaces.txt. I can probably just mod it for you when we figure out what your routers base IP address is 
cp /etc/network/interfaces ~/Desktop/interfaces.txt

please see at the bottom
 
3. More info on the "it stopped working" statement. Did it work before and if so did it seem to work correctly? Do you know if it stopped directly after a system update or did you install anything new that is at all network related? I would like to know this since I would just like to know what caused the behavior.
 
Sorry. Here is the info.
I assembled this PC 8 months ago, installed ubuntu and thank god, it started working right from the get go. Never had any problem until recently, when I tried to use the sound output, realized that the sound is not working. I tried to trouble shoot it few days ago using a guide in this site and I was stuck in the middle of the process. Other than that there was no changes made to my PC or router and it was working
perfectly.
While trouble shooting this internet problem, I might have screwed up more trying something randomly (ex: i remember running some command like default gw 192.168.1.1 etc)



I tried the "address reservation" that you mentioned (assigned 192.168.1.2). Now the PC is trying to connect to the router and it says "connection established" But not able to connect to internet (attached screen print of latest connection view).


Display of my /etc/network/interfaces  (modified yesterday)

```
auto lo
iface lo inet loopback

auto etho
iface eth0 inet dhcp.
```

---

### Post by nicedude on 2008-08-12
Ok more than likely your router ( since you said its a netgear ) will be 192.168.0.1 and you should try 192.168.0.2 as your IP for the interface and then run the dhclient command to register with the router. Since I see you have 2 PC's now and this is a desktop you are trying to get the ethernet to work on so that clears up what your situation is. 192.168.1.2 is usually a linksys router client address not a netgear so just follow this advice.

Try running these 2 exact commands, just cut and paste them

ifconfig eth0 inet 192.168.0.3

AND THEN

sudo dhclient


You should now be connected to your router and have internet.


Also you should defiantly make sure you log onto your router and set up its security if you have not already done so. Since if you leave your wifi unsecured then someone can connect to your router then log on to it and they can setup your security for you, without your knowledge, permission or best interest at heart :-( . They could also then scan any other machines on your network and cause all kinds of havoc. I don't know if you have set up your routers security yet but thought maybe you haven't. Remember to at least set the router password to something secure ( use at least numerals and numbers and at least 7 digits ) and also you should configure it to use WEP encryption at the minimum WPA though if you can get it to work. these 2 things are vital to not having bad things happen , trust me.

nicedude

---

### Post by capricon on 2008-08-13
Thanks.

I did the following and its still not working.

FYI. On the router i did the "address reservation" yesterday and the IP address reserved for the PC LAN is 192.168.1.2.


```

root@arsa-desktop:/home/arsa# ifconfig eth0 inet 192.168.1.3

root@arsa-desktop:/home/arsa# dhclient
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:19:21:33:c2:12
Sending on   LPF/eth0/00:19:21:33:c2:12
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
root@arsa-desktop:/home/arsa# 

root@arsa-desktop:/home/arsa# dmesg | grep eth
[    3.702218] eth0: VIA Rhine II at 0x1ee00, 00:19:21:33:c2:12, IRQ 18.
[    3.702933] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[   12.804889] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  166.886302] eth0: no IPv6 routers present

root@arsa-desktop:/home/arsa# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
**default         192.168.1.1     0.0.0.0         UG    0      0        0 et**h0
root@arsa-desktop:/home/arsa# 


```


Bye the way, i appreciate your concern about the router admin/pwd and WPA. Thats the first thing i did when i set up router a couple of years ago. I am careful about those to the extend i know things :-)

By the i dont know if the default gw 192.168.1.1 command i used before i posted the problem here is causing any issue(bolded above).

---

### Post by nicedude on 2008-08-13
Ok if you assigned your PC to 192.168.1.2 then you will need to use that address for your PC I just sain to use 192.168.1.3 in case anything else had already been assined 192.168.1.2. Actually last night when I looked at your screenshot of your interface I saw also your netmask and gateway were messed up too I think so I am just going to give you some screenshots on what yours should say for your setup and how to set it up.

Just follow the screenshots and tell me if this gets you going.

nciedude

---

### Post by capricon on 2008-08-14
Thanks lot.
Its working now. I didn't do anything today. After last night's changes,i i restarted, still the same problem. The only thing different i can think of is this morning, i unplugged the power and powered back in. Logged back on - its  working.
Thanks again for your help. If you need any further current information, plese let me know. Ifconfig is showing 192.168.1.5 even the router reserved 192.168.1.2 for the pc mac address.

I was on the verge of moving to SUSE when i had this issue on the top of the sound problem i am having. You helped me.

---

### Post by nicedude on 2008-08-14
Glad its working and hope you stay here with Ubuntu as Suse will probably be just a restart of same types of problems for you to fix. At least once you get things fixed they usually stay fixed and you learn a bunch of stuff in the process ( like how to bang your head on the wall :-) )

---

