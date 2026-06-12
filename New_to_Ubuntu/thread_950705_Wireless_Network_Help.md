---
title: "Wireless Network Help"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by locbart5 on 2008-10-17
I just installed Hardy Heron earlier this week and need some help connecting to my wireless network. I am using a Dell Inspiron 8200 with an internal Mini PCI card made by Broadcom (802.11b, Truemobile 1180 for Dell). I am dual booting Ubuntu 8.04 with XP SP2. My wireless access point is a Lynksys router - I currently have it set up visible to anyone and unsecured to make it easy to set up the new connection. The other laptops in the house are able to connect to the network, as does this laptop when it is running XP.

When I start up in Ubuntu, it does not detect a wireless network (under the Wireless Network icon, no networks are listed). I have enabled roaming, and it still does not detect it.  When I manually configure it by typing in the network ID, password and selecting automatically assigning (DHCP), it still is not able to connect. Another odd thing is that after about the third time I 'use' the Network Icon in the upper right, it goes away.

After reading the online help files, and some threads on this forum I ran 'iwlist scan', 'lshw - C network', 'lspci', and 'iwconfig' - hoping to be able to find out if wireless card drivers are installed, wireless card is turned on, and if it is able to see the network.  Unfortunately, I don't know enough to answer any of these questions based on the command output. The output is listed below. I'm hoping someone can steer me towards the solution.

Thanks

will@will-laptop:~$ sudo iwlist scan
[sudo] password for will: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down


will@will-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go] (rev a3)
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:01.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller
02:03.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)


will@will-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 78
       serial: 00:0b:db:13:42:b3
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=32 link=no maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:b0:bb:4b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b


will@will-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11b  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by ezramorris on 2008-10-17
Did you try System>Administration>Hardware Drivers? You may also want to run sudo apt-get update before this, because a new wireless driver came into the repos the other day.

---

### Post by locbart5 on 2008-10-17
Under Hardware Drivers, the only unsupported hardware listed is my Nvidea 3D graphics card. I just ran the update from the quick launch bar, as well as the sudo you posted - no change to wireless status.

I should note that I am able to connect to the wireless router via an ethernet cable and am connected that way now.

Thanks

---

### Post by ezramorris on 2008-10-17
> **locbart5 said:**
> Under Hardware Drivers, the only unsupported hardware listed is my Nvidea 3D graphics card. I just ran the update from the quick launch bar, as well as the sudo you posted - no change to wireless status.

I should note that I am able to connect to the wireless router via an ethernet cable and am connected that way now.

Thanks

You may want to have a look at [this page]("http://web.archive.org/web/20070218180140/http://doc.gwos.org/index.php/BroadcomWireless"). It is for older versions of Ubuntu, but may still work.

---

