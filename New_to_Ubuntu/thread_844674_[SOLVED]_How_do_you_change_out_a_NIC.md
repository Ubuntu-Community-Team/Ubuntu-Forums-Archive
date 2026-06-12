---
title: "[SOLVED] How do you change out a NIC"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by SteveNorman on 2008-06-29
I am trying to switch from an old wired lan card to a new intel pro/1000 gt (865080). I thought I could just take the old out, put the new in/ reboot and get online, but this is not the case. It launched intel boot agent first then goes to grub. I dont know if this matters or not.

I cant seem to find any info on how to fix this and am wondering If I am the only person to have this problem:-({|=

any help would be greatly appreciated. 

BTW I am using my old lan card again with no problems,,both are PCI, and it doesnt load in XP either (I dual boot). With XP I know I have to load a driver via DOS,,but from what I have read everyone seems to be able to get this card to work out of the box in ubuntu.

---

### Post by Xerp on 2008-06-29
Yes, normally you just take out the old card and put the new one in! So what actually happens? Does it get past grub and boot into Ubuntu, or hang?

---

### Post by kattman on 2008-06-29
Might be worth to Clear the computer Bios, and see if will detect the new card

---

### Post by SteveNorman on 2008-06-29
It boots into  ubunutu after it does this for awhile (20sec?):
DHCP............/   where / is turning


Not sure how you clear bios,,I have american mega trends


ifconfig with the intel card in gives:

```

eth1      Link encap:Ethernet  HWaddr 00:19:21:28:a6:82  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xdead 

eth2      Link encap:Ethernet  HWaddr 00:1b:21:1c:e0:f7  
          inet6 addr: fe80::21b:21ff:fe1c:e0f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3582 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:233864 (228.3 KB)  TX bytes:10071 (9.8 KB)
          Base address:0xbc00 Memory:f9fc0000-f9fe0000 

eth2:avahi Link encap:Ethernet  HWaddr 00:1b:21:1c:e0:f7  
          inet addr:169.254.9.5  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Base address:0xbc00 Memory:f9fc0000-f9fe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1076 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1076 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:55035 (53.7 KB)  TX bytes:55035 (53.7 KB)
```

lscpi with the card in gives:
```


00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:08.0 Multimedia audio controller: Creative Labs SB Audigy LS
00:09.0 Ethernet controller: Intel Corporation 82541PI Gigabit Ethernet Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)
```

---

### Post by neurostu on 2008-06-29
If you can get ubuntu to boot, open a terminal and type:
```

lspci

```
then paste the results below!

---

### Post by SteveNorman on 2008-06-29
read your mind Neurostu,,lol,it in the above post.

---

### Post by SteveNorman on 2008-06-30
It sees the card,,it just doesnt let me online. I tried manually configuring to no avail. Now it looks up on firebug then eventually lets me in.

---

### Post by Xerp on 2008-06-30
Cool, so Ubuntu sees your two gigabit NICs - they just need assigning some info. Do you use static IPs or are they assigned by a DHCP server?

---

### Post by SteveNorman on 2008-06-30
It says "enabled roaming mode" and is checked.

Here is ifconfig for my old card (one in now that works:
```
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:b5:83:18:42  
          inet addr:67.160.44.146  Bcast:255.255.255.255  Mask:255.255.252.0
          inet6 addr: fe80::210:b5ff:fe83:1842/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:750 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:52869 (51.6 KB)  TX bytes:12434 (12.1 KB)
          Interrupt:20 Base address:0xc400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1082 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1082 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:45466 (44.4 KB)  TX bytes:45466 (44.4 KB)

```

---

### Post by Xerp on 2008-06-30
Nice, so we have half the info there. Interesting IP address though - thats a "real" one. I'd expect to see something 192.168.x.x or 10.x.x.x What is plugged into your NIC?

manual config like this:

```
sudo ifconfig eth2 67.160.44.146 netmask 255.255.252.0
```

would set the NIC info, you'd then need the output from

```
netstat -rn
``` to see the old default route (with the old eth0 working), then

```
sudo route add default gateway ip.address.from.netstat
```

But all that is a little beside the point as your DHCP should be working :) ... The old eth0 is set to roaming too, yes?

---

### Post by SteveNorman on 2008-06-30
Oops sorry,,I think I confused you with my last post,,,I only have one working unit,,the old NIC running comcast high speed. I have to take it out of the motherboard and insert the new one (Intel that I cant get to work) in its place.

The roaming thing doesnt seem to work for the new card,,only for this old one that is in the slot now. So my old working nic is the only nic set for roaming. 

eth0 is my old working nic
eth1 and eth2 refer to my on-board (not working) and my new (notworking intel) nics, tho I am not sure which is which. I disabled my onboard in bios so when I try the new card again that should be the only one listed.

I will wait for a reply to make sure we are on the same page then.I will plug in my new one and try your commands and post the results.

---

### Post by SteveNorman on 2008-06-30
oh,,btw I did ipconfig in xp with my old card and got the gateway as 67.160.44.1,, would that be the same for ubuntu? seems like it would....
with the working nic (eth0):
```
~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
67.160.44.0     0.0.0.0         255.255.252.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         67.160.44.1     0.0.0.0         UG        0 0          0 eth0

```

---

### Post by ispyisail on 2008-07-01
This is a post i made awhile ago.


I've just upgraded to ubuntu server 8.04 LTS and all was well untill i decided to upgarde my NIC.

After replacing my network card there was no networking anymore.

I put the old card back in and the network worked again.

After much research i found the solution:

[https://bugs.launchpad.net/ubuntu/+bug/214789](https://bugs.launchpad.net/ubuntu/+bug/214789)

> Quote:
There is /etc/udev/rules.d/70-persistent-net.rules which lists the old MAC as eth0 and prevents the new card from becoming eth0.

There is /etc/network interfaces that lists all the eth intefaces generated so far (up to eth1) as "iface ethx inet dhcp".
Basically when ubuntu is installed it creates a link between the NIC MAC address and eth(x) and when a new NIC is installed the MAC address is associated with the next free eth(x) so eth0 (first card) now becomes eth1 (new card)

If you want the new card to become eth0 you need to edit /etc/udev/rules.d/70-persistent-net.rules Delete all the old rules then reboot.
```

nano -w /etc/udev/rules.d/70-persistent-net.rules
```

Hopefully this post will save somebody some time.

---

### Post by SteveNorman on 2008-07-01
That looks like it,,Ill try it in the morning and post the results.

So My old card is still listed as eth0 now,, and I want my new card to be eth0 not eth1 or eth2 right?

Ill make a backup of that file and try it out tomorrow,,thanks!

---

### Post by ispyisail on 2008-07-01
You are correct

Ubuntu records the MAC address of the NIC and logs it with a port e.g eth0

For every new NIC added to your machine it counts up e.g
eth1
eth2
eth3
..

I spent hours finding the solution to the very same problem.

Its actually quite usefull once you know about it.

---

### Post by SteveNorman on 2008-07-01
so this is my /etc/udev/rules.d/70-persistent-net.rules now...

```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x1113:0x1211 (8139too)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:10:b5:83:18:42", ATTR{type}=="1", NAME="eth0"

# PCI device 0x1039:0x0191 (sis190)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:19:21:28:a6:82", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x8086:0x107c (e1000)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1b:21:1c:e0:f7", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"
```

And this is what I want?:

```

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.



# PCI device 0x8086:0x107c (e1000)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1b:21:1c:e0:f7", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
```

---

### Post by punkybouy on 2008-07-02
Everything is fine.  That card has the ability to let you boot the computer remotely and that is why it boots the way it does.  It may have its own bios setting you can disable.

---

### Post by SteveNorman on 2008-07-03
I cant get it to work in an xp machine either,,I think I have a bad card. Gonna replace it and will post the results.

---

### Post by ispyisail on 2008-07-03
> **SteveNorman said:**
> so this is my /etc/udev/rules.d/70-persistent-net.rules now...

```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x1113:0x1211 (8139too)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:10:b5:83:18:42", ATTR{type}=="1", NAME="eth0"

# PCI device 0x1039:0x0191 (sis190)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:19:21:28:a6:82", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x8086:0x107c (e1000)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1b:21:1c:e0:f7", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"
```

And this is what I want?:

```

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.



# PCI device 0x8086:0x107c (e1000)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1b:21:1c:e0:f7", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
```

Correct

I've found if you delete the entire contents of the file then reboot it will rebuild the file for you starting at eth0

---

### Post by SteveNorman on 2008-07-09
so heres the summary in case it will help someone else.


had a bad NIC (the INTEL)

so I bought a new d-link DGE-530T pci.

plugged it in,,the kernal saw it but still no connection.
Tried a different twisted cable from an old router (cat 5).
Nothing,,,no what,,conky showed a crawl,,nothing.

took everything out,,unplugged the cable modem,,all the wires everything.
put it all back together carefully,,bam online:guitar: There was a loose connection somewhere. A series of bad coincidences, loose cable + bad NIC = headache.](*,)

 But so you know the D-link adapter seems to work out of the box. I sure learned a lot about NICS,,,lol

Thank you all for helping.

---

