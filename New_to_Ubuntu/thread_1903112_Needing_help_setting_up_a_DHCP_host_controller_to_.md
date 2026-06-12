---
title: "Needing help setting up a DHCP host controller to share internet"
date: 2012-01-01
forum: New to Ubuntu
---

### Post by Heinrich_Evers on 2012-01-01
Ok... So I've been diligently working at this for about 3 weeks now, and I'm new to Linux as far as command lines and whatnot so I'm kinda doing this blind, and feeling really stupid.

[SIZE=3]**THE GOAL:**[/SIZE] I have three windows clients that utilize my Netgear wireless G services through a ADSL connection supplied by AT&T uverse, And one Ubuntu linux server 10.,04 box that I'll be using this semester to study with my college Linux courses. I want to establish a DHCP host controller as an added layer of firewall protection with my windoze machines since recently I've been noticing some really crazy stuff involving my bandwidth disappearing with them. I re-installed them all, but after a short period of time it goes back to major lag on processor, and bandwidth. I check the processes, and when single instances of programs are opened the process list displays only what I can call "ghost processes" which more or less mirror the process I'm actually using. So I decided that if I have a DHCP host controller established, it will be easier for me to see what the hell is going on, and maybe prevent it using a firewall.

[SIZE=3]**THE PROBLEM:**[SIZE=1]My Ubuntu Linux 10.04 box that I've had to painstakingly build up "which has actually been a wonderful learning experience I might add"[/SIZE][/SIZE] is giving me problems with my NIC's upon installation eth0 works just fine, recognizes, downloads, internet access, and all that good stuff. However eth1 "the NIC that is to go to my wireless router on a hubbed port physically" seemsto give it conflictions that I don't understand.

For instance When eth1 is plugged in network manager states:

Wired Network (Intel 825682EZ 10/100 Etjhernet Controller)   <~~~~~~~~~~~~~~~ETH1
Auto eth1
Disconnect

Wired Network (Realtek RTL-8169 Gigabit Ethernet)  <~~~~~~ETH0
device not managed

So I ran ifconfig and got this:
eth0      Link encap:Ethernet  HWaddr 00:40:f4:ce:30:20  
          inet addr:192.168.1.71  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fece:3020/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24378 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1465964 (1.4 MB)  TX bytes:98575 (98.5 KB)
          Interrupt:22 Base address:0xac00 

eth1      Link encap:Ethernet  HWaddr 00:0c:f1:d0:db:0e  
          inet addr:172.16.0.5  Bcast:172.16.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:fed0:db0e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7562 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5505 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6833061 (6.8 MB)  TX bytes:889256 (889.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1416 (1.4 KB)  TX bytes:1416 (1.4 KB)

So even that looks like there should be nothing wrong, don't really know why eth0 is running unmanaged and when I right click Network Manager and click Connection Information it only displays the information for eth1.

When I right click it again and click edit connections only Auto eth1 is on the list. When I try to create Auto eth0 they way it's supposed to it asks me for my password, and does nothing.

When I disconnect eth1 physically from my router that I'm trying to share internet through eth0 begins to function again, but still remains unmanaged, and I can't create a profile for it in Network Manager.

Now I know they both work, so I'm feeling a bit retarded right about now, and it's extremly frustrating.

I have firestarter installed, but not running yet as I have to finish configging my network stuff before I can establish LAN permissions for the windoze machines.

ANY HELP WOULD BE EXTREMELY USEFUL AND THANKED!!!

---

