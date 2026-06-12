---
title: "Internet connection Hardy Heron"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Jim_in_Germany on 2008-04-24
Hi,

This morning I installed Hardy Heron (yay!)
Problem is, in a nutshell that the internet now doesn't work.

My desktop PC has a nvidia mcp55 network card and is connected by lan cable via a switch to a speedport router.

I dual boot the pc with Win XP, and there the internet connection works fine. I can therefore exclude a problem with the cable, switch, ethernet card or router.

The problem definitely lies with Hardy Heron.

In Win XP I would open a shell, type ipconfig, see if I can find the standard gateway and take it from there.

As I am new to Linux, I am not sure where to start.

Any help grately appreciated.

P.S. I am writing this from a laptop connected to the router by a wireless access point. I was just playing around with Hardy on my other PC, and it crashed the router which then needed a hard reset.
Could it be to do with IPv6???

---

### Post by swoll1980 on 2008-04-24
click on your network manager in the taskbar do manual configure click on the interface you want to set up hit properties disable roming mode and set it up for dhcp see if that helps

---

### Post by philinux on 2008-04-24
Try connecting the Hardy pc on it's own, directly to the router.

---

### Post by Jim_in_Germany on 2008-04-24
Hi there,

Cheers for the quick reply.

I tried both suggestions and neither work.
:-(

Does anyone have any other ideas?

---

### Post by jtrink on 2008-04-24
it may be possible that your nic isn't supported...

---

### Post by Jim_in_Germany on 2008-04-24
Yeah, I thought that, but why would it work perfectly under Gutsy, but not under Hardy?

---

### Post by subSkipper on 2008-04-24
When I first installed Hardy my wired internet connection failed during the installation procedure (through no fault of Hardy or XP) and as a consequence I couldn't access the Internet on my Ubuntu laptop once the installation was done. It took me a while to figure out what had happened since it was only a short break in the service, but I simply re-installed Hardy and made sure that I had a working wired connection throughout the installation procedure. It worked like a charm after that.

---

### Post by Jim_in_Germany on 2008-04-24
Nope, wasn't that.
I tried reinstalling Hardy whilst waiting for replies to my posts.
I was on my laptop the whole time and had internet connectivity.

It's like the Hardy PC cannot find the router.
I unplug the LAN cablefrom the PC with no conbnectivity, plug it into the laptop and have internet straight away.

Would be a shame if this meant I couldn't upgrade.

---

### Post by milosz.galazka on 2008-04-24
Hello,

Try to run
```
ifconfg -a
```

You will see something similar to

```
milosz@milosz-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:9d:43:79
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:255 Base address:0x2000

eth1      Link encap:Ethernet  HWaddr 00:02:44:7a:1d:75
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:44ff:fe7a:1d75/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1810300 errors:0 dropped:0 overruns:0 frame:0
          TX packets:989853 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2583011063 (2.4 GB)  TX bytes:74978570 (71.5 MB)
          Interrupt:17 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:498 errors:0 dropped:0 overruns:0 frame:0
          TX packets:498 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:24900 (24.3 KB)  TX bytes:24900 (24.3 KB)
```

Then for example you could try 
```
sudo dhclient eth0
```

I have mpc61 and this card is working:
```
sudo lspci -v
```
```

00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
        Subsystem: Giga-byte Technology Unknown device e000
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 511
        Memory at f5107000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at bc00 [size=8]
        Capabilities: [44] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/3 Enable+
        Capabilities: [6c] HyperTransport: MSI Mapping
```

```
milosz@milosz-desktop:~$ dmesg | grep eth
```
```
[   23.605454] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   24.124573] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1a:4d:9d:43:79
[   24.124578] forcedeth 0000:00:07.0: highdma pwrctl mgmt timirq gbit lnktim msi desc-v3
[   42.751196] eth0: no link during initialization.
```
Ethernet cable is not connected to it, but card is working.
At install there was no network but this was probably connected to this [bug]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/212271").

---

### Post by Jim_in_Germany on 2008-04-24
Cheers for that.
I tried running what you suggested, wasn't too sure what I was looking for though.

sudo dhclient eth0 produced:
No DHCP offers received
No working leases in persistent database ...

It really seems like DHCP is the problem (when I try to ping sth. I get the message: host not found).

How can I fix it though??

---

### Post by Jim_in_Germany on 2008-04-24
Oh yeah, when I typed dmesg | grep eth, I got the message:
eth1:link is not ready.

---

### Post by milosz.galazka on 2008-04-24
> **Jim_in_Germany said:**
> Oh yeah, when I typed dmesg | grep eth, I got the message:
eth1:link is not ready.

```
milosz@milosz-desktop:~/Pulpit$ lsmod | grep eth
forcedeth              55564  0
```

what is output of
```
sudo ethtool eth1
```
?

---

### Post by Jim_in_Germany on 2008-04-24
Hi,

I've had another idea. I'm going to reinstall Gutsy and update from within Gutsy to Hardy. I have it in the back of my mind that I read somewhere that this is possible.

Then maybe there is a chance that Internet will work too.

The whole process will take ca. 40 mins.

Then I'll post back here.

---

### Post by Jim_in_Germany on 2008-04-24
This also lets me inspect a working network configuration in Gutsy.
I never really paid much attention to it before.

---

### Post by sagor on 2008-04-24
Could it be that under Hardy, the autospeed of the NIC is set/reset differently? After installing Hardy, try resetting your router - check the status lights if you have any to see if it is 10/100 or HDX/FDX. Of course, check the link light too.
It may be that some default setting of the NIC may confuse it between the NIC and Router..

Just a thought, I've seen this happen at times in "other" O/S. Sometimes the NIC is init to 10mbits, and the router still expects to see the 100mbits and does not auto-speed...

---

### Post by Jim_in_Germany on 2008-04-24
Hi,

Just completed Gutsy reinstall.
Is there any helpful information I could look at before trying to update to Hardy?

---

### Post by Jim_in_Germany on 2008-04-24
Unfortunately resetting my router was the first thing I tried as trying to connect to the net with Hardy killed my laptop's wireless INternet connection (laptop running Win XP).

Is there any way under Linux to chek the aforementioned settings on the nic card?

---

### Post by milosz.galazka on 2008-04-24
sudo ethtool eth1
You mean that command?

---

### Post by Jim_in_Germany on 2008-04-24
Ah, that'll be what that does then
:-)
I'm just updating Firefox and co. (as Gutsy comes bundled with 2.0.0.6) which suffers from some kind of bug which makes it real slow. After that I'll post the data from both my onboard ethernet cards from a working Gutsy configuration.

