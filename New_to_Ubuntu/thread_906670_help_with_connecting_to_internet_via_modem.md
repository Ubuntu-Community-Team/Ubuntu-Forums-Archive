---
title: "help with connecting to internet via modem"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by babyblow10 on 2008-08-31
i tried setting the connection to dhcp and tried static ip none would work...i tried pppoeconf and that wouldnt work...

***_heres my ifconfig info_***

eth0      Link encap:Ethernet  HWaddr 00:0c:6e:f7:75:d5  
          inet addr:192.168.1.136  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:fef7:75d5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xb400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:310826 (303.5 KB)  TX bytes:310826 (303.5 KB)

[B][I][U]
AND HERES lshw -C Network info[/U][/I][/B]

  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: f
       bus info: pci@0000:01:0f.0
       logical name: eth0
       version: 10
       serial: 00:0c:6e:f7:75:d5
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.136 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s




can anyone help me out if u need more info tell me and ill get it for u

---

### Post by halitech on 2008-08-31
how do you physically connect to the internet? (ie, direct to modem, through a router with a wired connection, wirelessly through a router?)

---

### Post by babyblow10 on 2008-08-31
> **halitech said:**
> how do you physically connect to the internet? (ie, direct to modem, through a router with a wired connection, wirelessly through a router?)

router through wired connection which i just now noticed lol

---

### Post by halitech on 2008-08-31
then by the looks of this ```
eth0 Link encap:Ethernet HWaddr 00:0c:6e:f7:75:d5
inet addr:192.168.1.136 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::20c:6eff:fef7:75d5/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:17 Base address:0xb400 
``` you should be connected :)

---

### Post by babyblow10 on 2008-08-31
hmm well when i go on firefox nothing loads i cant even get on the routers page..and i enabled that ipv6 to true on firefox

---

### Post by halitech on 2008-08-31
ok, post the info from
```
cat /etc/network/interfaces
``` and ```
sudo ifconfig
```

also, try disabling ipV6, its not widely adopted yet and it could be causing some issues.

---

### Post by babyblow10 on 2008-08-31
> **halitech said:**
> ok, post the info from
```
cat /etc/network/interfaces
``` and ```
sudo ifconfig
```

also, try disabling ipV6, its not widely adopted yet and it could be causing some issues.

k i posted ifconfig on top but ill go and do the other command right now ill brb

---

### Post by babyblow10 on 2008-08-31
heres cat /etc/network/interfaces

auto lo
iface lo inet loopback



iface eth0 inet dhcp
address 192.168.1.136
netmask 255.255.255.0
gateway 192.168.254.254

auto eth0

---

### Post by halitech on 2008-08-31
I don't think you can have a static IP and DHCP set for the same interface. Try removing the static info and restart networking

```
gksu gedit /etc/networking/interfaces
```
then do
```
sudo dhclient eth0
```

also, what is the IP address of the router?

---

### Post by babyblow10 on 2008-08-31
yea only dhcp is setup i took off the static ip..and the router is 192.168.1.1

---

### Post by halitech on 2008-08-31
ok, what was the result of ```
sudo dhclient eth0
```

---

### Post by babyblow10 on 2008-08-31
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0c:6e:f7:75:d5
Sending on   LPF/eth0/00:0c:6e:f7:75:d5
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by babyblow10 on 2008-08-31
have u figured out whats wrong?

---

### Post by halitech on 2008-08-31
ok, looks like your router isn't giving an address out for some reason. I've run into the same thing with mine and I had to set a static ip address. 

go in and set a static ip but drop your number down to 192.168.1.110 as 136 may be outside the range that the router is setup to recognize. Then, power down your router, wait 45 seconds and power it back up and restart the computer

---

### Post by babyblow10 on 2008-08-31
i do that on network configuration right

---

### Post by halitech on 2008-08-31
you can do it with the manual network configuration or by
```
gksu gedit /etc/networking/interfaces
``` from the terminal

---

