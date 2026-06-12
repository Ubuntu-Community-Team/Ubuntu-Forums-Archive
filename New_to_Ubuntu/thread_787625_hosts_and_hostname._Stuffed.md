---
title: "hosts and hostname. Stuffed"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by wanfahmi on 2008-05-09
I've stuffed these two files (/etc/hosts and /etc/hostname)
while fixing the sudo problem (8.04 LTS)

Now I have sudo working, but no internet connection. I'm able to ping the wifi router (192.168.1.1) but nothing else (ping google.com doesn't do anything)
I know the internet connection is up, as I'm able to post this from windows.

In the network manager
Roaming:enabled
Hostname: wanlaptop
DNS: 192.168.1.1

hosts
```

127.0.0.1 localhost wanlaptop
127.0.1.1 wanlaptop

::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

hostname
```

wanlaptop

```

---

### Post by hyper_ch on 2008-05-09
output of:

```

cat /etc/network/interfaces

```

```

cat /etc/resolv.conf

```

```

ifconfig

```

```

iwconfig

```

---

### Post by prshah on 2008-05-09
> **hyper_ch said:**
> output of:

```

cat /etc/network/resolv.conf

```



That's "/etc/resolv.conf"

---

### Post by hyper_ch on 2008-05-09
that's what I meant ;) corrected it above ;)

---

### Post by prshah on 2008-05-09
> **wanfahmi said:**
> Now I have sudo working, but no internet connection. I'm able to ping the wifi router (192.168.1.1) but nothing else (ping google.com doesn't do anything)


No connection between the sudo and the internet problems. Looks like a DNS problem.

Your /etc/resolv.conf file should have an entry as below:
```

cat /etc/resolv.conf 
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5008
#
### END INFO



nameserver 192.168.1.1

```

In this case, the nameserver reffered to is my router. I assume it will be the same for you. If that is so, check if your router has DNS service (DNS Server Service) enabled.

Or you can edit the "/etc/dhcp3/dhclient.conf" and:

1) locate the line with "prepend domain-name-servers" then
2) remove the "#" in front of that line if there is one
3) Add DNS addresses as mentioned by your ISP to the end of the line, seperated by ";"
4) restart networking ```
sudo /etc/init.d/networking restart
```

Now pinging/internet browsing should work.

Note that you have to edit the dhclient.conf file, rather than the /etc/resolv.conf file, because you have roaming mode enabled. In roaming mode, the network manager simply replaces the resolv.conf file with auto-detected (via DHCP) parameter and parameters from dhclient.conf.

---

### Post by wanfahmi on 2008-05-09
Hi again, these are my outputs. Sorry a bit slow in replying. Bouncing thru windows and ubuntu.

**ifconfig**
```

eth0      Link encap:Ethernet  HWaddr 00:13:d4:6a:ec:0d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0x8c00 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:e2:59:7d  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fee2:597d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:874 errors:0 dropped:62 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:69442 (67.8 KB)  TX bytes:9008 (8.7 KB)
          Interrupt:19 Base address:0xa000 Memory:fe8ff000-fe8fffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3850 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3850 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:192500 (187.9 KB)  TX bytes:192500 (187.9 KB)


```

**iwconfig**
```

eth1      IEEE 802.11g  ESSID:"ZyXEL"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:19:CB:07:9B:C9   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/100  Signal level=-68 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:62   Missed beacon:9


```

**interfaces**
```

auto lo
iface lo inet loopback

```

**resolve**
```

### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4908
#
### END INFO

nameserver 192.168.1.1

```

---

### Post by wanfahmi on 2008-05-09
> **prshah said:**
> 4) restart networking ```
sudo /etc/init.d/networking restart
```

Now pinging/internet browsing should work.


Still not working with restart.

---

### Post by prshah on 2008-05-09
> **wanfahmi said:**
> Hi again, these are my outputs. Sorry a bit slow in replying. Bouncing thru windows and ubuntu.

**ifconfig**
**iwconfig**
**interfaces**
**resolve**


All look file. Try ```
sudo modprobe -r ipv6
sudo /etc/init.d/networking restart
```

Since it looks as though an ipv6 address has also been given to your adapter.

Did you also try the "prepend servers" bit?

---

### Post by wanfahmi on 2008-05-09
> **prshah said:**
> All look file. Try ```
sudo modprobe -r ipv6
sudo /etc/init.d/networking restart
```

Since it looks as though an ipv6 address has also been given to your adapter.

Did you also try the "prepend servers" bit?

Unable to modprobe -r ipv6
FATAL: ...in use

I did the prepend stuff.
I'm thinking of formatting/downgrading back to 7.10.
Everything worked better on Gutsy... sigh.

I'm really about to give up.

** EDIT **
Nevermind.
It's a problem that effects ubuntu. I've tried 7.10 Live CD and 8.04 Live CD. Both were unable to connect to this wifi ap.
Windows doesn't seem to have a problem though.
I've come to a conclusion that somehow the Router is trashy.
It's a ZyXEL P-320W running micro_httpd.

---

### Post by prshah on 2008-05-09
> **wanfahmi said:**
> Unable to modprobe -r ipv6
FATAL: ...in use


OK got it. Here's what you need to do, a final push that will bring everything in place.

Boot into ubuntu, edit your /etc/modprobe.d/blacklist file. Add a single line to the end of the file: ```
blacklist ipv6
```.

Save, reboot and check; should work fine now.

I think your ubuntu/router prefers to use the ipv6 network rather than the ipv4 network. You should have a setting in the router to turn off ipv6, but the above will work as well.

---

### Post by wanfahmi on 2008-05-10
Arghh.. I was expecting that to work.

but

it didn't. 

I did the blacklist and to be sure i ran this

```

lsmod | grep ipv6

```

with no output. I guess that means the ipv6 blacklist is done right.

Anymore ideas?

---

### Post by hyper_ch on 2008-05-10
can you actually ping the router?

```

ping 192.168.1.1

```

---

### Post by brettg on 2008-05-10
If you can ping the router (as above) then try to ping the opendns server at 208.67.222.222

If that works then you have a dns problem. 

If that doesn't work then make sure that /etc/network/interfaces has an entry; 

gateway 192.168.1.1 

for the interface that is connected to your "router"

If you type 'route' it should give your default gw as the above address.

---

### Post by wanfahmi on 2008-05-10
> **hyper_ch said:**
> can you actually ping the router?

```

ping 192.168.1.1

```

Yup, pinging the router works, pinging anything else fails. I'm suspecting the somehow ubuntu is not working with DNS or something.

---

### Post by brettg on 2008-05-10
If you can't ping anything else (by ip address, not name) then it is a routing problem and not dns. 

You can't do a dns lookup if you cant ping the dns server, it's that simple.

Do what I said before, check that your default gateway is set correctly.

---

