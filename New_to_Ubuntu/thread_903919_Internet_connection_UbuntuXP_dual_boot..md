---
title: "Internet connection Ubuntu/XP dual boot."
date: 2008-08-28
forum: New to Ubuntu
---

### Post by onetiger on 2008-08-28
My BT Voyager modem/router is normally connected to my computer by a usb cable and worked perfectly on both Ubuntu and XP in my dual boot set up.

XP got a bad virus so I reformatted the XP partition and just worked with Ubuntu for a few weeks with no problems browsing the internet.

After that, I re installed XP to its partition and I did reinstall the driver for connecting by usb but XP's New Hardware Wizard refused to find the driver so XP couldn't connect to the internet. For some reason, Ubuntu decided not to connect as well.  Neither O/S would connect to the internet.

I unplugged the usb cable and plugged in the ethernet cable (the Voyager can take either). XP immediately connected to the internet but Ubuntu just hunts and hunts.  It did manage to connect to a web page at first (after about 5 minutes) but now it just hunts and gets nowhere.

I think it's strange that XP couldn't find the usb driver this time round (it's definitely the correct driver) but my main worry is getting Ubuntu connecting to the internet again. I'm guessing it's a driver issue but I might be barking up the wrong tree altogether.

Any advice would be appreciated.

---

### Post by blastus on 2008-08-28
My advice; ditch the USB modem and get a real modem that has a network jack and hook it up to a router.

Most USB modems are like internal PCI modems in that they don't have the necessary hardware to function without proprietary Windows drivers. They are so-called "Winmodems." I would never buy or use a USB modem for that reason.

---

### Post by alienexplorers on 2008-08-28
Have you tried unplugging the modem/router from the wall, shutting down ubuntu/windows.  Wait about 10 seconds and restart the modem/router and the restarting ubuntu to see if it connects.

---

### Post by onetiger on 2008-08-29
blastus. My router/modem is ethernet and usb. I originally chose to use the usb connection because it is supposed to be faster. The Voyager has worked perfectly on XP for nigh on 2 years and it was working brilliantly on Linux too. 

alienexplorers. I've tried your suggestion but it did not make a difference.

---

### Post by ugm6hr on 2008-08-29
Read this: [http://ubuntuforums.org/showpost.php?p=5024425&postcount=1](http://ubuntuforums.org/showpost.php?p=5024425&postcount=1)

Specifically, look at number 8 in Windows.

With the modem plugged in and turned on at bootup, give details:
```
lshw -class network
ifconfig
route -n
```

Do you use Network Manager?

---

### Post by onetiger on 2008-08-29
Hi ugm6hr
I did open the Ubuntu network tools before I originally posted but I have no idea how to tinker with them. I am connecting to the internet using Windows and the ethernet connection.  
Here is the output I got from the commands you posted and the link you gave me :-

ken@bag:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 662 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS966 [MuTIOL Media IO] (rev 59)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 190 Gigabit Ethernet Adapter (rev 01)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 02)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0b.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 04)
ken@bag:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 055f:0006 Mustek Systems, Inc. ScanExpress 1200 UB
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
ken@bag:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 190 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 01
       serial: 00:50:8d:98:ca:3d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis190 driverversion=1.2 ip=192.168.1.2 latency=0 module=sis190 multicast=yes
ken@bag:~$ 
ken@bag:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8d:98:ca:3d  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fe98:ca3d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1612 (1.5 KB)  TX bytes:5982 (5.8 KB)
          Interrupt:20 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2042 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2042 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:102100 (99.7 KB)  TX bytes:102100 (99.7 KB)

ken@bag:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

____________________________________________


I don't know if it will be any help but here is the output from IPCONFIG in Windows too :-

Windows IP configuration:

host name		    ken-86d6626aecfa
primary dns suffix          (blank)
Node Type		    Unknown
IP routing enabled	    No
Wins proxy enabled          No
DNS suffix search list	    home


Ethernet Adapter Local Area Connection:

Connection-specific DNS Suffix		home
Description				SiS190 100/10 Ethernet Device
Physical Address			00-50-8D-98-CA-3D
Dhcp Enabled				Yes
Autoconfiguration Enabled		Yes
IP Address				192.168.1.2
Subnet Mask				255.255.255.0
Default Gateway				192.168.1.1
Dhcp Server				192.168.1.1
DNS Servers				192.168.1.1

