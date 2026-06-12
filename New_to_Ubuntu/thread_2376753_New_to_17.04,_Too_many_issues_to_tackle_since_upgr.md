---
title: "New to 17.04, Too many issues to tackle since upgrade Need Help"
date: 2017-11-05
forum: New to Ubuntu
---

### Post by verxius on 2017-11-05
So as the title implies I am new to Linux, I recently decided to upgrade to 17.04 since I thought it would help give me better results with my hybrid graphic cards. My goal was achieved but in the process I've opened up a whole new can of worms, my system has hit such a stage that I have had to resort to using windows in order to make this thread. as of right this moment I have 3 main problems that are of the utmost importance every other problem I have is small enough that I can work out on my own or deal with those problems are as follows the most important being first, and so on

Problem #1:
I am having an issue anytime I want to use a graphical application that requires root privileges for instance Boot-repair, gedit, gparted , etc. if I try opening from terminal the process stops abruptly and gives an error message( I will update this later to echo that error), if I try opening as a standard application from the GUI the authentication box pops up but is grayed out and I cannot type in it. 

Problem #2:
I cannot access my UEFI settings at all, every time I attempt to navigate the grub to that setting it gives me an error about my OSindacations(once again I will update this with the actual error message) 

Problem #3:
my network cannot connect unless I use a VPN, I've tweaked the network settings previously and got it to work smoothly but after 3 reboots the seem to revert back to the same error that I have no further information on aside from theres a question mark where my wifi network indicator used to be

Any help or guidance is greatly needed and appreciated
*I do apologize about the vagueness of this thread, I will update as I get more information on the problems as stated I am currently on windows so the exact verbiage of the errors eludes me, if you are going to comment "needs more information" tell me where to get that information, if this information isn't enough at the given time to even merit a response then I am sorry to have wasted your time, to all else thank you for your time.

---

### Post by TheFu on 2017-11-06
Welcome to the forums.

1 thread for each issue, please.  

Why different threads for different questions?  The guys who will help with GUI issues are different from the people who will try to help with networking stuff.  I won't touch GUI stuff, for example, but usually will try to help with networking and VPN things.  For help with networking, post the cmds and output of these things:
```
sudo lshw -C network
ifconfig
route -n

```
Show it with and without the VPN on.  Would be good to know the type of VPN, where the client is and where the server is. I use a VPN at home to be able to connect back when traveling/cafe'ing.  I use a VPN server in different locations when I prefer for my current location not to be trivially known.  2 very different purposes, with different issues and solutions.

17.04 support ends in about 2 months. Not worth the effort to fix it now. At this point, moving to 17.10 (until 18.04 LTS is released) is really the best solution.  Especially since the GUI was completely redone for 17.10 going forward, so any work you do will be throw-away come January.  Non-LTS releases have 6-9 months of support, BTW. For people new to Linux, it is strongly recommended to stay with an LTS (16.04.5) for the first 1-4 yrs. LTS happens every even year in April - 12.04, 14.04, 16.04, 18.04, 20.04 ...  all other releases are demos - only 6-9 months of support.  Often, those non-LTS releases are technology demonstration efforts.  17.10 is making Wayland the default display libraries instead of 40+ yr old X11.  That is a pretty big deal and has ramifications through the desktop software stack.

Please say HOW you are doing things.  Don't assume that the way you are doing it is the way others would do it.  Each different release (GUI versions) has different GUI tools.   For example, I don't use a GUI to manage network settings. They change too often.  For non-trivial networking, the GUI just doesn't work for my needs, IME.

Also, using root with GUIs is asking for trouble most of the time.  A strong understanding of Unix file/directory permissions is required.  I find it easier just to never use sudo/su - with any GUI (1 exception - gparted).  Are you certain the uid is in the correct group that is allowed to use sudo?  'id' will show that. To edit system files safely, use **sudoedit /path/to/file**.  Other methods are prone to errors and issues.  You can use any editor you like with sudoedit, just set the EDITOR environment variable.  Never use **sudo gedit**.  sudo doesn't setup the HOME directory so settings are likely to be stored with root:root ownership under your HOME. That's bad.  I think it is best to just dump the GUI editors and learn vim. **sudo vim** is fine, plus I've never seen any GUI editor on a router.  Vim in the hands of an expert is a sight to behold.  It is amazingly powerful, but if you want gedit, just set the EDITOR env variable.

