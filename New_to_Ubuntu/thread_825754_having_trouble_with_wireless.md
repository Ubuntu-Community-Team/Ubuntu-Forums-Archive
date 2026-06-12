---
title: "having trouble with wireless"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by TimmyR41 on 2008-06-11
i had posted some of this before but i figured i would seperate them out into two seperate posts for the two problems.  i am having trouble connecting to the internet after installing xubuntu.  i have a home network set up.  one computer (my dads windows xp) connects into the back of the wireless router.  my computer (xubuntu) back in my room connects via a wireless usb adapter.  i went through the internet troubleshooting section in the documentation and input the commands but to be honest i'm not really sure what they are telling me and what my next step should be.  i still have no internet connection.  also i forgot to mention we do have a proxy server active.  here are the outputs from the command lines.

check for driver/check device is on - sudo lshw -C network```
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: eth0
       version: 78
       serial: 00:04:76:37:35:23
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=64 link=no maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:12:17:7d:94:53
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.101 multicast=yes wireless=IEEE 802.11g

```

check for connection to the router - iwconfig```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:7D:7D:C9   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=31/100  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

check ip assignment - ifconfig```
eth0      Link encap:Ethernet  HWaddr 00:04:76:37:35:23  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:3 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:442 errors:0 dropped:0 overruns:0 frame:0
          TX packets:442 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23694 (23.1 KB)  TX bytes:23694 (23.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:7d:94:53  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:17ff:fe7d:9453/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:206 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13760 (13.4 KB)  TX bytes:19261 (18.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-12-17-7D-94-53-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Check DNS - ping 82.211.81.158```
PING 82.211.81.158 (82.211.81.158) 56(84) bytes of data.
From 192.168.1.101 icmp_seq=10 Destination Host Unreachable
through
From 192.168.1.101 icmp_seq=431 Destination Host Unreachable
then multiple
ping: sendmsg: No buffer space available
then multiple
From 192.168.1.101 icmp_seq=3992 Destination Host Unreachable
ending with
--- 82.211.81.158 ping statistics ---
4332 packets transmitted, 0 received, +242 errors, 100% packet loss, time 4479662ms
, pipe 3

```


check dns - ping [www.ubuntu.com](www.ubuntu.com)```
PING www.ubuntu.com (91.189.94.250) 56(84) bytes of data.
64 bytes from jujube.canonical.com (91.189.94.250): icmp_seq=20 ttl=47 time=1386 ms
64 bytes from jujube.canonical.com (91.189.94.250): icmp_seq=21 ttl=47 time=388 ms
64 bytes from jujube.canonical.com (91.189.94.250): icmp_seq=22 ttl=47 time=118 ms
64 bytes from jujube.canonical.com (91.189.94.250): icmp_seq=23 ttl=47 time=2639 ms
64 bytes from jujube.canonical.com (91.189.94.250): icmp_seq=24 ttl=47 time=10060 ms
64 bytes from 91.189.94.250: icmp_seq=25 ttl=47 time=17889 ms
From joshua-desktop.local (192.168.1.101) icmp_seq=27 Destination Host Unreachable
From joshua-desktop.local (192.168.1.101) icmp_seq=28 Destination Host Unreachable
From joshua-desktop.local (192.168.1.101) icmp_seq=29 Destination Host Unreachable
64 bytes from jujube.canonical.com (91.189.94.250): icmp_seq=38 ttl=47 time=694 ms
64 bytes from jujube.canonical.com (91.189.94.250): icmp_seq=39 ttl=47 time=119 ms
64 bytes from jujube.canonical.com (91.189.94.250): icmp_seq=40 ttl=47 time=120 ms
64 bytes from 91.189.94.250: icmp_seq=41 ttl=47 time=3517 ms
64 bytes from 91.189.94.250: icmp_seq=42 ttl=47 time=9254 ms
64 bytes from 91.189.94.250: icmp_seq=43 ttl=47 time=46725 ms
64 bytes from 91.189.94.250: icmp_seq=44 ttl=47 time=53797 ms
From joshua-desktop.local (192.168.1.101) icmp_seq=46 Destination Host Unreachable
From joshua-desktop.local (192.168.1.101) icmp_seq=47 Destination Host Unreachable
From joshua-desktop.local (192.168.1.101) icmp_seq=48 Destination Host Unreachable
64 bytes from jujube.canonical.com (91.189.94.250): icmp_seq=49 ttl=47 time=118 ms
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available

--- www.ubuntu.com ping statistics ---
98 packets transmitted, 14 received, +6 errors, 85% packet loss, time 349495ms
rtt min/avg/max/mdev = 118.667/10487.895/53797.161/17042.605 ms, pipe 4

```

check dns - cat /etc/resolv.conf```
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4734
#
### END INFO



nameserver 216.169.160.2
nameserver 66.109.229.4

```

IPv6 Not Supported - gksudo gedit /etc/modprobe.d/aliases - this returns me to the command prompt after i enter my password

lsusb```
Bus 001 Device 005: ID 13b1:000d Linksys 
Bus 001 Device 004: ID 413c:3200 Dell Computer Corp. 
Bus 001 Device 003: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 001 Device 002: ID 0409:0050 NEC Corp. 
Bus 001 Device 001: ID 0000:0000  

cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

any help i can get would be great.  thanks alot.

---

### Post by powerpleb on 2008-06-11
Did you enter the proxy details into FireFox, etc network preferences?

---

### Post by TimmyR41 on 2008-06-11
yes i did.  as far as i know i entered them correctly.  it does seem like its the proxy thats having a problem though.  is there anywhere else i would ahve to enter the proxy?

---

### Post by powerpleb on 2008-06-11
> **TimmyR41 said:**
> yes i did.  as far as i know i entered them correctly.  it does seem like its the proxy thats having a problem though.  is there anywhere else i would ahve to enter the proxy?

Well if you're going to use command line stuff (like apt) to access the internet look at this:
[http://ubuntuforums.org/showthread.php?t=83401](http://ubuntuforums.org/showthread.php?t=83401)

I don't know much about this. But you have an IP so I would say it should work. 
Is the IP static or do you have DHCP on the wireless router?

---

### Post by TimmyR41 on 2008-06-11
i believe its dhcp but i'm not 100% sure.  is there a way to find out?

---

### Post by powerpleb on 2008-06-11
> **TimmyR41 said:**
> i believe its dhcp but i'm not 100% sure.  is there a way to find out?

Yes. I wish I knew how though.

---

### Post by powerpleb on 2008-06-11
yes...

look at /etc/network/interfaces to see if it's static

if it looks like this
```
iface wlan0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.254
```

it's static

Mine looks like this:
```
auto lo
iface lo inet loopback

```
and I connect through wireless with DHCP

---

### Post by TimmyR41 on 2008-06-11
ok, i acctually did that allready and mine looks like this as well


```
auto lo
iface lo inet loopback

```

---

### Post by powerpleb on 2008-06-11
Oh yea, I don't know then.
If you're pinging websites from the command line i don't think it will work unless you configure it to go through the proxy.

Which you can do with this command:
export http_proxy='http://domain\userid:password@proxy:80/'

---

### Post by TimmyR41 on 2008-06-11
ok, my proxy is 

```
contentfilter.dejazzd.com port 2108
```

how would that be input to allow the command lines to access the internet and then which method should i use to input it into firefox.  there are multiple options i can choose from in firefox and i wasn't sure which one was correct.

---

