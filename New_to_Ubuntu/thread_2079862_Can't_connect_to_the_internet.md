---
title: "Can't connect to the internet"
date: 2012-11-02
forum: New to Ubuntu
---

### Post by 4rings on 2012-11-02
Hi,

I have a Ubuntu Server that doesn't connect to the internet.  I don't use it for much but I built it from scratch so I keep on my home network.  I turned it on recently and installed all the upgrades.  It upgraded to 12.04 LTS I believe.  Ever since, it doesn't connect to the internet.  I have Ethernet LAN connectivity as I can see and ping my other machines, router etc., but no WAN.  I'm using the default Firefox web browser.  All other machines on the network (an array of Windows and a Mac, both Ethernet and wireless) are fine.  Any suggestions are greatly appreciated.

Thank you.

---

### Post by dannyboy79 on 2012-11-02
within a terminal can you ping [www.google.com?](www.google.com?)
what about pinging 74.125.224.18?

I am trying to figure out if it's a DNS issue because I doubt your ethernet controller would become unsupported but it is possible.

so also post the output of this command
```
lspci -v
```

---

### Post by 4rings on 2012-11-02
Hi dannyboy79,

Thanks for your reply.  Here are the answers to your questions:

Can I ping [www.google.com?](www.google.com?)  No.
scott@chimera:~$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

Can I ping 74.125.224.18? No.
scott@chimera:~$ ping 74.125.224.18
PING 74.125.224.18 (74.125.224.18) 56(84) bytes of data.
^C
--- 74.125.224.18 ping statistics ---
60 packets transmitted, 0 received, 100% packet loss, time 59370ms

Output from the lspci -v command:

scott@chimera:~$ lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
    Subsystem: VIA Technologies, Inc. K8M800 Host Bridge
    Flags: bus master, 66MHz, medium devsel, latency 8
    Memory at <ignored> (32-bit, prefetchable)
    Capabilities: <access denied>
    Kernel driver in use: agpgart-amd64

00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
    Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
    Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
    Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
    Flags: bus master, medium devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
    Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/8251 PCI bridge [K8M890/K8T800/K8T890 South] (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, medium devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Memory behind bridge: fa000000-fbffffff
    Prefetchable memory behind bridge: f8000000-f9ffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Biostar Microtech Int'l Corp Device 3206
    Flags: bus master, medium devsel, latency 32, IRQ 20
    I/O ports at de00 [size=8]
    I/O ports at e400 [size=4]
    I/O ports at e500 [size=8]
    I/O ports at dc00 [size=4]
    I/O ports at dd00 [size=16]
    I/O ports at d000 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sata_via
    Kernel modules: sata_via

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
    Subsystem: Biostar Microtech Int'l Corp Device 3206
    Flags: bus master, medium devsel, latency 32, IRQ 20
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    I/O ports at df00 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_via
    Kernel modules: pata_via

00:10.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
    Subsystem: Biostar Microtech Int'l Corp Device 3206
    Flags: bus master, medium devsel, latency 32, IRQ 21
    I/O ports at e000 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
    Subsystem: Biostar Microtech Int'l Corp Device 3206
    Flags: bus master, medium devsel, latency 32, IRQ 21
    I/O ports at e100 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
    Subsystem: Biostar Microtech Int'l Corp Device 3206
    Flags: bus master, medium devsel, latency 32, IRQ 21
    I/O ports at e200 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.3 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
    Subsystem: Biostar Microtech Int'l Corp Device 3206
    Flags: bus master, medium devsel, latency 32, IRQ 21
    I/O ports at e300 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.4 USB controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
    Subsystem: Biostar Microtech Int'l Corp Device 3206
    Flags: bus master, medium devsel, latency 32, IRQ 21
    Memory at fc000000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
    Subsystem: Biostar Microtech Int'l Corp Device 3206
    Flags: bus master, stepping, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: i2c-viapro

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
    Subsystem: Biostar Microtech Int'l Corp Device 8215
    Flags: medium devsel, IRQ 22
    I/O ports at d400 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: snd_via82xx
    Kernel modules: snd-via82xx

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
    Subsystem: Biostar Microtech Int'l Corp Device 2200
    Flags: bus master, medium devsel, latency 32, IRQ 23
    I/O ports at d800 [size=256]
    Memory at fc001000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: via-rhine
    Kernel modules: via-rhine

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k8temp
    Kernel modules: k8temp

01:00.0 VGA compatible controller: NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15) (prog-if 00 [VGA controller])
    Subsystem: NVIDIA Corporation M64 AGP4x
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
    Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
    Memory at f8000000 (32-bit, prefetchable) [size=32M]
    [virtual] Expansion ROM at fb000000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb, rivafb

