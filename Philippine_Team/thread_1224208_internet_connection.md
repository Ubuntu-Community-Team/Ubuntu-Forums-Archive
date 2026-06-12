---
title: "internet connection?"
date: 2009-07-27
forum: Philippine Team
---

### Post by ismoke101 on 2009-07-27
ei need some help dyan, na wiwindang na talaga ako e, may problema yung ubuntu 8.10 ko, na kaka ping ako pero hindi ko ma open yung firefox, open na to d point na talagang loading then mag hang nalang,. nag try ako ng lts tapos ganun padin, take note full disk installation a, tapos depres na ko bumalik sa linux kaya nag debian ako, sa badtrip e ganun padin, kaka fresh install ko ulet ng windows xp, na ngangati na ko dito sa xp, waaaaa mis ko na linux for almost a month, any help? may nakaencounter na ba ng ganito? tell me what to do, maya konte mag dual boot naman ako, hardy muna naun 
:confused:

---

### Post by jeffimperial on 2009-07-27
> **ismoke101 said:**
> ei need some help dyan, na wiwindang na talaga ako e, may problema yung ubuntu 8.10 ko, na kaka ping ako pero hindi ko ma open yung firefox, open na to d point na talagang loading then mag hang nalang,. nag try ako ng lts tapos ganun padin, take note full disk installation a, tapos depres na ko bumalik sa linux kaya nag debian ako, sa badtrip e ganun padin, kaka fresh install ko ulet ng windows xp, na ngangati na ko dito sa xp, waaaaa mis ko na linux for almost a month, any help? may nakaencounter na ba ng ganito? tell me what to do, maya konte mag dual boot naman ako, hardy muna naun 
:confused:
subukan mo po sa commandline:

```
firefox &
```

tapos tingnan natin kung anong makuha nyo.

---

### Post by loell on 2009-07-27
also, what ethernet are you using?

```
lspci | grep Ethernet
```

---

### Post by ismoke101 on 2009-07-27
**jeffimperial**

Eto yung mga network config ko baka makatulong, 
```
gksudo gedit /etc/dhcp3/dhclient.conf ko 
# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

send host-name "";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
timeout 30;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}]
```

```
chico@chico-desktop:~$ clear
chico@chico-desktop:~$ ping www.pingplotter.com -c 3
PING pingplotter.com (216.92.151.75) 56(84) bytes of data.
64 bytes from pingplotter.com (216.92.151.75): icmp_seq=1 ttl=56 time=266 ms
64 bytes from pingplotter.com (216.92.151.75): icmp_seq=2 ttl=56 time=281 ms
64 bytes from pingplotter.com (216.92.151.75): icmp_seq=3 ttl=56 time=258 ms

--- pingplotter.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 11317ms
rtt min/avg/max/mdev = 258.315/268.981/281.953/9.796 ms
chico@chico-desktop:~$ cat /etc/resolv.conf
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4952
#
### END INFO



nameserver 192.168.0.154
nameserver 192.168.0.154


chico@chico-desktop:~$ gksudo gedit /etc/dhcp3/dhclient.conf
chico@chico-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:c0:26:70:1e:02  
          inet addr:192.168.0.57  Bcast:192.168.5.255  Mask:255.255.254.0
          inet6 addr: fe80::2c0:26ff:fe70:1e02/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:386 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31589 (30.8 KB)  TX bytes:7925 (7.7 KB)
          Interrupt:16 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1464 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1464 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:73200 (71.4 KB)  TX bytes:73200 (71.4 KB)

chico@chico-desktop:~$ 

```
yung ***firefox &*** e nag hang na ko, tapos [1]5889 ata sa terminal hope this help

**loell** yun ba yung eth0?

---

### Post by ismoke101 on 2009-07-27
any idea po? khit sino:confused:

---

### Post by loell on 2009-07-27
err, hindi mo nabigay ang ethernet make and model mo. ;)
my guess, it could an MTU issue.

---

### Post by ismoke101 on 2009-07-27
yun ba yun? MTU? panu yun? i think automatic e, wait lang e, maya onti help me here ehehe

---

### Post by vidgen13 on 2009-07-27
pre try mo lng a d ko sure ung /etc/resolve.conf mo gawin mo

nameserver 4.2.2.2
nameserver 4.2.2.3

tapos restart mo connection.

---

### Post by ismoke101 on 2009-07-27
**loell**
kapag yung sa lspci | grep Ethernet e nag space lang sya wala namang lumalabas na iba e, tapos yung sa mtu pinalitan ko na pero kapag every restart ako bumabalik padin sya ng 1500, di talaga ata kaya pag ganun yung mtu, nag ping ako ganitong value sa windows kaso too large daw, 1492 ata dapat yung value, pero di ko mapalitan e, ginamet ko yung **sudo ifconfig eth0 mtu 1492** , ayaw mapalitan e, babalik padin sa 1500 value.


**vidgen13** 
na edit ko sya using **sudo nano** and sudo gedit kaso babalik padin sa original na value di kumakagat yung binigay mo na value 

sorry late reply, dito pa ko sa school nag net, e,

---

### Post by loell on 2009-07-27
ok, just post the whole output of lspci.

---

### Post by ismoke101 on 2009-07-28
**loell **
eto man

```
chico@chico-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
01:00.1 Display controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
chico@chico-desktop:~$ 
```

eto pa pala: 

