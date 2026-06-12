---
title: "Noob  Looking For Help With Wireless Internet Connect"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by Monrizzy on 2008-09-20
I've got Ubuntu Hardy installed on my Gateway Desktop and I'm trying to set up the wireless internet.  I've got this machine as a dual boot and I'm able to connect to the internet wirelessly through my Windows XP OS but I'm completely stuck on how to set up with Ubuntu.  Mind you I am a complete and total noob and I'll try not to sound to stupid when asking for help.

Thanks tons for the opportunity to learn from you folks!!!!

---

### Post by bobnutfield on 2008-09-20
No one sounds stupid when they are looking for help.  You will find people on this forum happy to help.  Run this from a terminal:

> sudo lshw -C network

We need to know what wireless chipset you have.  Then we can recommend a solution.

---

### Post by phidia on 2008-09-20
Do you have any drivers in System > Administration > Hardware Drivers that need to be selected/enabled? If not or that doesn't help then open a terminal from Applications > Accessories and enter > lspci -v Post the output from that here.

---

### Post by Monrizzy on 2008-09-20
monrizzy@monrizzy-desktop:~$ lshw -c network 
Hardware Lister (lshw) - B.02.12.01 
usage: lshw [-format] [-options ...] 
       lshw -version 

	-version        print program version (B.02.12.01) 

format can be 
	-html           output hardware tree as HTML 
	-xml            output hardware tree as XML 
	-short          output hardware paths 
	-businfo        output bus information 

options can be 
	-class CLASS    only show a certain class of hardware 
	-C CLASS        same as '-class CLASS' 
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. ) 
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. ) 
	-quiet          don't display status 
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.) 

monrizzy@monrizzy-desktop:~$ sudo lshw -C network 
[sudo] password for monrizzy: 
Sorry, try again. 
[sudo] password for monrizzy: 
  *-network:0             
       description: Ethernet interface 
       product: 82801BA/BAM/CA/CAM Ethernet Controller 
       vendor: Intel Corporation 
       physical id: 8 
       bus info: pci@0000:02:08.0 
       logical name: eth0 
       version: 03 
       serial: 00:03:47:d8:95:d2 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s 
  *-network:1 
       description: Wireless interface 
       product: AR2413 802.11bg NIC 
       vendor: Atheros Communications Inc. 
       physical id: b 
       bus info: pci@0000:02:0b.0 
       logical name: wifi0 
       version: 01 
       serial: 00:1e:58:95:e7:f9 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g 
monrizzy@monrizzy-desktop:~$

---

### Post by bobnutfield on 2008-09-20
OK, if you go to System>Administration>Hardware Drivers it is likely you will see a wireless driver you can enable.  Ubuntu is recognizing it and has identified the driver for it (ath_pci).  This is the kernel Atheros driver.

---

### Post by Monrizzy on 2008-09-20
Yeah it is showing as enabled and when I went to network settings> manual config> wireless connection I saw my network I just can't seem to get on it.

---

### Post by bobnutfield on 2008-09-20
Are you using encryption on your network?  Try from a command line:

> sudo dhclient wlan0

To see if it will give you an IP address.  Also, go to System>Administration>Network and see if you see your wireless shown.  If so, try to configure it with the GUI.

---

### Post by Monrizzy on 2008-09-20
monrizzy@monrizzy-desktop:~$ sudo dhclient wlan0 
[sudo] password for monrizzy: 
Sorry, try again. 
[sudo] password for monrizzy: 
Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

wifi0: unknown hardware address type 801 
SIOCSIFADDR: No such device 
wlan0: ERROR while getting interface flags: No such device 
wlan0: ERROR while getting interface flags: No such device 
wifi0: unknown hardware address type 801 
Bind socket to interface: No such device 
monrizzy@monrizzy-desktop:~$

---

### Post by bobnutfield on 2008-09-20
Type in a terminal:

> sudo ifconfig -a

Your wireless may have a different name.  Also, did the wireless show up in Network?

---

### Post by Monrizzy on 2008-09-20
monrizzy@monrizzy-desktop:~$ sudo ifconfig -a 
ath0      Link encap:Ethernet  HWaddr 00:1e:58:95:e7:f9  
          inet6 addr: fe80::21e:58ff:fe95:e7f9/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

ath0:avahi Link encap:Ethernet  HWaddr 00:1e:58:95:e7:f9  
          inet addr:169.254.11.7  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 

eth0      Link encap:Ethernet  HWaddr 00:03:47:d8:95:d2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:2168 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2168 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:117804 (115.0 KB)  TX bytes:117804 (115.0 KB) 

wifi0     Link encap:UNSPEC  HWaddr 00-1E-58-95-E7-F9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:5231 errors:0 dropped:0 overruns:0 frame:82250 
          TX packets:10504 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:199 
          RX bytes:676992 (661.1 KB)  TX bytes:483544 (472.2 KB) 
          Interrupt:18 

monrizzy@monrizzy-desktop:~$ 



Yes the wireless did show up in the network.

---

### Post by bobnutfield on 2008-09-20
OK, your wireless is called ath0.  Before you try the dhclient again, since you wireless is showing up, just unlock the GUI with your sudo password, highlight your wireless connection, click edit, and put in the wireless configuration information.  DHCP is the easiest, and choose your style of encryption.  This should get it working for you.  If it doesn't for some reason, try

> dhclient ath0

But hopefully, you should be able to get it going using the GUI.

---

### Post by Monrizzy on 2008-09-20
Still doesn't seem to be working Bob.  Listed below is the result of "dhclient ath0"


