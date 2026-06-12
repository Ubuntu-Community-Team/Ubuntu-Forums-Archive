---
title: "Need help connecting to a wireless network"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by fuieru on 2008-08-14
Router is a 2wire Homeportal1000HW.
I'm using a linksys wireless card.
I have installed the ndisgtk thing and it insists that the driver for my wireless card, but I'm not picking up any networks whatsoever from the dropdown list in the network properties.
Any assistance would be much appreciated as I just installed linux for the first time.

---

### Post by maybeway36 on 2008-08-14
Is it encyrpted, and if so is it WEP, WPA, or WPA2?
I have WEP and like to bypass NetworkManager and put it in /etc/network/interfaces:
```
auto wlan0
iface wlan0 inet dhcp
wireless-essid [name]
wireless-key [hexadecimal key]
```

---

### Post by nicedude on 2008-08-15
If you installed Ndiswrapper you must also provide that with a Windows XP wifi driver that you get from the manufacturer of the device. Ndiswrapper is kinda what it says "a wrapper" that allows the windows driver to work in a linux machine in situations where Linux based drivers are either unavailable or are very difficult to make work and the person would rather just get it working simply & quickly. So did you also try to use Ndis to load a XP driver for the wifi adapter in question? Also youo could run the following command to let others here see what is going on, run these in a terminal and paste the output here ( to open a terminal go to top menubar Applications -> Accessories -> Terminal )

Here are the commands to paste one at a time and just press enter after each one

iwconfig

sudo lshw -C Network


Run those and post back. Also give your linksys wifi card model and I will see what drivers there are for it :-)

---

### Post by jualin on 2008-08-15
And also depending on your card you may need to disable any linux drivers that Ubuntu is loading by default. Go to the terminal and post the output of > lspci
lsusb so we can make sure your ndiswrapper installation was correct.

---

### Post by fuieru on 2008-08-16
Here are those outputs you guys asked for.
Lspci:


00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:05.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

lsusb:
Bus 004 Device 006: ID 08ec:0008 M-Systems Flash Disk Pioneers 

lsusb:

Bus 004 Device 004: ID 04b8:0819 Seiko Epson Corp. 
Bus 004 Device 002: ID 13b1:000d Linksys 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 413c:3010 Dell Computer Corp. Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


iwconfig:


lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"2wire853"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


sudo lshw -C Network:

  *-network DISABLED      
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:58:26:01
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 latency=64 link=no module=ssb multicast=yes port=twisted pair
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:12:17:76:66:81
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

also my network is encripted and i'm fairly sure its in hex. how would i double check? the key is 1502811166 if that helps.

the model is a linksys wireless-g 2.4 ghz WUSB546 ver 4.

---

### Post by jualin on 2008-08-16
You need to locate the Windows driver for your wireless card to use it with Ndiswrapper on Linux. I found your card on the [Ndiswrapper Card List]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/") but the link is not working. Your card uses the device ID "13b1:000d" so just search the link with that. If the card came with a CD then you may use that driver. You can follow the turorial on my signature when you get the driver.

---

