---
title: "WIRED internet"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by gerben1 on 2008-04-29
Can anybody give me some ideas on how to get wired internet working again. It stopped working when I tried to get wireless working. I got that working in the end with the b43 driver. That driver does not perform very well, not by far as nice as the ndiswrapper way worked in Gutsy, so I would like to try that again, but it is very annoying working with the laptop without any internet connection, so i would really like to get the wired connection working again.

(for example you cannot even turn the b43 dirver on again in system->administration once you turned it off, because when you turn it on it wants to download b43-fwcutter, how great is that?? NO internet connection and in order to solve it you NEED an internet connection...)

Any ideas?

---

### Post by superprash2003 on 2008-04-29
can you post your ifconfig output

---

### Post by gerben1 on 2008-04-29
> **superprash2003 said:**
> can you post your ifconfig output

```

gerben@CC1184274-A:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:ff:40:a2
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:477 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:30528 (29.8 KB)  TX bytes:4545 (4.4 KB)
          Interrupt:18

eth0:avahi Link encap:Ethernet  HWaddr 00:c0:9f:ff:40:a2
          inet addr:169.254.9.38  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:512 errors:0 dropped:0 overruns:0 frame:0
          TX packets:512 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:50696 (49.5 KB)  TX bytes:50696 (49.5 KB)

```

---

### Post by gerben1 on 2008-04-29
I just reinstalled the b43 drivers, so that I at least have an internet connection on the laptop. The Wired internet still does not work, but the output of ifconfig is a bit different, I do not know if it matters but this is the output now:
```

gerben@CC1184274-A:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:ff:40:a2
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18

eth1      Link encap:Ethernet  HWaddr 00:14:a4:6a:b1:ae
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1052 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:954871 (932.4 KB)  TX bytes:185924 (181.5 KB)

eth0:avahi Link encap:Ethernet  HWaddr 00:c0:9f:ff:40:a2
          inet addr:169.254.9.38  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:15976 (15.6 KB)  TX bytes:15976 (15.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A4-6A-B1-AE-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by gerben1 on 2008-04-30
anybody?

---

### Post by hyper_ch on 2008-04-30
please post the output of:

```

cat /etc/network/interfaces

```


```

cat /etc/resolv.conf

```

---

### Post by gerben1 on 2008-04-30
```

gerben@CC1184274-A:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback




iface eth0 inet dhcp







auto eth0


iface eth1 inet dhcp
wpa-psk 3691c71c0bf9edfcba12f7316546a3c8dd451103ebf0f85c1664e9c45f9e91f0
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid rotman

auto eth1

```
```

gerben@CC1184274-A:~$ cat /etc/resolv.conf
search zwoll1.ov.home.nl
nameserver 213.51.129.37
nameserver 213.51.144.37

```

---

### Post by hyper_ch on 2008-04-30
change this to
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp
#wpa-psk 3691c71c0bf9edfcba12f7316546a3c8dd451103ebf0f85c1664e9c45f9e91f0
#wpa-driver wext
#wpa-key-mgmt WPA-PSK
#wpa-proto WPA
#wpa-ssid rotman

```

and then run

```

sudo /etc/init.d/networking restart

```

The post again
```

ifconfig

```

---

### Post by gerben1 on 2008-04-30
when I ran 
sudo/etc/networking restart an bunch of things happened and the halted at 
 * Starting NTP server ntpd
   ...done.
after waiting for about 5 min I ended it with a ctrl-c

this is the output:
```

gerben@CC1184274-A:~$ sudo gedit /etc/network/interfaces
[sudo] password for gerben:
gerben@CC1184274-A:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                 There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:c0:9f:ff:40:a2
Sending on   LPF/eth0/00:c0:9f:ff:40:a2
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                                [ OK ]
gerben@CC1184274-A:~$  * Stopping NTP server ntpd
   ...done.
 * Starting NTP server ntpd
   ...done.

```

and here ifconfig after that:
```

gerben@CC1184274-A:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:ff:40:a2
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:321 (321.0 B)  TX bytes:64 (64.0 B)
          Interrupt:18

eth1      Link encap:Ethernet  HWaddr 00:14:a4:6a:b1:ae
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:5808 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5904 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5391643 (5.1 MB)  TX bytes:928970 (907.1 KB)

eth0:avahi Link encap:Ethernet  HWaddr 00:c0:9f:ff:40:a2
          inet addr:169.254.9.38  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4880 (4.7 KB)  TX bytes:4880 (4.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A4-6A-B1-AE-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by hyper_ch on 2008-04-30
are you sure you did save the changes?

Eth1 has a connection there but eth0 doesn't... according to my config it should not be like that.

---

### Post by gerben1 on 2008-04-30
yes, here is /etc/network/interfaces

```

gerben@CC1184274-A:~$ cat /etc/net
netscsid.conf  network/       networks
gerben@CC1184274-A:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp
#wpa-psk 3691c71c0bf9edfcba12f7316546a3c8dd451103ebf0f85c1664e9c45f9e91f0
#wpa-driver wext
#wpa-key-mgmt WPA-PSK
#wpa-proto WPA
#wpa-ssid rotman


```

---

### Post by gerben1 on 2008-04-30
Oops sorry, my network cable was not connected, sorry....

ok, connected the cable now:

```

gerben@CC1184274-A:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                 RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 24346
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:c0:9f:ff:40:a2
Sending on   LPF/eth0/00:c0:9f:ff:40:a2
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:c0:9f:ff:40:a2
Sending on   LPF/eth0/00:c0:9f:ff:40:a2
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 192.168.1.102 from 192.168.1.1
DHCPREQUEST of 192.168.1.102 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.102 from 192.168.1.1
bound to 192.168.1.102 -- renewal in 34697 seconds.
                                                                                [ OK ]
gerben@CC1184274-A:~$  * Stopping NTP server ntpd
   ...done.
 * Starting NTP server ntpd
   ...done.

```

```

gerben@CC1184274-A:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:ff:40:a2
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1380 (1.3 KB)  TX bytes:3490 (3.4 KB)
          Interrupt:18

eth1      Link encap:Ethernet  HWaddr 00:14:a4:6a:b1:ae
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:7231 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7365 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6557094 (6.2 MB)  TX bytes:1196040 (1.1 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4880 (4.7 KB)  TX bytes:4880 (4.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A4-6A-B1-AE-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by hyper_ch on 2008-04-30
you are now connected with both your network devices... but the question still remains why eth1 is getting a connection....

---

### Post by gerben1 on 2008-04-30
Well, why should it not? I obviously don't know, but this is how i would think about this based on absolutely no knowledge of how this works:

I am restarting networking, and then apparently it sees two ways to connect and then connects both ways.

How is it controlled which one should be tried first? and if that one succeeds should the other one then not be tried?

---

### Post by hyper_ch on 2008-04-30
Well, with the # for eht1 one it means it's just comments in that text files and should not be parsed... hence the configuration file does not configure eth1 at all and hence it should not at all be loaded...

---

### Post by gerben1 on 2008-04-30
Oh wow I did not even realise it, but the wired internet now works. 
Thanks a lot.

I am using wicd, perhaps that has something to do with it. It may have some config file that also holds the info to connect to the wireless network.

---