---

### Post by Jim_in_Germany on 2008-04-24
By the way, as I have two ethernet ports, how can I tell which one is currently in use?
Windows has like a warning "cable removed" for the one not in use

---

### Post by milosz.galazka on 2008-04-24
> **Jim_in_Germany said:**
> By the way, as I have two ethernet ports, how can I tell which one is currently in use?
Windows has like a warning "cable removed" for the one not in use

ethtool will for example show you
```
        Speed: 100Mb/s
        Duplex: Full
```
if there is a connection or something similar
```
        Speed: Unknown! (65535)
        Duplex: Unknown! (255)
```
otherwise.

ifconfig -a will show if there is ip address assigned

cat /var/log/messages | grep eth1 contains every link changes
```
Apr 23 23:43:50 milosz-desktop kernel: [   42.781523] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
```

there are ways too...

---

### Post by Jim_in_Germany on 2008-04-24
That's cool. Thanks

So, Gutsy is up and running, here is the printout from sudo ethtool eth0

        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: external
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Link detected: yes

I guess that is the live one

And here is ethtool eth1

        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: Unknown! (65535)
        Duplex: Unknown! (255)
        Port: MII
        PHYAD: 1
        Transceiver: external
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Link detected: no

I will now update to Hardy (via gksu "update-manager -c") and will let you know if it works

---

### Post by milosz.galazka on 2008-04-24
I just saw that here is a 
Link detected: yes/no
I didn't noticed it :)

---

