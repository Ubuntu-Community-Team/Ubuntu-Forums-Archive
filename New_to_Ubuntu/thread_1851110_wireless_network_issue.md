---
title: "wireless network issue"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by aam-aadmi on 2011-09-27
Hi All,

I am running Ubuntu 10.04 on a Dell Latitude E5510. I am having the following wireless issue: I am unable to access the wireless network at home. But I am able to access the wireless network at office.

I am also able to access the home network on another windows machine.

Any suggestions on how to deal with this issue?

Here is the output for ifconfig

[HTML]eth0      Link encap:Ethernet  HWaddr f0:4d:a2:9e:38:91  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr c0:cb:38:2c:8f:73  
          inet addr:128.119.195.203  Bcast:128.119.195.255  Mask:255.255.254.0
          inet6 addr: fe80::c2cb:38ff:fe2c:8f73/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32463 errors:1 dropped:0 overruns:0 frame:46729
          TX packets:12652 errors:12 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14175377 (14.1 MB)  TX bytes:7211169 (7.2 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:146 errors:0 dropped:0 overruns:0 frame:0
          TX packets:146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15961 (15.9 KB)  TX bytes:15961 (15.9 KB)

[/HTML] 

And here is the output for iwconfig
[HTML]lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:208  Noise level:167
          Rx invalid nwid:0  invalid crypt:66  invalid misc:0
[/HTML]

Here is the output for lspci

[HTML]00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: Broadcom Corporation Device 4353 (rev 01)
03:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 03)
03:00.4 FireWire (IEEE 1394): Ricoh Co Ltd Device e832 (rev 03)
0b:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5761e Gigabit Ethernet PCIe (rev 10)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
[/HTML]
Thanks.
Aam-aadmi

---

### Post by bkratz on 2011-09-27
Are you running a different encryption method at home vrs. office? Often network manager has some problems with wireless routers that are set to mixed mode (you know wpa and also wpa2). You should check both and try to use wpa2 only if possible.

---