### Post by babyblow10 on 2008-08-31
k i tried that and still not able to load pages or get on the routers page

---

### Post by halitech on 2008-08-31
ok, time to start checking the hardware side of things. The port on your router where the cable is plugged in for this computer, is the light on with the cable plugged in and if you unplug it from the computer, does it go out?

---

### Post by babyblow10 on 2008-08-31
> **halitech said:**
> ok, time to start checking the hardware side of things. The port on your router where the cable is plugged in for this computer, is the light on with the cable plugged in and if you unplug it from the computer, does it go out?

yea when i unplugged the ethernet thats connected from the comp to the router the light went off

---

### Post by halitech on 2008-08-31
is there any other computers using this connection?

---

### Post by babyblow10 on 2008-08-31
yea wirelessly upstairs

---

### Post by halitech on 2008-08-31
ok, check the IP address on that machine and see if it is matching what we are trying to use. Also, did you do a reboot on the router?

---

### Post by babyblow10 on 2008-08-31
nope its not and yea i did

---

### Post by halitech on 2008-08-31
they don't match? what is the IP address upstairs and are you sure its connected to your router?

---

### Post by babyblow10 on 2008-08-31
192.168.1.2

yea cuz the internet is working and its listed on my routers page

---

### Post by babyblow10 on 2008-08-31
k i tried doing the mac filter cuz i had to do that for ps3 to work and that didnt help either

---

### Post by halitech on 2008-08-31
ok, maybe we need to drop down even farther if your machine that is working is 192.168.1.2, maybe 192.168.1.110 is even too high, try to change it to 192.168.1.10 then reboot the computer

---

### Post by babyblow10 on 2008-08-31
still aint working

---

### Post by halitech on 2008-08-31
can you try removing the router temporarily and see if you can connect with a dhcp address?

---

### Post by babyblow10 on 2008-08-31
yea ill try that right now

---

### Post by babyblow10 on 2008-08-31
alright the ethernet light aint turning on on the modem for somereason so its only working through the rourter right now

---

### Post by babyblow10 on 2008-09-01
bump 
can anyone help me out with this

---

### Post by halitech on 2008-09-01
so no light when plugging into the modem but you say you do get a light when connecting from the router to the computer? something sounds fishy to me as the cable from the modem to the computer should be a patch cable which would be the same as going from the router to your computer so either they should both work or neither should work

---

### Post by babyblow10 on 2008-09-01
yea i dont get it..i even tried 2 different cables and different slots on the modem still didnt come up

---

### Post by halitech on 2008-09-01
> **babyblow10 said:**
> yea i dont get it..i even tried 2 different cables and different slots on the modem still didnt come up

ummmmmm different slots on the modem? modems typically only have 1 port to plug an ethernet connection into. what is the make and model of your modem?

---

### Post by babyblow10 on 2008-09-01
the modem has a router in it itself i guess cuz it has a light thing for wireless and has an atenna but idono how to use it...

speedstream 6520
wireless adsl gateway

---

### Post by halitech on 2008-09-01
ok, so you have 2 seperate devices and the cable gives you a light when you plug into the second device?

---

### Post by babyblow10 on 2008-09-01
k i took out the router and now im just using the modem and have the wireless setup too so thats good now i dont need the router now ill try ubuntu again

---

### Post by babyblow10 on 2008-09-01
the ethernet light still dont come on under ubuntu..do i need to install drivers or something?

---

### Post by halitech on 2008-09-01
the lights indicate a physical connection so either the cable is wrong, the ports on the modem are not turned on or the nic in the computer is shot. Maybe call your ISP and see if you have to do anything with them if you are sure all your hardware is fine.

---

### Post by babyblow10 on 2008-09-01
well its working perfectly fine when im on windows but when i boot into ubuntu it dont come on so it must be a ubuntu problem

---

### Post by babyblow10 on 2008-09-01
k i tried using usb instead of ethernet in ubuntu and the light came on but i still couldnt get a connection

---