### Post by ekravche on 2008-04-24
Try running an older kernel like 2.4.22. The latest kernel has broken wireless for me to...

---

### Post by Jim_in_Germany on 2008-04-24
Ok, I upgraded to Hardy from a working Gutsy and ....

No internet!!!

Here is the printout from ethtool eth0

Supported ports: [ MII ]
Supported link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
1000baseT/Full
Supports auto-negotiation: Yes
Advertised link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
1000baseT/Full
Advertised auto-negotiation: Yes
Speed: 100Mb/s
Duplex: Full
Port: MII
PHYAD: 1
Transceiver: external
Auto-negotiation: on
Supports Wake-on: g
Wake-on: d
Link detected: yes

CAn anyone help??:(

---

### Post by milosz.galazka on 2008-04-24
> **Jim_in_Germany said:**
> Ok, I upgraded to Hardy from a working Gutsy and ....

No internet!!!

Here is the printout from ethtool eth0

Supported ports: [ MII ]
Supported link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
1000baseT/Full
Supports auto-negotiation: Yes
Advertised link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
1000baseT/Full
Advertised auto-negotiation: Yes
Speed: 100Mb/s
Duplex: Full
Port: MII
PHYAD: 1
Transceiver: external
Auto-negotiation: on
Supports Wake-on: g
Wake-on: d
Link detected: yes

CAn anyone help??:(

```
sudo dhclient eth0
```
this maybe could help

---

### Post by Jim_in_Germany on 2008-04-24
Hi,

I'm afraid that sudo dhclient eth0 comes back:
No DHCPOFFERS received
No working leases in persistent database - sleeping

---

### Post by milosz.galazka on 2008-04-24
Could you look at logs in your router/access point?

Could you assign static ip (sudo ifconfig eth0 *ip_address* like 192.168.0.101) on the computer and then try to ping outer/access point?

---

### Post by Jim_in_Germany on 2008-04-24
I assigned myself the ip 192.168.2.110.
I could ping myself (obviously) but as soon as I tried to ping the acces point I got the message - "destination host unreachable".
I also cannot access the config interface of the router via the browser.

---

### Post by milosz.galazka on 2008-04-24
Look here [https://bugs.launchpad.net/ubuntu/+bug/136836](https://bugs.launchpad.net/ubuntu/+bug/136836)

---

### Post by Jim_in_Germany on 2008-04-24
Yay it works!!!!
Thank you very much indeed for helping me out.
You are a star!

For anyone with the same problem, this is what I did:

Run gedit as root and open /etc/rc.local
Atl+F2 -> gksu gedit /etc/rc.local 

Paste the following lines between the comment lines and exit0:
rmmod forcedeth
modprobe forcedeth msi=0 msix=0
/etc/init.d/networking restart

Restart the computer and that's it!

---

### Post by wilsonmuse on 2008-04-24
```
ifconfig
```

This should show working network interface cards "eth0". There should also be a loopback interface "lo"

if you have no "eth" in the output from that command your interface is not configured and working. Use this to find out what interfaces you are missing:

```
ifconfig -a
```

If an "eth" interface is returned by that command but not by the first (ifconfig) try to get it working using this where "eth" is the name of that interface (eth0, eth1, eth5):

```
sudo ifconfig eth up
```

if no errors were returned you can now try to connect with this where "eth" is the name of your interface (eth0, eth1, eth3):

```
sudo dhclient eth
```


Edit: Too late :D

---

### Post by Jim_in_Germany on 2008-04-24
Cheers anyway:)

---

### Post by bebox on 2008-04-26
> **Jim_in_Germany said:**
> I assigned myself the ip 192.168.2.110.
I could ping myself (obviously) but as soon as I tried to ping the acces point I got the message - "destination host unreachable".
I also cannot access the config interface of the router via the browser.

hi...i use static ip and have the same problem...i tried what you said and it isn't fixing the problem

bebox@bebox:~$ ping 40.30.5.100
PING 40.30.5.100 (40.30.5.100) 56(84) bytes of data.
From 40.30.5.62 icmp_seq=1 Destination Host Unreachable
From 40.30.5.62 icmp_seq=2 Destination Host Unreachable
From 40.30.5.62 icmp_seq=3 Destination Host Unreachable

here is my ifconfig...if anybody can help me..please:

eth0      Link encap:Ethernet  HWaddr 00:13:8f:89:7a:fd  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:27 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:250 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:0a:5e:3f:44:d8  
          inet addr:40.30.5.62  Bcast:40.30.5.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1222 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1222 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:65016 (63.4 KB)  TX bytes:65016 (63.4 KB)

---

### Post by milosz.galazka on 2008-04-26
> **bebox said:**
> hi...i use static ip and have the same problem...i tried what you said and it isn't fixing the problem

bebox@bebox:~$ ping 40.30.5.100
PING 40.30.5.100 (40.30.5.100) 56(84) bytes of data.
From 40.30.5.62 icmp_seq=1 Destination Host Unreachable
From 40.30.5.62 icmp_seq=2 Destination Host Unreachable
From 40.30.5.62 icmp_seq=3 Destination Host Unreachable

here is my ifconfig...if anybody can help me..please:

eth0      Link encap:Ethernet  HWaddr 00:13:8f:89:7a:fd  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:27 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:250 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:0a:5e:3f:44:d8  
          inet addr:40.30.5.62  Bcast:40.30.5.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1222 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1222 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:65016 (63.4 KB)  TX bytes:65016 (63.4 KB)

Do you have nvidia ethernet? If yes then there is a link [https://bugs.launchpad.net/ubuntu/+bug/136836](https://bugs.launchpad.net/ubuntu/+bug/136836) on third page :)

---

### Post by andyrue304 on 2008-04-26
> **Jim_in_Germany said:**
> Yay it works!!!!
Thank you very much indeed for helping me out.
You are a star!

For anyone with the same problem, this is what I did:

Run gedit as root and open /etc/rc.local
Atl+F2 -> gksu gedit /etc/rc.local 

Paste the following lines between the comment lines and exit0:
rmmod forcedeth
modprobe forcedeth msi=0 msix=0
/etc/init.d/networking restart

Restart the computer and that's it!

This didn't work for me.

Maybe 'cause I was just logged in as my standard user name?

How do you log in as 'root'?

---

### Post by milosz.galazka on 2008-04-26
> **andyrue304 said:**
> This didn't work for me.

Maybe 'cause I was just logged in as my standard user name?

How do you log in as 'root'?

You can type 'sudo su' in gnome terminal to gain root privileges.
gksu allows you to open X applications as root.

What is output of
sudo lspci -v
regarding nvidia ethernet?

---

### Post by andyrue304 on 2008-04-26
> **milosz.galazka said:**
> You can type 'sudo su' in gnome terminal to gain root privileges.
gksu allows you to open X applications as root.

What is output of
sudo lspci -v
regarding nvidia ethernet?

Hi Milosz,

thanks for that reply.

sudo lspci -v
seems to return a lot!

I tried again with the original comment on the above link and the internet seems to be working (for now) I'm going to try and restart and then will post again.

EDIT: Ok, so I restarted and it wouldn't work again. It works when I do this in the terminal:

```
$ sudo su
# rmmod forcedeth
# modprobe forcedeth msi=0 msix=0
# /etc/init.d/networking restart

```

This is exactly what I've added in the rc.local, which I've now edited as root and I've checked to see if the code is still there.

Here's the output of the sudo lspci -v command: (sorry to post it all but don't know which bits are important!)

```
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [40] HyperTransport: Host or Secondary Interface

00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: bus master, 66MHz, fast devsel, latency 0

00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: ea000000-edffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0c55
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: efc00000-efcfffff
	Prefetchable memory behind bridge: 00000000ef900000-00000000ef9fffff
	Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0c55
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: efe00000-efefffff
	Prefetchable memory behind bridge: 00000000efd00000-00000000efdfffff
	Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0c55
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
	Subsystem: ASUSTeK Computer Inc. Unknown device cb84
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [44] HyperTransport: Slave or Primary Interface
	Capabilities: [e0] #00 [fee0]

00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device cb84
	Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device cb84
	Flags: 66MHz, fast devsel, IRQ 5
	I/O ports at ff00 [size=64]
	I/O ports at 1c00 [size=64]
	I/O ports at 1c80 [size=64]
	Capabilities: [44] Power Management version 2

00:0a.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device cb84
	Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device cb84
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at effff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device cb84
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at efffe000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port
	Capabilities: [80] Power Management version 2

00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device f043:cb84
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at fc00 [size=16]
	Capabilities: [44] Power Management version 2

00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Unknown device cb84
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at f700 [size=16]
	Memory at efffd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
	Capabilities: [cc] HyperTransport: MSI Mapping

00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Unknown device cb84
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at f200 [size=16]
	Memory at efffc000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
	Capabilities: [cc] HyperTransport: MSI Mapping

00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Unknown device cb84
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at f100 [size=8]
	I/O ports at f000 [size=4]
	I/O ports at ef00 [size=8]
	I/O ports at ee00 [size=4]
	I/O ports at ed00 [size=16]
	Memory at efffb000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
	Capabilities: [cc] HyperTransport: MSI Mapping

00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: efb00000-efbfffff
	Prefetchable memory behind bridge: efa00000-efafffff
	Capabilities: [b8] Subsystem: nVidia Corporation Unknown device cb84
	Capabilities: [8c] HyperTransport: MSI Mapping

00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 81f2
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at efff0000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Capabilities: [6c] HyperTransport: MSI Mapping

00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device cb84
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at efffa000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at ec00 [size=8]
	Memory at efff9000 (32-bit, non-prefetchable) [size=256]
	Memory at efff8000 (32-bit, non-prefetchable) [size=16]
	Capabilities: [44] Power Management version 2
	Capabilities: [70] MSI-X: Enable- Mask- TabSize=8
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/3 Enable-
	Capabilities: [6c] HyperTransport: MSI Mapping

00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device cb84
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at efff7000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at eb00 [size=8]
	Memory at efff6000 (32-bit, non-prefetchable) [size=256]
	Memory at efff5000 (32-bit, non-prefetchable) [size=16]
	Capabilities: [44] Power Management version 2
	Capabilities: [70] MSI-X: Enable- Mask- TabSize=8
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/3 Enable-
	Capabilities: [6c] HyperTransport: MSI Mapping

00:13.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: ef800000-ef8fffff
	Prefetchable memory behind bridge: 00000000ef700000-00000000ef7fffff
	Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:14.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 00008000-00008fff
	Memory behind bridge: ef600000-ef6fffff
	Prefetchable memory behind bridge: 00000000ef500000-00000000ef5fffff
	Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:15.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: ef400000-ef4fffff
	Prefetchable memory behind bridge: 00000000ef300000-00000000ef3fffff
	Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:16.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: ef200000-ef2fffff
	Prefetchable memory behind bridge: 00000000ef100000-00000000ef1fffff
	Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:17.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: ef000000-ef0fffff
	Prefetchable memory behind bridge: 00000000eef00000-00000000eeffffff
	Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:18.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: eee00000-eeefffff
	Prefetchable memory behind bridge: 00000000eed00000-00000000eedfffff
	Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8234
	Flags: bus master, fast devsel, latency 0, IRQ 7
	Memory at ec000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at ea000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at df00 [size=128]
	Expansion ROM at edfe0000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint IRQ 0

04:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 81fe
	Flags: bus master, medium devsel, latency 32, IRQ 19
	Memory at efbff000 (32-bit, non-prefetchable) [size=2K]
	I/O ports at cf00 [size=128]
	Capabilities: [50] Power Management version 2

```

---

### Post by andyrue304 on 2008-04-26
I have new info (please see above post)

---

### Post by milosz.galazka on 2008-04-26
You could add a line
```
forcedeth msi=0 msix=0
```
to */etc/modules* file, remove modifications of */etc/rc.local*, reboot and then see if it is working...

---

### Post by andyrue304 on 2008-04-26
> **milosz.galazka said:**
> You could add a line
```
forcedeth msi=0 msix=0
```
to */etc/modules* file, remove modifications of */etc/rc.local*, reboot and then see if it is working...

Nope...

Still had to

```
sudo su

rmmod forcedeth

modprobe forcedeth msi=0 msix=0

/etc/init.d/networking restart
```

After rebooting :confused:

---

### Post by milosz.galazka on 2008-04-26
Look [here]("http://ubuntuforums.org/showthread.php?t=691372&page=2") as somebody has same problem solved :)

---

### Post by andyrue304 on 2008-04-26
> **milosz.galazka said:**
> Look [here]("http://ubuntuforums.org/showthread.php?t=691372&page=2") as somebody has same problem solved :)

