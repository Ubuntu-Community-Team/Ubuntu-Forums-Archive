---
title: "Noob and problems with Wireless card"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by malebolges on 2008-09-07
Hello, I am a new user and as you can see from the tittle of my post I am having issues configuring the wireless card of my laptop Sony VGN-AR320E.
I have been trying to read other posts before asking, but I cant seem to find the solution to my wireless problems. If I am not mistaken my wireless card is supported on Ubuntu 0.84 Tls, one more thing is that the WLAN indicator wont turn but this is only on ubuntu, so I might be missing something to make it work. I am using a linksys WRT54G router, which I also use on windows vista without problems and I am using WPA Personal security.
After doing 
lshw -C network
This is what I get:
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:d5:ae:b5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:0a:08.0
       logical name: eth0
       version: 02
       serial: 00:13:a9:82:fb:3b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.1.100 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes

After doing  sudo pppoe-start
This is what I get.
sudo: pppoe-start: command not found

I hope you can guide me trough the process of setting up my wireless network 
Thanks in advance.

---

### Post by bobnutfield on 2008-09-07
There are a lot of threads about your wireless card.  You just need to put the chipset model in the search engine.  Also, here is a link that will be of help to you:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

Open a terminal and type:

> sudo ifconfig -a

and post the results back.

---

### Post by Sameer kumar on 2008-09-07
to enable your wifi led just edit /etc/sysctl.conf:type gedit /etc/sysctl.conf and add this at the end of the file and save 

dev.wifi0.ledpin=1

dev.wifi0.softled=1 

reboot and thats it!!!!!!!!!!!!!!

man ifconfig & man iwconfig for wireless solutins!!!

---

### Post by malebolges on 2008-09-07
After doing the sudo ifconfig -a I got this. Sorry for taking this long but I had to do some other stuff

eth0      Link encap:Ethernet  HWaddr 00:13:a9:82:fb:3b  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:a9ff:fe82:fb3b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:592 errors:0 dropped:0 overruns:0 frame:0
          TX packets:501 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:738539 (721.2 KB)  TX bytes:56551 (55.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2340 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2340 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:117000 (114.2 KB)  TX bytes:117000 (114.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:d5:ae:b5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-D5-AE-B5-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


And for the second solution, It wont let me do anything, it answers
Warning: unknown mime-type for "/etc/sysctl.conf:type" -- using "application/*"
Warning: unknown mime-type for "gedit" -- using "application/*"
Warning: unknown mime-type for "/etc/sysctl.conf" -- using "application/*"
Error: no write permission for file "/etc/sysctl.conf:type"
Error: no "edit" mailcap rules found for type "application/*"
Error: no write permission for file "/etc/sysctl.conf"
phoenix@Mazinkaiser:~$ /etc/sysctl.conf:type gedit /etc/sysctl.conf
bash: /etc/sysctl.conf:type: No such file or directory

---

### Post by bobnutfield on 2008-09-07
> 
wlan0 Link encap:Ethernet HWaddr 00:18:de:d5:ae:b5
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

Your wireless is being detected.  Try in a terminal:

> sudo ifconfig wlan0 up
> sudo iwconfig wlan0 essid <the name of your network or router>
> sudo dhclient wlan0

These commands should start your wireless, but I do not use WPA (never have), so someone else will have to chime in to help set that up.  Once you bring up the network wireless, you may be able to start it with Network Manager as the wireless may show up in the list of choices.  After trying the above commands, try:

> sudo iwlist scan

to see if your network is listed.

---

### Post by malebolges on 2008-09-07
I tried the > sudo ifconfig wlan0 up and it wont do anything. The weird thing is that when I used the > sudo iwlist wlan0 scan I saw my network...
When I did try
phoenix@Mazinkaiser:~$ sudo dhclient wlan0
I got:
[sudo] password for phoenix: 
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:18:de:d5:ae:b5
Sending on   LPF/wlan0/00:18:de:d5:ae:b5
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Also, right now I have a wire plugged to the router, but when i try every one of this commands I unplug the cable, I don't know if that matters
And by the way thanks for the patience and the help, I know that it must be hard to deal with noobs:lolflag:

---

### Post by bobnutfield on 2008-09-07
Nothing visible happens when you run ifconfig wlan0 up.  It simply brings it up and goes back to the prompt.  But if you saw your network, you are receiving wireless signals.  It is just a matter of configuring it now.  Go to System>Network and see if you see a choice for your wireless.  Also, if you have the network icon in your taskbar, click on it and see if you see any networks shown.

Also try running:

> sudo iwconfig wlano essid any

I also found this for instructions on getting WPA to work with your wireless:

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html]("http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html")

---

### Post by malebolges on 2008-09-07
Thanks for the help, I can use my wireless now, so the next step is configure ubuntu to access my router.

---

### Post by bobnutfield on 2008-09-08
Do you know the IP address of your router?  If so, try to ping your router.

> ping 192.168.2.x

The above will tell you if you are able to access your router.  Then it is just a matter of setting up your WPA encryption, and you are all set.

---

