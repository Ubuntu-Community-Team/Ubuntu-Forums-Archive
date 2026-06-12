---
title: "Problems since last upgrade"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by bigtel on 2008-06-15
Since the last upgrade my PC went through last week, my network adapter and USB mouse has stopped working. The only way I can use my Ubuntu now is to revert to a previous version (19 I think) through the GRUB start menu.

Any ideas how I can get around this?

I am unsure how to look for and install drivers (that I am sure were once there..!)

Thanks

PS The 'Wired Connection' option has also gone from the network settings options..

---

### Post by chili555 on 2008-06-16
Please post:```
sudo lshw -C network
iwconfig
ifconfig
```Thanks.

---

### Post by bigtel on 2008-06-16
Here we go then...

This is the output when I boot up using Ubuntu 8.04.1 kernel 2.6.24-19 - **virtual**

terry@terry-laptop:~$ sud lshw -C network
bash: sud: command not found
terry@terry-laptop:~$ sudo lshw -C network
[sudo] password for terry: 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       version: 51
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=16 maxlatency=8 mingnt=3
terry@terry-laptop:~$ iwconfig
lo        no wireless extensions.

terry@terry-laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4618 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4618 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:234814 (229.3 KB)  TX bytes:234814 (229.3 KB)


And this is the output when I boot up using  Ubuntu 8.04.1 kernel 2.6.24-19 - **generic**

terry@terry-laptop:~$ sudo lshw -C network
[sudo] password for terry: 
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 51
       serial: 00:c0:9f:11:d1:5e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.0.2 latency=16 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s

terry@terry-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

terry@terry-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:11:d1:5e  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe11:d15e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2901 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2143 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2571267 (2.4 MB)  TX bytes:361280 (352.8 KB)
          Interrupt:11 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7239 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7239 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:365866 (357.2 KB)  TX bytes:365866 (357.2 KB)

terry@terry-laptop:~$ 


I hope you can obtain some info from this lot..!!!!!

---

### Post by bigtel on 2008-06-16
...should say that's it's the **Virtual** boot up that does not work..

---

### Post by chili555 on 2008-06-17
And while you are booted in **Virtual**, what is the result of:```
sudo modprobe via-rhine
sudo ifup eth0
```Do you get an IP address? If so, we can probably make this permanent.

---

### Post by bigtel on 2008-06-17
Here is the output..

terry@terry-laptop:~$ sudo modprobe via-rhine
[sudo] password for terry: 
FATAL: Module via_rhine not found.
terry@terry-laptop:~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.
terry@terry-laptop:~$ 


I see no IP address here. What is the difference between the Generic and Virtual boot up sequence?

I have noticed something else as I have been rebooting. When I load the **Virtual** (does not work), I get no error messages. When I load the **Generic** (works OK) I get a message while loading hardware drivers - acer-acpi: no or unsupported WMI interface

I am not sure if this is related at all to the problem..??

---

### Post by chili555 on 2008-06-17
Upon further investigation, I have found that the driver as been omitted in x-19, but was present in x-17 and x-18. I have not yet determined if it's an error or intentional. I am looking and will report.

---

### Post by bigtel on 2008-06-17
OK great, thanks for your help on this one.

Could I install the 'missing' driver manually to fix this problem?

---

### Post by chili555 on 2008-06-17
> I have found that the driver as been omitted in x-19Well, scratch all that; I made a rookie mistake. Hello, gravel-trap!> FATAL: Module via_rhine not found.This is funny. Please do:```
sudo updatedb
locate rhine | grep .ko
```*updatedb* will take a few moments; be patient. Let's see what is there in Virtual...or not.

---

### Post by bigtel on 2008-06-18
Here is the output...

terry@terry-laptop:~$ sudo updatedb
[sudo] password for terry: 
terry@terry-laptop:~$ locate rhine | grep .ko
/lib/modules/2.6.22-14-generic/kernel/drivers/net/via-rhine.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/net/via-rhine.ko
/lib/modules/2.6.24-17-generic/kernel/drivers/net/via-rhine.ko
/lib/modules/2.6.24-18-generic/kernel/drivers/net/via-rhine.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/net/via-rhine.ko
terry@terry-laptop:~$

---

### Post by chili555 on 2008-06-18
> FATAL: Module via_rhine not found.That's weird, because there it is, right before our eyes:> /lib/modules/2.6.24-19-generic/kernel/drivers/net/via-rhine.koLet's see if we can modprobe this with the absolute path:```
sudo modprobe /lib/modules/2.6.24-19-generic/kernel/drivers/net/via-rhine.ko
```If this is successful, then go on to:```
sudo ifconfig eth0 up
sudo dhclient eth0
```Post back and let us know.

---

### Post by bigtel on 2008-06-18
Output as follows...


terry@terry-laptop:~$ sudo modprobe /lib/modules/2.6.24-19-generic/kernel/drivers/net/via-rhine.ko
[sudo] password for terry: 
FATAL: Module /lib/modules/2.6.24_19_generic/kernel/drivers/net/via_rhine.ko not found.
terry@terry-laptop:~$ sudo ifconfig eth0 up
eth0: ERROR while getting interface flags: No such device
terry@terry-laptop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
terry@terry-laptop:~$

---

### Post by bigtel on 2008-06-18
..am I in the right directory within terminal whe entering these commands..?

I have manually looked in the directory using the file browser and I can see the via-rhine.ko file there..it is in the Generic directory, but NOT in the virtual directory.

---

### Post by bigtel on 2008-06-27
I still have had no joy with this. Are you still thinking about this one Chili555..?

---