And when posting output, always use 'code tags' - Adv Reply (#) so things line up. Experts are used to reading it that way and makes it much easier for us.  The easier the output is to read, the more likely that more people are to actually look at it and help.

Good luck.

---

### Post by oldos2er on 2017-11-07
Which version did you upgrade from?

---

### Post by verxius on 2017-11-07
16 don't remember which version of 16 though

---

### Post by verxius on 2017-11-07
So my apologies about breaking etiquette, in my head addressing all three issues at once would possibly help diagnose the error, anyways heres the results of the commands
Without VPN
```
[dracarys:~]$ sudo lshw -C network[sudo] password for dracarys: 
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 10
       serial: f0:76:1c:aa:57:44
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:49 ioport:4000(size=256) memory:d1204000-d1204fff memory:d1200000-d1203fff
  *-network
       description: Wireless interface
       product: Wireless 3160
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlp4s0
       version: 93
       serial: b4:6d:83:32:b1:cb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.13.0-16-generic firmware=17.459231.0 ip=192.168.1.190 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:54 memory:d1100000-d1101fff
[dracarys:~]$ ifconfig
enp3s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether f0:76:1c:aa:57:44  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 2291  bytes 428008 (428.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2291  bytes 428008 (428.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp4s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.190  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 2600:1700:f020:3b10::47  prefixlen 128  scopeid 0x0<global>
        inet6 2600:1700:f020:3b10:4d8e:230a:93e2:d85d  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::17d2:40f4:aab6:c5cf  prefixlen 64  scopeid 0x20<link>
        inet6 2600:1700:f020:3b10:80ba:6841:cdbb:4600  prefixlen 64  scopeid 0x0<global>
        ether b4:6d:83:32:b1:cb  txqueuelen 1000  (Ethernet)
        RX packets 1600  bytes 1349598 (1.3 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 964  bytes 408284 (408.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


[dracarys:~]$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    20600  0        0 wlp4s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp4s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp4s0
[dracarys:~]$ 



```

With VPN(ExpressVPN)

```
[dracarys:~]$ sudo lshw -C network[sudo] password for dracarys: 
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 10
       serial: f0:76:1c:aa:57:44
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:49 ioport:4000(size=256) memory:d1204000-d1204fff memory:d1200000-d1203fff
  *-network
       description: Wireless interface
       product: Wireless 3160
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlp4s0
       version: 93
       serial: b4:6d:83:32:b1:cb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.13.0-16-generic firmware=17.459231.0 ip=192.168.1.190 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:54 memory:d1100000-d1101fff
[dracarys:~]$ ifconfig
enp3s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether f0:76:1c:aa:57:44  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 3424  bytes 640614 (640.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 3424  bytes 640614 (640.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


tun0: flags=4305<UP,POINTOPOINT,RUNNING,NOARP,MULTICAST>  mtu 1500
        inet 10.38.243.66  netmask 255.255.255.255  destination 10.38.243.65
        inet6 fe80::6b40:c318:487f:f2d0  prefixlen 64  scopeid 0x20<link>
        unspec 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  txqueuelen 100  (UNSPEC)
        RX packets 959  bytes 728247 (728.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1016  bytes 129680 (129.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp4s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.190  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 2600:1700:f020:3b10::47  prefixlen 128  scopeid 0x0<global>
        inet6 2600:1700:f020:3b10:4d8e:230a:93e2:d85d  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::17d2:40f4:aab6:c5cf  prefixlen 64  scopeid 0x20<link>
        inet6 2600:1700:f020:3b10:80ba:6841:cdbb:4600  prefixlen 64  scopeid 0x0<global>
        ether b4:6d:83:32:b1:cb  txqueuelen 1000  (Ethernet)
        RX packets 4108  bytes 2616831 (2.6 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2210  bytes 702625 (702.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


[dracarys:~]$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.38.243.65    128.0.0.0       UG    0      0        0 tun0
0.0.0.0         192.168.1.254   0.0.0.0         UG    600    0        0 wlp4s0
10.38.0.1       10.38.243.65    255.255.255.255 UGH   0      0        0 tun0
10.38.243.65    0.0.0.0         255.255.255.255 UH    0      0        0 tun0
45.56.154.48    192.168.1.254   255.255.255.255 UGH   0      0        0 wlp4s0
128.0.0.0       10.38.243.65    128.0.0.0       UG    0      0        0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp4s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp4s0



```

When it came to connecting the network initially I tried both using the GUI and then using terminal, as to the HOW I am doing most things I wish I could answer you, most of the things I've tried are trial and error from different forum posts with similiar problems


I rarely ever use Sudo with GUI only in cases like GEdit or Gparted

---

### Post by TheFu on 2017-11-07
So you are using wifi?

192.168.1.254 is the gateway/router?

Did you mean for the "metric" for the router connection to be obscenely high?  20600+?  Normally, that would have a default value of 0 to 100.

There might be something wrong with the DNS.
Can you ping the router by IP?
Can you ping 8.8.8.8?
Can you ping google.com?

Do those **in that order** and report where the failure happens.

---

### Post by verxius on 2017-11-07
Yes I am using WI-FI
As to the Metric I have no idea how to change that or how it became that value(what does this mean in laymans terms)
heres the output of those commands
```
[dracarys:~]$ ping 192.168.1.254 PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
64 bytes from 192.168.1.254: icmp_seq=1 ttl=64 time=4.90 ms
64 bytes from 192.168.1.254: icmp_seq=2 ttl=64 time=3.58 ms
64 bytes from 192.168.1.254: icmp_seq=3 ttl=64 time=2.36 ms
64 bytes from 192.168.1.254: icmp_seq=4 ttl=64 time=2.47 ms
64 bytes from 192.168.1.254: icmp_seq=5 ttl=64 time=3.99 ms
^C
--- 192.168.1.254 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4004ms
rtt min/avg/max/mdev = 2.365/3.463/4.901/0.956 ms
[dracarys:~]$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=55 time=26.0 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=55 time=27.0 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=55 time=27.4 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=55 time=43.1 ms
^C
--- 8.8.8.8 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 26.021/30.919/43.148/7.083 ms
[dracarys:~]$ ping www.google.com
ping: www.google.com: Name or service not known
[dracarys:~]$ 



```

---

### Post by TheFu on 2017-11-07
The metric is the priority for a specific routing solution when/if there are conflicts. 

So - it appears you don't actually have any network issues.
[B]
You have a DNS issue. [/B] That is where you need to concentrate.  Fix the DNS issue.   resolveconf is the package that controls the /etc/resolv.conf file. This is where DNS servers are set for the entire system.  If you can't reach those, there should be 2-3 DNS servers specified.  Try to ping the DNS servers specified inside your resolv.conf file.

---