This doesn't work for me either :confused:

---

### Post by milosz.galazka on 2008-04-26
[Here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/136836/comments/11") is information how to rebuild initramfs

---

### Post by andyrue304 on 2008-04-26
This bit > NOTE: if the update-initramfs bit goes wrong it could stop your system from booting - don't blame me - make sure you know how to fix it first. sounds very ominous!

How would I fix it if this goes wrong? Complete re-install?

So far I have Ubuntu installed via wubi so that wouldn't be a problem :)

---

### Post by milosz.galazka on 2008-04-26
> **andyrue304 said:**
> This bit  sounds very ominous!

How would I fix it if this goes wrong? Complete re-install?

So far I have Ubuntu installed via wubi so that wouldn't be a problem :)

backup your /boot directory, it should be sufficient to recover using bootable cd

---

### Post by andyrue304 on 2008-04-26
> **milosz.galazka said:**
> backup your /boot directory, it should be sufficient to recover using bootable cd

Do i have to name it (the backup) anything in particular?

Then burn it to a disk or just leave it on the hard disk?

:lolflag:sorry I feel like a right idiot!

---

### Post by milosz.galazka on 2008-04-26
just copy it under new name so if something goes wrong you could use old initramfs file

it's fine, it's always better to ask  :)

---

### Post by andyrue304 on 2008-04-26
YYYYYYYYAAAAAAAAAAAAAAYYYYYYYYYYY!!!!!!!!

