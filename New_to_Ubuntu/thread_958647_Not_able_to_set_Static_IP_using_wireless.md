---
title: "Not able to set Static IP using wireless"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by ubfu on 2008-10-25
Using Ubuntu 8.04
Router Linksys WRT54G
My PC wireless WMP54G

Sorry I am new to ubuntu , I tried to set it at interface

First try - not working
```
sudo nano /etc/network/interfaces

auto eth0
iface eth0 inet static
address 192.168.1.103
netmask 255.255.255.0
gateway 192.168.1.1 

sudo /etc/init.d/networking restart

```
Second try - not working
```

auto wlan0
iface wlan0 inet static
address 192.168.1.103
netmask 255.255.255.0
gateway 192.168.1.1
```
My router setting
> DHCP Server: Enabled
Starting IP  Address:   192.168.1.100     
Maximum Number of  DHCP Users:  4

Sudo ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:e0:06:09:00:84  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1006 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1006 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:50300 (49.1 KB)  TX bytes:50300 (49.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:e5:fc:1e:b5  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:e5ff:fefc:1eb5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10754 (10.5 KB)  TX bytes:10842 (10.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1E-E5-FC-1E-B5-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```
lshw -C network
```
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 90
       serial: 00:e0:06:09:00:84
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=32 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network:1
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: wmaster0
       version: 00
       serial: 00:1e:e5:fc:1e:b5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.1.101 latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11g
```

Almost a day trying it set it to a static IP address 192.168.1.103.'m totally out of idea hoping someone could help me out.Thank you :)

---

### Post by quirks on 2008-10-25
Hi ubfu,

I ran into this issue not so long ago, too. This is a known deficiency of Network Manager. You simply cannot configure it to use static IP addresses. Fortunatelly, it is supported in version 0.7 / Intrepid: [http://www.ubuntu.com/testing/intrepid/beta#Network%20Manager%200.7](http://www.ubuntu.com/testing/intrepid/beta#Network%20Manager%200.7)

Until then, here is what you can do:
1. Kill Network Manager (go to System -> Administration -> System Monitor, switch to the Processes tab, locate nm-applet and click the End Process button).
2. Configure your static IP using the ordinary config tool (System -> Administration -> Network).

This is how I got it to work. If you have trouble following these steps (I must admit I tested them already a few days ago), tell me.

If everything should fail, maybe you can tell your router to assign the same IP to you PC, whenever it requests one from the DHCP (some routers support that - mine, for example).

---

### Post by ubfu on 2008-10-26
> **quirks said:**
> Hi ubfu,

I ran into this issue not so long ago, too. This is a known deficiency of Network Manager. You simply cannot configure it to use static IP addresses. Fortunatelly, it is supported in version 0.7 / Intrepid: [http://www.ubuntu.com/testing/intrepid/beta#Network%20Manager%200.7](http://www.ubuntu.com/testing/intrepid/beta#Network%20Manager%200.7)

Until then, here is what you can do:
1. Kill Network Manager (go to System -> Administration -> System Monitor, switch to the Processes tab, locate nm-applet and click the End Process button).
2. Configure your static IP using the ordinary config tool (System -> Administration -> Network).

This is how I got it to work. If you have trouble following these steps (I must admit I tested them already a few days ago), tell me.

If everything should fail, maybe you can tell your router to assign the same IP to you PC, whenever it requests one from the DHCP (some routers support that - mine, for example).

Sorry , It doesn't work.I'am using 8.04 hardy and linksys WRT54G.
1.I killed the network manager and the network icon at the panel disappear.
2.Set my static IP at system->adminstration->network wireless setting key then
192.168.1.103
255.255.255.0
192.168.1.1

Not working

Tried using the same method without killing the nm-applet.Went to  system->adminstration->network and set wireless.
The weired thing is the wireless at the network panel is gone.
Totally confuse.Anyone can help out ?:(

---

### Post by jabeez on 2008-10-26
I set up all my static IP's through my router. just had to connect to it, find the MAC address of whatever computer I wanted to set and tell it what IP to assign that MAC address. works like a charm and is probably easier than going the software route.............

---

### Post by melojo on 2008-10-26
I created a file and called it net.sh and added it to /etc/rc.local.  I also had to shut down the gnome network manager

#!/bin/sh -e
#script to start wireless network
dhclient -r wlan0
ifconfig wlan0 192.168.2.5 netmask 255.255.255.0 up
route add default gw 192.168.2.1
iwconfig wlan0 essid "belkin54g"
iwconfig wlan0 key XXXXXX
iwconfig wlan0 key open
iwconfig wlan0 mode Managed
#dhclient wlan0

maybe this will help

---

### Post by ubfu on 2008-10-26
> **jabeez said:**
> I set up all my static IP's through my router. just had to connect to it, find the MAC address of whatever computer I wanted to set and tell it what IP to assign that MAC address. works like a charm and is probably easier than going the software route.............

My router setting only have MAC address filter and permits but not IP address.Using linksys wrt54g

> **melojo said:**
> I created a file and called it net.sh and added it to /etc/rc.local.  I also had to shut down the gnome network manager

#!/bin/sh -e
#script to start wireless network
dhclient -r wlan0
ifconfig wlan0 192.168.2.5 netmask 255.255.255.0 up
route add default gw 192.168.2.1
iwconfig wlan0 essid "belkin54g"
iwconfig wlan0 key XXXXXX
iwconfig wlan0 key open
iwconfig wlan0 mode Managed
#dhclient wlan0

maybe this will help

Sorry I don't quite understand , I am new to ubuntu.
At etc , there is a file called rc.local but not a folder.
I try to create a folder 
sudo cd /etc/
sudo mkdir rc.local
but it doesn't allow.

Can you kindly guide me through the process ? Thank you :)

---

### Post by quirks on 2008-10-26
You are not supposed to create a directory in /etc. There already is a file called rc.local. You are supposed to paste the code which melojo provided you into this file. BTW, the reason why it won't let you create a directory is because there already is a file with the same name.

If the rc.local thingy does not work out (you have to reboot to apply the changes), you might also want to try setting the IP/etc. manually in a terminal. I also noticed that the administration tool provided by Ubuntu often does not work as expected (it's a shame). So, if the suggestion with the rc.local file does not work, do the following:
1. Kill nm-applet as I outlined earlier.
2. Open a terminal.
3. Adjust the following code as needed and paste it into a terminal:
```
ip addr flush dev wlan0
ip link set wlan0 up
ip addr add 192.168.1.103/24 dev wlan0
ip route add to default via 192.168.1.1
```
4. Enter the following command in a terminal:
```
echo "nameserver 192.168.1.1" >> /etc/resolv.conf
```
This will register your router as a DNS server on your client PC.

---

### Post by ubfu on 2008-10-26
> **quirks said:**
> You are not supposed to create a directory in /etc. There already is a file called rc.local. You are supposed to paste the code which melojo provided you into this file. BTW, the reason why it won't let you create a directory is because there already is a file with the same name.

If the rc.local thingy does not work out (you have to reboot to apply the changes), you might also want to try setting the IP/etc. manually in a terminal. I also noticed that the administration tool provided by Ubuntu often does not work as expected (it's a shame). So, if the suggestion with the rc.local file does not work, do the following:
1. Kill nm-applet as I outlined earlier.
2. Open a terminal.
3. Adjust the following code as needed and paste it into a terminal:
```
ip addr flush dev wlan0
ip link set wlan0 up
ip addr add 192.168.1.103/24 dev wlan0
ip route add to default via 192.168.1.1
```
4. Enter the following command in a terminal:
```
echo "nameserver 192.168.1.1" >> /etc/resolv.conf
```
This will register your router as a DNS server on your client PC.

The rc.local didn't work.Was able to connect to the router but not the internet

Tried your code too but I get a message not permitted 

```
ip addr flush dev wlan0
Nothing to flush.
ip link set wlan0 up
RTNETLINK answers: Operation not permitted
ip addr add 192.168.1.103/24 dev wlan0
RTNETLINK answers: Operation not permitted
ip route add to default via 192.168.1.1
RTNETLINK answers: Operation not permitted

echo "nameserver 192.168.1.1" >> /etc/resolv.conf
bash: /etc/resolv.conf: Permission denied
```

---

### Post by tubegeek on 2008-10-26
I'm happy to see this thread active.

I recently upgraded to the 8.10 beta (getting ahead of the crowds?) and now a static route is damaged. This route was set up using the gnome network manager GUI and worked fine for a long time under 8.04. Now the LAN seems to work fine - so the static IP address part seems to be working fine - but the access to the internet etc., was broken, with no ability to resolve domains. I could ping numerical addresses but not domain names, for example.

I did this (the echo command given above did not work)

In a terminial I typed:

code:
sudo gedit /etc/resolv.conf

In the text editor window I added this line:
code:
nameserver 192.168.0.1

And then I quit the text teditor and rebooted.

All is well - THANKS!!

---

### Post by ubfu on 2008-10-27
> **tubegeek said:**
> I'm happy to see this thread active.

I recently upgraded to the 8.10 beta (getting ahead of the crowds?) and now a static route is damaged. This route was set up using the gnome network manager GUI and worked fine for a long time under 8.04. Now the LAN seems to work fine - so the static IP address part seems to be working fine - but the access to the internet etc., was broken, with no ability to resolve domains. I could ping numerical addresses but not domain names, for example.

I did this (the echo command given above did not work)

In a terminial I typed:

code:
sudo gedit /etc/resolv.conf

In the text editor window I added this line:
code:
nameserver 192.168.0.1

And then I quit the text teditor and rebooted.

All is well - THANKS!!

It doesn't do anything at all.I set it but it get reset on the next restart.

---

### Post by quirks on 2008-10-28
Oh, I'm sorry, ubfu. I should have mentioned that the commands I gave you are to be run as root. Prefix every command by "sudo". I usually enter "sudo -s", giving me permanent root privileges. And then I forget about all the sudoing. Again, sorry.

So in short: follow the instructions I posted earlier and prepend a "sudo" to each command. Hope it works this time ...

---

