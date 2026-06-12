---
title: "bug ? wireless issue"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by trigsenior on 2008-08-04
Hello,

I recently updated my kernel too ( the one above 2.6.24-18-generic )
2.6.24-19-generic?. Well i can not connect to the internet ( but i can pick up wireless points). I have to boot to the older kernel version 2.6.24-18-generic. I ran ifconfig in the problem kernel. 

eth0      Link encap:Ethernet  HWaddr 00:1b:fc:5e:5d:d9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4994 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4994 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:256900 (250.8 KB)  TX bytes:256900 (250.8 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:ee:e0:e5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:351 (351.0 B)  TX bytes:5897 (5.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-C0-A8-EE-E0-E5-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)










and in the kernel which works 

eth0      Link encap:Ethernet  HWaddr 00:1b:fc:5e:5d:d9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4210 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:210500 (205.5 KB)  TX bytes:210500 (205.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:ee:e0:e5  
          inet addr:192.168.1XXX  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:a8ff:feee:e0e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8905 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6390 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12368278 (11.7 MB)  TX bytes:671017 (655.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-C0-A8-EE-E0-E5-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


I am have issues my connection , This is my wireless usb thing not sure which one it is so i pasted everything 

lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:01.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
01:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)

hope you can help , thanxs

im using ubuntu hardy btw

---

### Post by alpage2 on 2008-08-04
This is not an unusual problem - when a new kernal is installed, the wireless metworking will need setting up again. If your wireless adapter is one of those that are supported 'out of the box', (which looks to be the case, judging from the output of ifconfig), your problem may just be that the wireless adapter needs configuring again for your wireless network - i.e. giving it the network name and setting up the encryption again, if you use encryption.

If you did this previously with the network manager, just repeat the same steps. It works for some, but I have always found it to be more reliable to set up at the command line, using iwconfig ;-)

If this does not solve your problem:

What model is your wireless adapter, and is it an internal pci card, or is it a usb device?

if usb, post here the output of the lsusb command.

And in either case, post the output of the iwconfig command.

Regards
Alan

---

