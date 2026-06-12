---
title: "Installing samba4"
date: 2013-10-19
forum: New to Ubuntu
---

### Post by dtree46 on 2013-10-19
Following these instructions:
[http://www.jadota.com/2013/01/installing-samba4-on-ubuntu-12-04/](http://www.jadota.com/2013/01/installing-samba4-on-ubuntu-12-04/)

Says to do this:

**Configure a fixed IP for your new server.**

 Edit **/etc/network/interfaces** and change the config to set a static IP. Please use your own IP information where applicable:

 sudo nano /etc/network/interfaces

 auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 192.168.1.10 8.8.8.8
dns-search mydomain.local

Also to: Please use your own IP information where applicable:

This is my 'ifconfig'.



dlw@dlw:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:5a:20:c2:cf  
          inet addr:10.0.0.4  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:5aff:fe20:c2cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:871 errors:0 dropped:0 overruns:0 frame:0
          TX packets:851 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:715933 (715.9 KB)  TX bytes:104533 (104.5 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1864 (1.8 KB)  TX bytes:1864 (1.8 KB)

virbr0    Link encap:Ethernet  HWaddr 72:0c:45:f1:5b:67  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

dlw@dlw:~$ 

What settings do I use?
Any help appreciated.

dlw

---