scott@chimera:~$

---

### Post by dannyboy79 on 2012-11-02
hmmmm, your ethernet card is a Ethernet controller: VIA Technologies, Inc. VT6102. Try and google that to see if there are any bugs. Also, I need to know for sure what version you're using now.

I just find it hard to believe you had internet access, then proceeded to perform a version upgrade and then lost internet access. You sure the ethernet cord didn't get unplugged?

What does this return?
```
ifconfig -a
```

---

### Post by 4rings on 2012-11-02
Please tell me how best to obtain software version number.  Yes, I'm sure the Ethernet cable is plugged in as I am able to ping my router and see all other machines on my network.  I'm thinking that something might have gotten over written as at times along the upgrade process, I was prompted with whether I wanted to keep the existing file or over write it.  That happened a few times.  Maybe I over wrote a file when I should have kept it.

---

### Post by dannyboy79 on 2012-11-02
```
lsb_release -a
```

and the kernel
```
uname -r
```

what does your /etc/resolv.conf file contain in it?

and also your /etc/interfaces file.

---

### Post by 4rings on 2012-11-02
Hi dannyboy79,

Here are the answers to your questions:

scott@chimera:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.1 LTS
Release:    12.04
Codename:    precise

scott@chimera:~$ uname -r
3.2.0-32-generic

/etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

/etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# auto eth0
# iface eth0 inet dhcp

# Remove #'s from the following lines to manually configure a static IP address.
auto eth0
iface eth0 inet static
address     192.168.1.4
netmask      255.255.255.0
network   192.168.1.0
broadcast 192.168.1.255
gateway   192.168.1.1
 
Also, I checked on Google for bugs as you suggested.  I read over some things but I'm not sure if anything I read would be the cause of why the computer can't connect to the internet.

I  hope this helps.

Thank you.

---

### Post by dannyboy79 on 2012-11-03
do you have a router? does it use an MAC filtering or for any reason would be blocking the server's outgoing traffic to reach the internet?

can you ping 8.8.8.8?

---

### Post by sandyd on 2012-11-03
Can you post the result of
```

route -n
```
Thanks!

---

### Post by Cheesemill on 2012-11-03
12.04 changed the way that DNS is handled in /etc/resolv.conf

Instead of specifying your nameservers in resolv.conf they are now set up in the interfaces file. Try editing /etc/networking/interfaces and add the following line to the bottom:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# auto eth0
# iface eth0 inet dhcp

# Remove #'s from the following lines to manually configure a static IP address.
auto eth0
iface eth0 inet static
address     192.168.1.4
netmask      255.255.255.0
network   192.168.1.0
broadcast 192.168.1.255
gateway   192.168.1.1
[COLOR=Red]dns-nameservers 192.168.1.1[/COLOR]
```
I'm assuming that your router provides your DNS, alter the IP address accordingly if it doesn't.

This is one of your issues solved but there is another problem. You say that you can ping your router and other devices on your network but you can't ping external hosts by IP address. This means that there is a bigger connectivity problem somewhere, even without the change I've outlined above you should still have been able to ping 74.125.224.18 successfully.

Are you sure that the internet connection on your router is working correctly?

---

### Post by 4rings on 2012-11-03
Hi dannyboy79, sandyd and Cheesemill,

dannyboy79 and sandyd, I got the output you were asking for, and I added that dns-nameserver entry into the interfaces file while I was at it.

dannyboy79 and sandyd, thank you for your suggestions.  I really appreciate your time.

Cheesemill, your suggestion fixed my issue.  I added that entry and now I can connect to the internet on that machine.

A BIG thank you to the three of you!

---

### Post by dannyboy79 on 2012-11-03
awesome, I was leaning toward it being a DNS issue but when you said you couldn't ping googles IP address that steered me away from that. ANyway, glad you got it working. 

Mark it as solved.

---

### Post by jdthood on 2012-11-04
> **4rings said:**
> I added that dns-nameserver entry into the interfaces file while I was at it.

Just to prevent anyone getting confused... the name of the option is "dns-nameservers" with an 's' on the end. Spelled without the 's' it won't work (i.e., the listed nameserver addresses won't be added to resolv.cof) and you won't be warned about this either.

---