monrizzy@monrizzy-desktop:~$ dhclient ath0 
There is already a pid file /var/run/dhclient.pid with pid 134519072 
Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

wifi0: unknown hardware address type 801 
can't create /var/lib/dhcp3/dhclient.leases: Permission denied 
Can't create /var/run/dhclient.pid: Permission denied 
drop_privileges: could not set group id: Operation not permitted 
monrizzy@monrizzy-desktop:~$

---

### Post by bobnutfield on 2008-09-20
Open a terminal and type:

> sudo ifconfig     with no parameters

See if an IP address is being assigned.

---

### Post by Monrizzy on 2008-09-20
Yes it does seem to have issued an IP Address from what I can tell.

monrizzy@monrizzy-desktop:~$ sudo ifconfig 
[sudo] password for monrizzy: 
ath0      Link encap:Ethernet  HWaddr 00:1e:58:95:e7:f9  
          inet6 addr: fe80::21e:58ff:fe95:e7f9/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

ath0:avahi Link encap:Ethernet  HWaddr 00:1e:58:95:e7:f9  
          inet addr:169.254.11.7  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 

eth0      Link encap:Ethernet  HWaddr 00:03:47:d8:95:d2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:2344 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2344 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:131516 (128.4 KB)  TX bytes:131516 (128.4 KB) 

wifi0     Link encap:UNSPEC  HWaddr 00-1E-58-95-E7-F9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:5316 errors:0 dropped:0 overruns:0 frame:186839 
          TX packets:10612 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:199 
          RX bytes:687977 (671.8 KB)  TX bytes:488920 (477.4 KB) 
          Interrupt:18

---

### Post by bobnutfield on 2008-09-20
> ath0:avahi Link encap:Ethernet HWaddr 00:1e:58:95:e7:f9
inet addr:169.254.11.7 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 

Well, according to this, you should be up and running.  Have you tried opening your browser to see if you are connected?  You have an IP address, so you should be connected.  Do you know the IP address of your router?  If so, try to 

> ping <ip address of your router

Then, from the command line, try:

> ping [www.google.com](www.google.com) hit Control+C after a few seconds to stop it.

---

### Post by Monrizzy on 2008-09-20
I get this when I ping the router

monrizzy@monrizzy-desktop:~$ ping 192.168.0.1 
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data. 
From 169.254.11.7 icmp_seq=1 Destination Host Unreachable 
From 169.254.11.7 icmp_seq=2 Destination Host Unreachable 
From 169.254.11.7 icmp_seq=3 Destination Host Unreachable 
From 169.254.11.7 icmp_seq=4 Destination Host Unreachable 
From 169.254.11.7 icmp_seq=5 Destination Host Unreachable 
From 169.254.11.7 icmp_seq=6 Destination Host Unreachable 

And I get this when I ping [www.google.com](www.google.com)

monrizzy@monrizzy-desktop:~$ ping [www.google.com](www.google.com) 
ping: unknown host [www.google.com](www.google.com) 
monrizzy@monrizzy-desktop:~$ ping [www.google.com](www.google.com) 
ping: unknown host [www.google.com](www.google.com)

---

### Post by bobnutfield on 2008-09-20
OK, first problem.  If your router is 192.168.0.1, then it would not have assigned (I do not believe) a 169.x.x.x  ip address.  It would have, like mine, assigned something like 192.168.2.x.  Open a terminal and type:

> sudo iwlist scan 

Lets see if your network shows up.  I may have to look into this one to give a better answer.  Hopefully, someone else will chime in to help further.

---

### Post by bobnutfield on 2008-09-20
I believe the IP address is being assigned by the avahi daemon and has nothing to do with the router.  You appear to be receiving but are not connected to your router.  I will find out what I can for you and book mark this page.  If no one else has provided an answer before, I will get back to you as soon as I have an answer.

---

### Post by Monrizzy on 2008-09-20
Thanks Bob!

---

### Post by Monrizzy on 2008-09-20
Can anyone else offer any wisdom on this matter?

---

### Post by Monrizzy on 2008-09-20
> OK, first problem. If your router is 192.168.0.1, then it would not have assigned (I do not believe) a 169.x.x.x ip address. It would have, like mine, assigned something like 192.168.2.x. Open a terminal and type:

Quote:
sudo iwlist scan
Lets see if your network shows up. I may have to look into this one to give a better answer. Hopefully, someone else will chime in to help further.

monrizzy@monrizzy-desktop:~$ sudo iwlist scan 
[sudo] password for monrizzy: 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

wifi0     Interface doesn't support scanning. 

ath0      Scan completed : 
          Cell 01 - Address: 00:1E:58:FC:22:A7 
                    ESSID:"IzzyHome" 
                    Mode:Master 
                    Frequency:2.412 GHz (Channel 1) 
                    Quality=47/70  Signal level=-48 dBm  Noise level=-95 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Extra:bcn_int=100 
                    Extra:wme_ie=dd070050f202000100 
          Cell 02 - Address: 00:13:10:81:1C:53 
                    ESSID:"RevDoc2008" 
                    Mode:Master 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality=8/70  Signal level=-87 dBm  Noise level=-95 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s 
                              12 Mb/s; 48 Mb/s 
                    Extra:bcn_int=100

---

### Post by Monrizzy on 2008-09-26
Anybody seen a problem like this before?

---

### Post by Monrizzy on 2008-09-27
Anybody seen a problem like this before?

---

### Post by bobnutfield on 2008-09-28
Try in a terminal:

> dhclient ath0

see if it offers an IP address.

---

