---
title: "Can't get internet connection working on Ubuntu Server 14.04.3 LTS"
date: 2015-08-16
forum: New to Ubuntu
---

### Post by mikegryo on 2015-08-16
Hi,

I just wiped an old ~2005-ish Dell Inspiron and installed my first Ubuntu Server 14.04.3 LTS via LiveCD to try to set up a home server.  I've never set up a home server before, but I'm somewhat familiar with linux.  I've had Ubuntu and Mint installed as Virtual machines for over six months, and have successfully installed and configured Arch in a VM recently, too.  I have the laptop hooked up to my router via ethernet and manually configured network settings during install because the Ubuntu Server install couldn't auto detect settings.  I used the IP address and other related info (subnet mask, etc.) of the original Windows OS when setting up.  

I successfully installed and booted into my Ubuntu Server, but I can't for the life of me get the internet connection going.  I've Googled for hours and hours and tried various things that I've found in threads, but nothing is working.  Note that I am posting this from another laptop that has internet access (the same ethernet cable that I'm currently connecting to the Ubuntu Server laptop worked on this laptop, and wireless works on this laptop, as well).  Also, note that I can't copy and paste from the Ubuntu Server, so I'll try to type as much as possible from what I"m getting from the Ubuntu Server laptop.  Here is some info:

ifconfig:

```
eth0     Link uncap:Ethernet  HWaddr 00:1c:23:a3:12:98
           inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
           UP BROADCAST MULTICAST  MTU:1500  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collision:0 txqueuelen:1000
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
           Interrupt:17

lo        Link encap:Local Loopback
           inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr:  ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:65536  Metric:1
           RX packets:498 errors:0 dropped:0 overruns:0 frame:0
           TX etc etc
           collsions etc etc
           RX bytes:143426 (143.4 KB)  TX bytes:143426 (143.4 KB)

virbr0  Link encap:Ethernet  HWaddr 32:d2:12:b2:b0:d1
           inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
            etc etc
            bunch of other info that I can type if you need it....
```

route:

```
Kernel IP routing table
Destination          Gateway          Genmask          Flags     Metric     Ref     Use     Iface
default                192.168.1.1     0.0.0.0             UG        0            0        0         eth0
localnet               *                     255.255.255.0  U          0            0        0         eth0
192.168.122.0     *                     255.255.255.0  U          0            0        0         virbr0
```

/etc/network/interfaces:

```
#This file describes the network interfaces available on your system
#and how to activate them.  For more information , see interfaces(5).

#The loopback network interface
auto lo
iface lo inet loopback

#The primary network interface
auto eth0
iface eth0 inet static
          address 192.168.1.106
          netmask 255.255.255.0
          network 192.168.1.0
          broadcast 192.168.1.255
          gateway 192.168.1.1
          # dns-* options are implemented by the resolvconf package, if installed
          dns-nameservers 192.168.1.1 8.8.8.8 8.8.4.4
          dans-search yoyo.com
```

ifconfig -a | grep eth0:

```
eth0           Link uncap:Ethernet  HWaddr 00:1c:23:a3:12:98
```

ip link: 

```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc no queue state UNKNOWN mode DEFAULT group default
     link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fifo_fast state DOWN mode DEFAULT group default glen 1000
     link/ether 00:1c:23:a3:12:98 bed ff:ff:ff:ff:ff:ff
3: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN mode DEFAULT group default
     link/ether 32:d2:12:b2:b0:d1 brd ff:ff:ff:ff:ff:ff
```

route -n:

```
Kernel IP routing table
Destination          Gateway          Genmask          Flags     Metric     Ref     Use     Iface
0.0.0.0                192.168.1.1     0.0.0.0             UG        0            0        0         eth0
192.168.1.0         0.0.0.0            255.255.255.0  U          0            0        0         eth0
192.168.122.0     0.0.0.0            255.255.255.0   U          0            0        0         virbr0
```

nslookup ubuntu.com:

```
;; connection timed out; no servers could be reached
```

dig ubuntuforums.com

```
; <<>> DiG 9.9.5-3ubuntu0.4-Ubuntu <<>> ubuntuforums.org
;; global options: +cmd
;; connection timed out; no servers could be reached
```

sudo service networking restart:

```
stop: Job failed while stopping
start: Job is already running: networking
```

sudo service networking start:

```
start: Job is already running: networking
```

```
ping -c 3 8.8.8.8:

PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From 192.168.1.106 icmp_seq=1 Destination Host Unreachable
From 192.168.1.106 icmp_seq=2 Destination Host Unreachable
From 192.168.1.106 icmp_seq=3 Destination Host Unreachable

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 1999ms
pipe 3
```

ping -c 3 [www.google.com:]("http://www.google.com:")

```
ping: unknown host www.google.com

```
apt-cache policy network-manager:

```
network-manager: 
  Installed; (none)
  Candidate: (none)
  Version table: 
```

lspci Ethernet controller shows:

```
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev02)

```

Also tried: ```
ifconfig eth0 up
``` but it doesn't change anything (that I can find)


I'm seriously out of ideas.  Please let me know if any other information can help diagnose what is going on.

---

### Post by dino99 on 2015-08-16
Then you do not have DNS nameservers. Add these two lines to /etc/resolv.conf:

  nameserver 8.8.8.8
  nameserver 8.8.4.4
and it should work.

---

### Post by mikegryo on 2015-08-16
Hi dino,

My /etc/resolv.conf file is already set as:

```
#Dyanamic resolv.conf(5) file for glib resolver(3) generated by resolvconf (8)
#DO NOTE EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 8.8.8.8
nameserver 8.8.4.4
search yoyo.com
```

No connection using this.

---

### Post by tripp98 on 2015-08-17
From your server try pinging your gateway.

ping 192.168.1.1

---

### Post by matt_symes on 2015-08-17
Hi

The link state for eth0 is showing no carrier.

Check the cabling first and check the cable itself works.

ifconfig is also showing the state as UP but ip link is showing the state as DOWN.

Kind regards

---

### Post by mikegryo on 2015-08-17
> **tripp98 said:**
> From your server try pinging your gateway.

ping 192.168.1.1

tripp,

When I ping my gateway I get:

```
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data
From 192.168.1.106 imp_seq=1 Destination Host Unreachable
From 192.168.1.106 imp_seq=2 Destination Host Unreachable
From 192.168.1.106 imp_seq=3 Destination Host Unreachable
From 192.168.1.106 imp_seq=4 Destination Host Unreachable
From 192.168.1.106 imp_seq=5 Destination Host Unreachable
```

and repeats until I CTRL+C.  Then I get:

```
---192.168.1.1 ping statistics ---
13 packets transmitted, 0 received, +12 errors, 100% packet loss, time 12061ms
pipe 3
```

---

### Post by mikegryo on 2015-08-17
Ok so I was frustrated and shut down and unplugged everything. Came back a little later and booted up and plugged everything back in again and I'm up and running with an Internet connection. 

Noob life...

---

### Post by matt_symes on 2015-08-17
Hi

You had no carrier signal so Ubuntu did not think you even had an Ethernet cable plugged into the card.

I suspect that unplugging everything and then replugging it all back in fixed that issue.

I also suspect that the reboot brought up your interfaces.

I'm glad it's fixed.

Kind regards

---

### Post by mikegryo on 2015-08-18
Thank you for the help and time!

---

