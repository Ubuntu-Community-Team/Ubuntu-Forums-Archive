---
title: "unable to open drivers"
date: 2012-11-19
forum: New to Ubuntu
---

### Post by keithpitts on 2012-11-19
i have a usb radio interface attached to my laptop when  i start the software the only ports that show up are tty serial ports and not usb. the drivers are installed i can do a find command and the drivers are there but usb will not show up  under the port pull down menu in the software. do i need to do some thing to open the usb port.

Ubuntu 12.10
thanks
keith pitts

---

### Post by idoitprone on 2012-11-19
> **keithpitts said:**
> i have a usb radio interface attached to my laptop when  i start the software the only ports that show up are tty serial ports and not usb. the drivers are installed i can do a find command and the drivers are there but usb will not show up  under the port pull down menu in the software. do i need to do some thing to open the usb port.

Ubuntu 12.10
thanks
keith pitts
```

lsusb -t

lspci -nnk
```

---

### Post by bogan on 2012-11-19
Hi!, keithpitts,

What command are you using to display usb ports?

Edit: on my setup  the USB port shows as : > |__ Port 7: Dev 5, If 0, Class=stor., Driver=usb-storage, 480M

Please Post the output from: ```
 sudo lshw -C network
lsusb | grep -ie network
```Chao, bogan

---

### Post by keithpitts on 2012-11-19
this is what i get
keithpitts@ubuntu:~$ sudo lshw -C network
[sudo] password for keithpitts: 
  *-network               
       description: Wireless interface
       product: RTL8191SEvA Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: 1c:65:9d:3c:3f:21
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192se  driverversion=3.5.0-18-generic firmware=N/A ip=192.168.1.102 latency=0  link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 ioport:3000(size=256) memory:93500000-93503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 60:eb:69:3b:f2:a7
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes  port=MII speed=10Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:91410000-91410fff memory:91400000-9140ffff memory:91420000-9142ffff
i'm not using a PCI Card
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/rebrand/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/rebrand/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=12362819") 		 		  	 	 	 	 		  		 			 			[[IMG]http://ubuntuforums.org/images/rebrand/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=12362819")

---

### Post by mlentink on 2012-11-19
Where did you get the drivers? And could you please post the results of the commands idoitprone posted?

---

### Post by keithpitts on 2012-11-19
keithpitts@ubuntu:~$ lsusb -t
/:  Bus 08.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/8p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/4p, 480M
keithpitts@ubuntu:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:1484]
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:1484]
    Kernel driver in use: i915
    Kernel modules: i915
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:1484]
00:1a.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1484]
    Kernel driver in use: uhci_hcd
00:1a.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1484]
    Kernel driver in use: uhci_hcd
00:1a.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1484]
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1484]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1484]
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1484]
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1484]
    Kernel driver in use: uhci_hcd
00:1d.3 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1484]
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1484]
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1484]
    Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] [8086:2929] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1484]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1484]
    Kernel modules: i2c-i801
00:1f.6 Signal processing controller [1180]: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem [8086:2932] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1484]
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:1467]
    Kernel driver in use: rtl8192se
    Kernel modules: rtl8192se
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1484]
    Kernel driver in use: r8169
    Kernel modules: r8169

---

### Post by mlentink on 2012-11-19
> 02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171] (rev 10)

Is that the one you mean?

---

### Post by keithpitts on 2012-11-19
this is the link to the drivers
[http://www.westmountainradio.com/content.php?page=support](http://www.westmountainradio.com/content.php?page=support)
select the 
**RIGblaster Advantage**

 thanks
 keith pitts

---

### Post by idoitprone on 2012-11-19
it is the proper driver i believe

```
rfkill list all
```

post the result of this

---

### Post by mlentink on 2012-11-19
I am way out of my league here, as I don't even know what these things are. But from what I see these 'drivers' need to be compiled from source. Is this what you did?

---

### Post by keithpitts on 2012-11-19
the drivers were compiled

keithpitts@ubuntu:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
keithpitts@ubuntu:~$

---

### Post by idoitprone on 2012-11-19
```
ifconfig -a
```

it not soft block then see if there is wlan0

---

### Post by keithpitts on 2012-11-19
keithpitts@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 60:eb:69:3b:f2:a7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44478 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44478 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2600525 (2.6 MB)  TX bytes:2600525 (2.6 MB)

wlan0     Link encap:Ethernet  HWaddr 1c:65:9d:3c:3f:21  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e65:9dff:fe3c:3f21/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:181663 errors:0 dropped:0 overruns:0 frame:0
          TX packets:118440 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:236725803 (236.7 MB)  TX bytes:14377291 (14.3 MB)

keithpitts@ubuntu:~$

---

### Post by mlentink on 2012-11-19
According to the readmes you should have a /dev/ttyUSB* is that the case?

---

### Post by keithpitts on 2012-11-19
i do not have a /dev/ttyUSB*
keithpitts

---

### Post by idoitprone on 2012-11-19
i guess try this thread

[http://ubuntuforums.org/showthread.php?p=12261151&posted=1#post12261151](http://ubuntuforums.org/showthread.php?p=12261151&posted=1#post12261151)

realtek make bad linux drivers

---

### Post by keithpitts on 2012-11-20
I think some how we got off track. i have no problem with the wireless not working. the problem is that _ the USB ports do not show up in all the programs when you look under ports_.
thanks
keith pitts

---

### Post by mlentink on 2012-11-21
> **keithpitts said:**
> I think some how we got off track. i have no problem with the wireless not working. the problem is that _ the USB ports do not show up in all the programs when you look under ports_.
thanks
keith pitts

If I read those readmes correctly, the driver should present the USB-device to you as if it were a serial device. You should have e.g. a /dev/ttyUSB1. You don't, so obviously you will not see any devices. Since i haven't the foggiest idea what the equipment you're trying to connect is supposed to do I cannot help you with that. 
Maybe there's another HAM-radio fan in the forums?

---

### Post by keithpitts on 2012-11-21
i have /dev/ttys0 through ttys16 with nothing plugged in do i need  a usb device plugged in before ttyUSB0 will show up. plugged in or not i still don't have ttyUSB0
thanks
keith

---

### Post by wc5b on 2013-02-23
Keith, (or anyone)

Are you still having this problem? I am having the same issue tonight. 

Tom
WC5B

---