It works!

Thankyou so much everyone for all your help!:-D 8)

---

### Post by bebox on 2008-04-27
[QUOTE=milosz.galazka;4798198]Do you have nvidia ethernet? If yes then there is a link [https://bugs.launchpad.net/ubuntu/+bug/136836](https://bugs.launchpad.net/ubuntu/+bug/136836) on third page :)[/Q

no...i don't have nvidia...it's ralink i think...?

---

### Post by Marky-Mark47 on 2008-04-27
Did you try rebooting your router?  I also lost my internet connection after installing Hardy, but switching off the power to my router, then switching it back on solved it!


> **Jim_in_Germany said:**
> Hi,

This morning I installed Hardy Heron (yay!)
Problem is, in a nutshell that the internet now doesn't work.

My desktop PC has a nvidia mcp55 network card and is connected by lan cable via a switch to a speedport router.

I dual boot the pc with Win XP, and there the internet connection works fine. I can therefore exclude a problem with the cable, switch, ethernet card or router.

The problem definitely lies with Hardy Heron.

In Win XP I would open a shell, type ipconfig, see if I can find the standard gateway and take it from there.

As I am new to Linux, I am not sure where to start.

Any help grately appreciated.

P.S. I am writing this from a laptop connected to the router by a wireless access point. I was just playing around with Hardy on my other PC, and it crashed the router which then needed a hard reset.
Could it be to do with IPv6???

---

### Post by milosz.galazka on 2008-04-27
> **bebox said:**
> [QUOTE=milosz.galazka;4798198]Do you have nvidia ethernet? If yes then there is a link [https://bugs.launchpad.net/ubuntu/+bug/136836](https://bugs.launchpad.net/ubuntu/+bug/136836) on third page :)[/Q

no...i don't have nvidia...it's ralink i think...?

Try here:
[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.24/+bug/134660](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.24/+bug/134660)

You should post new thread so more people could see it :)

EDIT: this link is about wireless ;/, sorry

---

