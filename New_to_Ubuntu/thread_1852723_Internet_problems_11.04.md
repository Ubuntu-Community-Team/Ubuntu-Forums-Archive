---
title: "Internet problems 11.04"
date: 2011-09-30
forum: New to Ubuntu
---

### Post by queendeagle on 2011-09-30
user@home:~$ sudo lshw -C network
[sudo] password for user: 
  *-network               
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c1
       serial: 00:26:6c:5a:f8:f8
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:d5400000-d543ffff ioport:3000(size=128)
  *-network
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: 70:f1:a1:9e:2b:9d
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0017.0507.2010 firmware=63 ip=192.168.1.64 latency=0 link=yes multicast=yes wireless=802.11bgn
       resources: irq:17 ioport:2000(size=256) memory:d4400000-d4403fff
[/quote]

---

### Post by queendeagle on 2011-09-30
Sorry about that - I tried to copy and paste in the whole lot but it's taken me half an hour and I can't get the rest of the data in, either via a reply or by editing.

My issue is that the wireless keeps sleeping. Please help, it's getting to the point where I'm going to have to restore my windows image.

My computer was dual boot with win7 and I started having these problems on Monday. Windows was working fine. In the end I decided to reinstall ubuntu thinking that I'd done something that messed it up. At the same time I decided to delete my windows partitions, so I can't even boot into windows to get the stuff on here, although I do have images of windows as a last resort.

In order to give you the output of the other commands, I'll have to put it in separate posts as I've only got a small window of opportunity to post it on here and I'm realising that there's just too much text to be able to upload it.

---

### Post by queendeagle on 2011-09-30
lspci
> 00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)


---

### Post by queendeagle on 2011-09-30
iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  ESSID:"O2wirelessF5DFFB"  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:26:44:F5:DF:FB   
          Bit Rate=135 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management period:0us  mode:All packets received
          Link Quality=83/100  Signal level=-58 dBm  Noise level=-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


---

### Post by grahammechanical on 2011-09-30
Did you notice this?

> Link Quality=83/100 Signal level=-58 dBm Noise level=-111 dBm

Now compare that with the iwconfig from my machine

> Link Quality=70/70  Signal level=-35 dBm

Compare link qualities and note the fact that you have a noise level which I do not. Is 111dBm excessive? I do not know. As a guess I would say that may be there are nearby wireless access points/routers that are using the same frequency as your router and this could be causing the connection to drop. If this is correct that you need to change the frequency channel of the router.

Others on this forum might give you better advice.

Regards.

---

### Post by queendeagle on 2011-10-01
Thanks. I finally managed to get it sorted. I realised that if I pinged my router indefinitely, it would stop the wireless from sleeping and give me enough of an internet connection to search properly.

It seems my wireless card isn't well supported and I'm guessing it was a kernal update that caused problems with the driver. I found another topic on here that went to 17 pages (it's that much of a problem!) and downloading the driver from realtek and installing it worked. Thanks.

---