nung try ko mag palit ng mtu dito [http://www.ubuntugeek.com/how-to-change-mtu-maximum-transmission-unit-of-network-interface-in-ubuntu-linux.html](http://www.ubuntugeek.com/how-to-change-mtu-maximum-transmission-unit-of-network-interface-in-ubuntu-linux.html) e ganito lang nakalagay sakin, walang eth0


[B]auto lo
iface lo inet loopback[/B]

pano man to ehehehe

---

### Post by loell on 2009-07-28
your rhino ethernet card seems to known not to work.
[http://ubuntuforums.org/showthread.php?p=7228859](http://ubuntuforums.org/showthread.php?p=7228859)

but you have another ethernet card,[B]RTL-8139/8139C/8139C+ (rev 10)
[/B] does this work?

you have a modem, by the way, you have not yet stated what your connection is.

---

### Post by ismoke101 on 2009-07-28
ethernet card?iis that my hardware device connected to the board? i have a cable broadband. and they just provide me with this Chinese router.

---

### Post by loell on 2009-07-28
> ethernet card?iis that my hardware device connected to the board?
yes,

may dalawa kang network card, yun yung connection sa pagitan ng pc mo at router mo, siguro ang ginamit mong network card ay yung rhino network card na parang hindi gumagana sa ubuntu, gamitin mo yung realtek network card.

---

### Post by ismoke101 on 2009-07-28
gumagana naman ata yung realtek 

chico@chico-desktop:~$ dmesg | grep -i duplex
[   78.678339] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  152.268246] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  154.780986] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1

got that from google, telling me na kailangan daw palitan yung 100mbps to 10, complicated, try ko naun gabe, nasa windows ako ngayun gumagana naman po realyek

---

### Post by ismoke101 on 2009-07-28
meron pa eto na lahat ehehehe:

```
chico@chico-desktop:~$ sudo lshw -C Network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 10
       serial: 00:c0:26:70:1e:02
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.57 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       version: 78
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=8 mingnt=3
chico@chico-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:c0:26:70:1e:02  
          inet addr:192.168.0.57  Bcast:192.168.5.255  Mask:255.255.254.0
          inet6 addr: fe80::2c0:26ff:fe70:1e02/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:712 errors:0 dropped:0 overruns:0 frame:0
          TX packets:311 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:77128 (75.3 KB)  TX bytes:66590 (65.0 KB)
          Interrupt:17 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:936 errors:0 dropped:0 overruns:0 frame:0
          TX packets:936 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:46800 (45.7 KB)  TX bytes:46800 (45.7 KB)

chico@chico-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:c0:26:70:1e:02  
          inet addr:192.168.0.57  Bcast:192.168.5.255  Mask:255.255.254.0
          inet6 addr: fe80::2c0:26ff:fe70:1e02/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:728 errors:0 dropped:0 overruns:0 frame:0
          TX packets:314 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:78328 (76.4 KB)  TX bytes:66822 (65.2 KB)
          Interrupt:17 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:936 errors:0 dropped:0 overruns:0 frame:0
          TX packets:936 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:46800 (45.7 KB)  TX bytes:46800 (45.7 KB)

chico@chico-desktop:~$ sudo lspci -nn | grep -i realtek
00:0a.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
chico@chico-desktop:~$ dmesg | grep -e via -e eth0
[   40.540107] eth0: RealTek RTL8139 at 0xd800, 00:c0:26:70:1e:02, IRQ 17
[   40.540111] eth0:  Identified 8139 chip type 'RTL-8139C'
[   40.711215] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   40.713830] via-rhine: probe of 0000:00:12.0 failed with error -5
[   40.723207] pata_via 0000:00:0f.1: version 0.3.3
[   40.734562] scsi0 : pata_via
[   40.745130] scsi1 : pata_via
[   41.909340] sata_via 0000:00:0f.0: version 2.3
[   41.909429] sata_via 0000:00:0f.0: routed to hard irq line 10
[   41.911621] scsi2 : sata_via
[   41.912510] scsi3 : sata_via
[   55.699397] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/via82xx.c:581: codec_read: codec 0 is not valid [0xfe0000]
[   55.707318] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/via82xx.c:581: codec_read: codec 0 is not valid [0xfe0000]
[   55.715286] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/via82xx.c:581: codec_read: codec 0 is not valid [0xfe0000]
[   55.723222] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/via82xx.c:581: codec_read: codec 0 is not valid [0xfe0000]
[   78.827231] eth0: link down
[  105.851679] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  257.817314] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  257.817702] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  258.026383] eth0: link down
[  260.330052] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  260.330452] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  277.589386] eth0: no IPv6 routers present
[  359.580700] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  379.073798] eth0: no IPv6 routers present
[  507.389461] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  523.748426] eth0: no IPv6 routers present
chico@chico-desktop:~$ 

```

---

### Post by loell on 2009-07-28
parang di tayo nagkakaintindihan, ang ibig ko sanang sabihin na gamitin yung isa pang network card ( realtek),  ay.. tanggalin mo yung connection sa likod tapos isaksak mo sa isa pang kahalintulad na saksakan. kasi nga,  dalawa yun, yung isa di gumagana sa ubuntu, hopefully yung pangalawa ay gagana.

---

### Post by ismoke101 on 2009-07-30
ginamet ko na kaso ayaw e, sabi parang sa windows yung wake on lan ang problema ng realtek, ewan, pinalitan ko na, yung rhine yung gamet ko dito sa windows, yung lan nung motherboard, sira na din yung realtek e, pati sa windows minsan di na gagana,. tanx nalang, lam mo ba kung panu enable yung lan ng motherboard sa linux/? pag ifconfig kasi e yung lo lang nag appear. :P:popcorn:

---

