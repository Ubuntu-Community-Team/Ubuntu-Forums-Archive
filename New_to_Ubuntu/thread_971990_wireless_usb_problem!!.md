---
title: "wireless usb problem!!"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by neu2buntu on 2008-11-05
hi ,and thanks for taking the time to look....

here my prob (only since 8.10 ibex) ..im on advent k4000 laptop and it has  built in wifi with poor signal most of the time, so i use external usb zydas dongle,..but when i try to connect to access point my internal wifi cuts in...   network manager in the top panel shows that they are both connected. in hardy i was able to choose between the two... is there a command or a way of shutting down internal card....:confused::confused::confused::confused::confused:](*,)

---

### Post by Peter09 on 2008-11-05
can you post the output of the terminal command

```
lshw -C network
```

this will give us an idea of whats connected.

Also the command

```
ifconfig
```

---

### Post by neu2buntu on 2008-11-05
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:03:0d:7b:02:1d
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan2
       serial: 00:02:72:6d:ef:48
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.2 multicast=yes wireless=IEEE 802.11bg
  *-network:1
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:10:60:94:fe:9d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.68 multicast=yes wireless=IEEE 802.11bg
  *-network:2 DISABLED
       description: Ethernet interface
       physical id: 4
       logical name: pan0
       serial: 6e:31:82:2e:94:ae
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by neu2buntu on 2008-11-05
eth0      Link encap:Ethernet  HWaddr 00:03:0d:7b:02:1d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1030 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1030 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70352 (70.3 KB)  TX bytes:70352 (70.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:10:60:94:fe:9d  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:60ff:fe94:fe9d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8346 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6339 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8019735 (8.0 MB)  TX bytes:1063058 (1.0 MB)

wlan2     Link encap:Ethernet  HWaddr 00:02:72:6d:ef:48  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::202:72ff:fe6d:ef48/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:569 errors:0 dropped:0 overruns:0 frame:0
          TX packets:948 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:339096 (339.0 KB)  TX bytes:205754 (205.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-02-72-6D-EF-48-66-34-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster1  Link encap:UNSPEC  HWaddr 00-10-60-94-FE-9D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Peter09 on 2008-11-05
From the IP addresses on these devices you appear to be connected to two different networks, is that correct?

---

### Post by neu2buntu on 2008-11-05
sorry for delay... wlan0 is my internal wifi and wlan2 is my external usb wifi:lolflag:

---

### Post by neu2buntu on 2008-11-05
yeah my usb keeps picking up my neighbours open a.p.   it just jumps to it whenever it cant connect to my own:p

---

### Post by Peter09 on 2008-11-05
My initial advice would be to not use your USB as the bars on the icon are not really accurate. Do you get drop outs with your internal device?

I'll look into disabling your internal device if you do not want to do the above.

---

### Post by Peter09 on 2008-11-05
The way to disable your internal card is to add the driver to the black list.

You need to put an entry in the file (see below) which has the name of your internal wifi driver

/etc/modprobe.d/blacklist file

---

### Post by neu2buntu on 2008-11-05
yeah i would rather use the usb...when i was using hardy it gave perfect performance and the internal wifi has always gave dropouts...i would really appreciate it if you would look into disabling the internal one...thanks

---

### Post by neu2buntu on 2008-11-05
have just got your msg there...i will try this and let you know how it went

---

### Post by neu2buntu on 2008-11-05
ok i think i might have the right driver.. will i need a restart or modprobe the driver

---

### Post by Peter09 on 2008-11-05
Think its best to reboot

---

### Post by neu2buntu on 2008-11-05
ok ...hopefully get back soon...and thanks once again for your time...i will post a thanks on your profile too

---

### Post by FreewheelinFrank on 2008-11-05
I have a similar problem:

[http://ubuntuforums.org/showthread.php?t=966654](http://ubuntuforums.org/showthread.php?t=966654)

---

### Post by neu2buntu on 2008-11-05
thats me back on and it has worked a treat ....

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan2     IEEE 802.11bg  ESSID:"BTHomeHub-5CBF"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1D:68:AC:1B:F5   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=58/100  Signal level:23/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


no sign of it now ..happy days!    there are prob a few bugs not ironed out yet in inteprid,,,like earlier i was messing with screen resolution and it crashed my top panel for some reason,.but thanks to the good old forums i got it restored to default...

---

### Post by Peter09 on 2008-11-05
Frank,
have you tried to blacklist your driver?

---

### Post by FreewheelinFrank on 2008-11-05
How do I find the driver name exactly?

---

### Post by Peter09 on 2008-11-05
Great Chrissy, 
happy Ubuntuing - see you around the forums

---

### Post by Peter09 on 2008-11-05
Frank,
do the same as I ask Chrissy, post the output of lshw -C network

---

### Post by FreewheelinFrank on 2008-11-05
This seems to be the internal WiFi card:

```
    description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:7e:28:39
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
```

---

### Post by Peter09 on 2008-11-05
Frank,
your driver is iwl3945

You need to put that text in the blacklist file.

---

### Post by FreewheelinFrank on 2008-11-05
Cheers!

I'll give it a go.

---

### Post by FreewheelinFrank on 2008-11-05
After a reboot, my internal card does not appear, so as a work-around, this seems to be fine, but should Network Manager really be trying to connect via internal card and USB at the same time?

Thanks for the help.

---

### Post by Peter09 on 2008-11-05
Hi Frank,
not sure of your response - did it fix it?

Many Computers have multiple network cards which attach to different networks - so I guess it is valid for this to happen.

---

### Post by FreewheelinFrank on 2008-11-05
Yes, the internal card is not visible in Network Manager now, so the conflict can't arise.

At the moment the default seems to be for both the internal Wi-fi card and any USB receiver to attempt to connect to the same router, leading to neither connecting correctly. 

It would be nice to have Network Manager avoid this situation on its own, or at least give the user the chance to decide which connection to use.

---

