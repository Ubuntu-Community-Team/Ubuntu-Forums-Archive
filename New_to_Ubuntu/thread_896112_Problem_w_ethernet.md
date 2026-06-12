---
title: "Problem w/ ethernet?"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by 7ehWhitey on 2008-08-20
(Desktop = Ubuntu; Laptop = Vista)

I just downloaded and installed the latest version of Ubuntu and I'm now having difficulties connecting to the internet.  I use an ethernet cord from my desktop to my laptop and my laptop uses a network bridge to give my desktop internet.  

I'm not sure how to diagnose the problem (this is my first time using linux) I've tried browsing other topics to find the answer to my problem and I'm still clueless from what I've gathered it may be a problem with the drivers for my chipset but I'm not exactly sure how to tell which chipset I have or how to install the new drivers if I did know my chipset.

---

### Post by Dr Small on 2008-08-20
Is your ethernet cable a crossover cable?

---

### Post by 7ehWhitey on 2008-08-20
Yes, it is.

---

### Post by Dr Small on 2008-08-20
Have you tried setting up the network configuration to use the laptop's IP as the gateway, and have the proper subnet mask, etc ?

---

### Post by 7ehWhitey on 2008-08-20
Yea, I'm pretty sure anyway, networking has never really been a strength of mine.

---

### Post by ugm6hr on 2008-08-20
Give the output from the following commands (on your Ubuntu desktop):
```
lspci
lshw -class network
route -n
ifconfig
```

They will help identify:
1. Your hardware / chipset
2. The driver being used
3. The IP gateway (if connected)
4. Your IP

---

### Post by 7ehWhitey on 2008-08-20
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
03:03.0 Communication controller: Conexant HSF 56k Data/Fax Modem
03:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)

  *-network               
       description: Ethernet interface
       product: 82801G (ICH7 Family) LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:9b:aa:2e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.1.100 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0


eth0      Link encap:Ethernet  HWaddr 00:12:3f:9b:aa:2e  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fe9b:aa2e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:282 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28205 (27.5 KB)  TX bytes:25199 (24.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1578 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1578 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:79588 (77.7 KB)  TX bytes:79588 (77.7 KB)

---

### Post by ugm6hr on 2008-08-20
The important bits:
> 
03:08.0 Ethernet controller: **Intel Corporation 82801G **(ICH7 Family) LAN Controller (rev 01)

configuration: broadcast=yes **driver=e100** driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.1.100 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes

inet addr:192.168.1.100


Judging by that, everything is looking OK:
Intel chipset, e100 driver, IP address

Try pinging the Gateway (laptop):
```
ping 192.168.1.1
```
Use Ctrl+C to stop it.

---

### Post by 7ehWhitey on 2008-08-20
Pinging 192.168.1.1
Reply from 192.168.1.1: bytes=32 time=2ms TTL=64
Reply from 192.168.1.1: bytes=32 time=1ms TTL=64
Reply from 192.168.1.1: bytes=32 time=1ms TTL=64
Reply from 192.168.1.1: bytes=32 time=1ms TTL=64

Ping statistics for 1992.168.1.1:
     Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trim times in milli-seconds:
     Minimum = 1ms, Maximum = 2ms, Average = 1ms

---

### Post by 7ehWhitey on 2008-08-21
Does this mean it is a problem with my settings?  Though I'm pretty sure I set it up right..

---

### Post by forger on 2008-08-21
How about going the other way around, connect the ubuntu/desktop as a gateway/bridge then connect the vista/laptop to it? Does the desktop have internet then?

---

### Post by 7ehWhitey on 2008-08-21
My desktop doesn't have a wireless card which is how I get internet on my laptop, what would bridging my ubuntu desktop do exactly.

I'm probably misunderstanding you.

---

### Post by Abdulkarim on 2008-08-21
Try to verify your network satting if it is automatic or manual network configuration. Reset the ip address then restart your computer!

---

### Post by 7ehWhitey on 2008-08-21
I've tried it on automatic and manual static IP but neither are working for me.

---

### Post by icecloud on 2008-08-21
ok this will sound long winded (plz mind it though)

1. does your laptop get internet and is it able to access the internet?

2. what settings are you using in vista? vista doesnt even like to network with windows xp let alone any other operating system so i honestly think its probably something in your vista o/s rather than your new linux box.

3. try to ping the ip of your desktop from your laptop to see if your laptop even recognizes that its there. you can do this in the command prompt.

4. try sharing things over your network on your laptop or your desktop (dont know how to do this in ubunto yet myself) but i do know how to in vista you should just be able to right click the folder (name it a generic name TIM'S TEST 1 or something) and click sharing in the properties. you should then be able to see whether or not your pc's can actually talk to each other.

---

### Post by 7ehWhitey on 2008-08-21
1. Yes, my laptop is able to access and view the internet.

2. What settings do you mean?  I have it networking fine with the rest of the computers in the house.

3. My laptop can ping my desktop.

4. I'm not sure how to share files on linux, someone said I would need to install Samba, but when I try it says something about not being able to find the file, my guess is its because I cant connect to the internet.

---

### Post by 7ehWhitey on 2008-08-21
I was messing around with some settings on my laptop and I my ipv4 settings to static instead of automatic and gave my desktop the same static ip settings and now my desktop gets internet but my laptop doesn't do to the conflicting ip addresses.  This problem was probably alot simpler then I was making it, though where do I go from here?

---

### Post by ugm6hr on 2008-08-21
> **7ehWhitey said:**
> Pinging 192.168.1.1
Reply from 192.168.1.1: bytes=32 time=2ms TTL=64
Reply from 192.168.1.1: bytes=32 time=1ms TTL=64
Reply from 192.168.1.1: bytes=32 time=1ms TTL=64
Reply from 192.168.1.1: bytes=32 time=1ms TTL=64

Ping statistics for 1992.168.1.1:
     Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trim times in milli-seconds:
     Minimum = 1ms, Maximum = 2ms, Average = 1ms

This looks like the desktop and laptop are connected correctly.

Now, from the Ubuntu desktop, try pinging google.com:
```
ping www.google.com
ping 216.239.59.99
```
Again: Ctrl+C to end

If this also works - then the problem is with Firefox.
If 216.etc works, but google.com doesn't, the problem is probably ipv6 related.
If neither works, the problem is with Vista's internet sharing setup.

---

### Post by 7ehWhitey on 2008-08-21
The problem is with my internet sharing, I gave both my laptop and desktop the same static ip and then my desktop had internet and my laptop got the "conflicting ip" message, so it didn't.  I'm thinking what I'm going to try is to go into my registry on my laptop and edit it to allow dhcp, because its currently disabled.

If anyone else knows an easier way, please let me know.

---

### Post by icecloud on 2008-08-21
you should be able to allow dhcp through your services if i remember correctly. you could try that before messing with your registry.

---

### Post by 7ehWhitey on 2008-08-21
I searched around for a bit and this was the only way I could find to do it.

---

### Post by 7ehWhitey on 2008-08-21
Fixed.

---