---

### Post by ugm6hr on 2008-08-29
Looks like you are connected to the modem OK - you have been assigned an IP.

Now try pinging:
```
ping -c3 192.168.1.1
ping -c3 66.102.9.99
ping -c3 www.google.co.uk
```

---

### Post by onetiger on 2008-08-29
ken@bag:~$ ping -c3 192.168.1.1


PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.855
ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.806 
ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.805
ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received,
0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.805/0.822/0.855/0.023


ken@bag:~$ ping -c3 66.102.9.99


PING 66.102.9.99 (66.102.9.99) 56(84) bytes of data.

64 bytes from 66.102.9.99: icmp_seq=1 ttl=244 time=69.2
ms
64 bytes from 66.102.9.99: icmp_seq=2 ttl=244 time=67.4
ms
64 bytes from 66.102.9.99: icmp_seq=3 ttl=244 time=68.5
ms

--- 66.102.9.99 ping statistics ---
3 packets transmitted,3 received,
0% packet loss, time 2002ms
rtt min/avg/max/mdev = 67.490/68.425/69.237/0.718 ms



ken@bag:~$ ping -c3 [www.google.com](www.google.com)


PING [www.l.google.com](www.l.google.com) (66.249.93.99) 56(84) bytes of data.

64 bytes from [www.google.com](www.google.com) (66.249.93.99): icmp_seq=1 ttl=244 time=49.5                                ms
64 bytes from [www.google.com](www.google.com) (66.249.93.99): icmp_seq=2 ttl=244 time=51.0
ms
64 bytes from [www.google.com](www.google.com) (66.249.93.99): icmp_seq=3 ttl=244 time=52.2                                ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
3 packetstransmitted,3received,
0% packet loss, time 1999ms
rtt min/avg/max/mdev = 49.512/50.918/52.211/1.104 ms


By the way, I forgot about this. When I said that Ubuntu (Firefox)
just hunted about forever when a web site is requested, there is 1 exception to that - Google -  it opens like a flash and, if you do a search for anything, it opens up its usual list of possible sites like lightning. Unfortunately, when you pick one, Firefox resumes hunting about.  This doesn't happen with Yahoo, Ask or any other of the search engines.

---

### Post by ugm6hr on 2008-08-30
> **onetiger said:**
> By the way, I forgot about this. When I said that Ubuntu (Firefox) just hunted about forever when a web site is requested, there is 1 exception to that - Google -  it opens like a flash and, if you do a search for anything, it opens up its usual list of possible sites like lightning. Unfortunately, when you pick one, Firefox resumes hunting about.  This doesn't happen with Yahoo, Ask or any other of the search engines.

That's odd - was that the case from the beginning?

Anyway, try pinging some of the sites that don't work:
```
ping -c3 www.yahoo.com
ping -c3 87.248.113.14)
```

In any case, I suspect this is an ipv6 issue with Firefox.  If you are able to ping sites from the Terminal successfully (as you have demonstrated with google), but Firefox doesn't, try looking at this:
[http://en.opensuse.org/Disable_IPv6_for_Firefox](http://en.opensuse.org/Disable_IPv6_for_Firefox)

---

### Post by onetiger on 2008-08-30
Yo ugm6hr

I managed to solve this!  :)


I tried a different usb driver from the Dynalink site and lo and behold, it works!  I booted into Windows and connected using the ethernet cable and downloaded and installed the usb driver.  It works in Ubuntu too without having to install any usb driver - I don't know why that is.  Now I am surfing in Linux and Windows using the usb cable.

The thing that puzzles me is when I was using the usb before with the dual boot, I got that bad virus in Windows so I reformatted the Windows partition.  I only had Ubuntu on the hard drive then yet the usb internet connection was working even though I had never installed a Linux driver for it.

Anyway, all's well that ends well. The fast Google phenonemen is another thing that baffles me but I'm not going to worry about it now.  I just want to thank you for all your help in what looked like being a real pain in the neck problem.

Thanks again.
Regards, Ken
  :guitar:

---

### Post by ugm6hr on 2008-08-30
Very bizarre.  From what you describe, it sounds like the XP driver was influencing the way the modem behaved with Ubuntu...

Anyway - all that ends well, eh?

---

### Post by airtonix on 2008-08-30
Let it be known that microsoft write software that presupposes you are an idiot and will take steps to interfere with your hardware based on this premise.

---

