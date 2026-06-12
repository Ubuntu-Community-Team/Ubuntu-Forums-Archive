---
title: "Ethernet Internet Works in Try Ubuntu 14.04.1 but not after Installing"
date: 2015-02-07
forum: New to Ubuntu
---

### Post by bryant3 on 2015-02-07
I am now using the Ubuntu 14.04.1 "Try Ubuntu", the Ethernet connection to go on the internet works great, as you can see.  However, when I boot up the installed version, no Ethernet, no Wireless.  Is there a way to get the correct info over to the installed version so it works?

---

### Post by sandyd on 2015-02-07
> **bryant3 said:**
> I am no using the Ubuntu 14.04.1 "Try Ubuntu", the Ethernet connection to go on the internet works great, as you can see.  However, when I boot up the installed version, no Ethernet, no Wireless.  Is there a way to get the information the correct info over to the installed version so it works?

Hi, and welcome to Ubuntu Forums :)

Can you run the following commands, and post the file "hwinfo.txt" that is in your home folder (I placed the output into this file for convenience so that you can copy it onto a USB drive)

This will allow us to diagnose your issue further.

```

lspci > ~/hwinfo.txt
lsusb >> ~/hwinfo.txt
lshw -C network >> ~/hwinfo.txt
```

Thanks!

---

### Post by bryant3 on 2015-02-07
When I put these commands in the terminal, in the "Try Ubunto" mode:

lspci > ~/hwinfo.txt
lsusb >> ~/hwinfo.txt
lshw -C network >> ~/hwinfo.txt

I get the following:

Warning:  You should run this program as a super-user.
Warning:  Output may be incomplete or inaccurate, you should run this program as a super-user.

I entered these commands in the installed version to get the information you request:

   00:00.0 Host bridge: Intel Corporation Mobile
PM965/GM965/GL960 Memory Controller Hub (rev 0c) 00:01.0 PCI bridge: Intel Corporation Mobile
PM965/GM965/GL960 PCI Express Root Port (rev 0c) 00:1a.0 USB controller: Intel Corporation 82801H
(ICH8 Family) USB UHCI Controller #4 (rev 02) 00:1a.1 USB controller: Intel Corporation 82801H
(ICH8 Family) USB UHCI Controller #5 (rev 02) 00:1a.7 USB controller: Intel Corporation 82801H
(ICH8 Family) USB2 EHCI Controller #2 (rev 02) 00:1b.0 Audio device: Intel Corporation 82801H
(ICH8 Family) HD Audio Controller (rev 02) 00:1c.0 PCI bridge: Intel Corporation 82801H
(ICH8 Family) PCI Express Port 1 (rev 02) 00:1c.1 PCI bridge: Intel Corporation 82801H
(ICH8 Family) PCI Express Port 2 (rev 02) 00:1c.3 PCI bridge: Intel Corporation 82801H
(ICH8 Family) PCI Express Port 4 (rev 02) 00:1d.0 USB controller: Intel Corporation 82801H
(ICH8 Family) USB UHCI Controller #1 (rev 02) 00:1d.1 USB controller: Intel Corporation 82801H
(ICH8 Family) USB UHCI Controller #2 (rev 02) 00:1d.2 USB controller: Intel Corporation 82801H
(ICH8 Family) USB UHCI Controller #3 (rev 02) 00:1d.7 USB controller: Intel Corporation 82801H
(ICH8 Family) USB2 EHCI Controller #1 (rev 02) 00:1e.0 PCI bridge: Intel Corporation 82801
Mobile PCI Bridge (rev f2) 00:1f.0 ISA bridge: Intel Corporation 82801HM
(ICH8M) LPC Interface Controller (rev 02) 00:1f.1 IDE interface: Intel Corporation
82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02) 00:1f.2 IDE interface: Intel Corporation
82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [IDE mode] (rev 02) 00:1f.3 SMBus: Intel Corporation 82801H (ICH8
Family) SMBus Controller (rev 02) 01:00.0 VGA compatible controller: NVIDIA
Corporation G84M [GeForce 8600M GT] (rev a1) 03:00.0 Ethernet controller: Broadcom
Corporation BCM4401-B0 100Base-TX (rev 02) 03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd
R5C832 IEEE 1394 Controller (rev 05) 03:01.1 SD Host controller: Ricoh Co Ltd R5C822
SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) 03:01.2 System peripheral: Ricoh Co Ltd R5C592
Memory Stick Bus Host Adapter (rev 12) 03:01.3 System peripheral: Ricoh Co Ltd
xD-Picture Card Controller (rev 12) 0c:00.0 Network controller: Broadcom Corporation
BCM4311 802.11a/b/g (rev 01) Bus 002 Device 002: ID 05a9:2640 OmniVision
Technologies, Inc. OV2640 Webcam Bus 002 Device 001: ID 1d6b:0002 Linux
Foundation 2.0 root hub Bus 007 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hub Bus 006 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hub Bus 005 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hub Bus 001 Device 001: ID 1d6b:0002 Linux
Foundation 2.0 root hub Bus 004 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hub Bus 003 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hub   *-network        description: Network controller        product: BCM4311 802.11a/b/g        vendor: Broadcom Corporation        physical id: 0        bus info: pci@0000:0c:00.0        version: 01        width: 32 bits        clock: 33MHz        capabilities: bus_master cap_list        configuration: driver=wl latency=0        resources: irq:17
memory:f9ffc000-f9ffffff   *-network UNCLAIMED        description: Ethernet controller        product: BCM4401-B0 100Base-TX        vendor: Broadcom Corporation        physical id: 0        bus info: pci@0000:03:00.0        version: 02        width: 32 bits        clock: 33MHz        capabilities: bus_master cap_list        configuration: latency=64        resources: memory:f9bfe000-f9bfffff

---

### Post by sandyd on 2015-02-07
Lets take a look...

Wireless card is BCM4311 802.11a/b/g

Can be made to work with
```

sudo apt-get install firmware-b43-installer
```

However, you need some kind of internet to actually install that so lets take a look at getting internet through your ethernet first.

Your ethernet is BCM4401-B0.

This sounds like a blacklisting problem in a bug, mainly [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1113779](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1113779)

Can you post the output of
```
ls -l /etc/modprobe.d/

```

---

### Post by bryant3 on 2015-02-07
ls -l /etc/modprobe.d/  

 total 56  
 -rw-r--r-- 1 root root 2507 Feb 13  2013 alsa-base.conf  

 -rw-r--r-- 1 root root  325 Apr 10  2014 blacklist-ath_pci.conf  
 -rw-r--r-- 1 root root  347 Feb  5 18:37 blacklist-bcm43.conf  
 -rw-r--r-- 1 root root 1603 Apr 10  2014 blacklist.conf  
 -rw-r--r-- 1 root root  210 Apr 10  2014 blacklist-firewire.conf  
 -rw-r--r-- 1 root root  677 Apr 10  2014 blacklist-framebuffer.conf  
 -rw-r--r-- 1 root root  156 Feb 13  2013 blacklist-modem.conf  
 lrwxrwxrwx 1 root root   41 Feb  5 17:37 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf  
 -rw-r--r-- 1 root root  583 Apr 10  2014 blacklist-rare-network.conf  
 -rw-r--r-- 1 root root 1077 Apr 10  2014 blacklist-watchdog.conf  
 -rw-r--r-- 1 root root  127 Jan 15  2014 dkms.conf  
 -rw-r--r-- 1 root root  456 Apr 14  2014 fbdev-blacklist.conf  
 -rw-r--r-- 1 root root  347 Apr 10  2014 iwlwifi.conf  
 -rw-r--r-- 1 root root  104 Apr 10  2014 mlx4.conf  
 -rw-r--r-- 1 root root   30 Apr 10  2014 vmwgfx-fbdev.conf  

Thanks,
Bryant

---

### Post by sandyd on 2015-02-07
> **bryant3 said:**
> ls -l /etc/modprobe.d/  

 total 56  
 -rw-r--r-- 1 root root 2507 Feb 13  2013 alsa-base.conf  

 -rw-r--r-- 1 root root  325 Apr 10  2014 blacklist-ath_pci.conf  
 -rw-r--r-- 1 root root  347 Feb  5 18:37 blacklist-bcm43.conf  
 -rw-r--r-- 1 root root 1603 Apr 10  2014 blacklist.conf  
 -rw-r--r-- 1 root root  210 Apr 10  2014 blacklist-firewire.conf  
 -rw-r--r-- 1 root root  677 Apr 10  2014 blacklist-framebuffer.conf  
 -rw-r--r-- 1 root root  156 Feb 13  2013 blacklist-modem.conf  
 lrwxrwxrwx 1 root root   41 Feb  5 17:37 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf  
 -rw-r--r-- 1 root root  583 Apr 10  2014 blacklist-rare-network.conf  
 -rw-r--r-- 1 root root 1077 Apr 10  2014 blacklist-watchdog.conf  
 -rw-r--r-- 1 root root  127 Jan 15  2014 dkms.conf  
 -rw-r--r-- 1 root root  456 Apr 14  2014 fbdev-blacklist.conf  
 -rw-r--r-- 1 root root  347 Apr 10  2014 iwlwifi.conf  
 -rw-r--r-- 1 root root  104 Apr 10  2014 mlx4.conf  
 -rw-r--r-- 1 root root   30 Apr 10  2014 vmwgfx-fbdev.conf  

Thanks,
Bryant
Looks like your affected by the bug.

Run the following, which will remove the blacklist file
```

sudo mkdir /etc/modprobe.d-disabled/
sudo mv /etc/modprobe.d/blacklist-bcm43.conf /etc/modprobe.d-disabled/

```

Do a reboot and see if ethernet is working again.

---

### Post by bryant3 on 2015-02-07
Thank you!  I am now working from the installed version.  Should I run 
sudo apt-get install firmware-b43-installer now? 

Also, there was a part of the installation which did not complete b/c the internet connection, couldn't download.  I believe it was flash, will 
that just happen automatically without the aid of mirror dust and fairies?

Thanks again for your help,
Bryant

---

### Post by sandyd on 2015-02-07
> **bryant3 said:**
> Thank you!  I am now working from the installed version.  Should I run 
sudo apt-get install firmware-b43-installer now? 

Also, there was a part of the installation which did not complete b/c the internet connection, couldn't download.  I believe it was flash, will 
that just happen automatically without the aid of mirror dust and fairies?

Thanks again for your help,
Bryant

In that case, lets make sure everything is updated before we install anything
```

sudo apt-get update
sudo apt-get upgrade
```

---

### Post by bryant3 on 2015-02-08
Ran update and upgrade.

---

### Post by sandyd on 2015-02-08
> **bryant3 said:**
> Ran update and upgrade.

Should now be fine to run```
sudo apt-get install firmware-b43-installer now
```

---

### Post by bryant3 on 2015-02-08
Thanks again.   The Wireless Card is being recognized, connects, but doesn't go on to the internet or the Windows network.

---

### Post by sandyd on 2015-02-08
Looks like it doesn't like the firmware in firmware-b43-installer

Lets try linux-firmware-nonfree.

Run
```

sudo apt-get remove --purge b43-fwcutter firmware-b43-installer
sudo apt-get install linux-firmware-nonfree
```

Do a reboot and see if it is better

---

### Post by bryant3 on 2015-02-09
This linux-firmware-nonfree doesn't get as far as the first.  After I firmware-b43-installer, I had to manually enter the router's ssid, password.  Maybe that just needed some more manual setting up.  Thanks

---

### Post by chili555 on 2015-02-09
Please hook up the ethernet and do:```
sudo apt-get purge bcmwl-kernel source
sudo apt-get install  --reinstall firmware-b43-installer
```Reboot and let us have your results.

---

### Post by bryant3 on 2015-02-10
Sorry for the delay...

First I ran these: sudo apt-get purge bcmwl-kernel source sudo apt-get install  --reinstall firmware-b43-installer Rebooted, the Wireless was not connected to, the icon for the wireless card was lit. 

I then ran: sudo apt-get remove --purge b43-fwcutter firmware-b43-installer sudo apt-get install firmware-b43-installer The WIFI network is now connected.  Here are the updated results of running these commands, hope they are the results you need:


lspci > ~/hwinfo.txt
lsusb >>
~/hwinfo.txt
lshw -C network >> ~/hwinfo.txt


hwinfor.txt file:   



00:00.0 Host bridge: Intel Corporation Mobile
PM965/GM965/GL960 Memory Controller Hub (rev 0c) 00:01.0 PCI bridge: Intel Corporation Mobile
PM965/GM965/GL960 PCI Express Root Port (rev 0c) 00:1a.0 USB controller: Intel Corporation 82801H
(ICH8 Family) USB UHCI Controller #4 (rev 02) 00:1a.1 USB controller: Intel Corporation 82801H
(ICH8 Family) USB UHCI Controller #5 (rev 02) 00:1a.7 USB controller: Intel Corporation 82801H
(ICH8 Family) USB2 EHCI Controller #2 (rev 02) 00:1b.0 Audio device: Intel Corporation 82801H
(ICH8 Family) HD Audio Controller (rev 02) 00:1c.0 PCI bridge: Intel Corporation 82801H
(ICH8 Family) PCI Express Port 1 (rev 02) 00:1c.1 PCI bridge: Intel Corporation 82801H
(ICH8 Family) PCI Express Port 2 (rev 02) 00:1c.3 PCI bridge: Intel Corporation 82801H
(ICH8 Family) PCI Express Port 4 (rev 02) 00:1d.0 USB controller: Intel Corporation 82801H
(ICH8 Family) USB UHCI Controller #1 (rev 02) 00:1d.1 USB controller: Intel Corporation 82801H
(ICH8 Family) USB UHCI Controller #2 (rev 02) 00:1d.2 USB controller: Intel Corporation 82801H
(ICH8 Family) USB UHCI Controller #3 (rev 02) 00:1d.7 USB controller: Intel Corporation 82801H
(ICH8 Family) USB2 EHCI Controller #1 (rev 02) 00:1e.0 PCI bridge: Intel Corporation 82801
Mobile PCI Bridge (rev f2) 00:1f.0 ISA bridge: Intel Corporation 82801HM
(ICH8M) LPC Interface Controller (rev 02) 00:1f.1 IDE interface: Intel Corporation
82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02) 00:1f.2 IDE interface: Intel Corporation
82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [IDE mode] (rev 02) 00:1f.3 SMBus: Intel Corporation 82801H (ICH8
Family) SMBus Controller (rev 02) 01:00.0 VGA compatible controller: NVIDIA
Corporation G84M [GeForce 8600M GT] (rev a1) 03:00.0 Ethernet controller: Broadcom
Corporation BCM4401-B0 100Base-TX (rev 02) 03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd
R5C832 IEEE 1394 Controller (rev 05) 03:01.1 SD Host controller: Ricoh Co Ltd R5C822
SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) 03:01.2 System peripheral: Ricoh Co Ltd R5C592
Memory Stick Bus Host Adapter (rev 12) 03:01.3 System peripheral: Ricoh Co Ltd
xD-Picture Card Controller (rev 12) 0c:00.0 Network controller: Broadcom Corporation
BCM4311 802.11a/b/g (rev 01) Bus 002 Device 002: ID 05a9:2640 OmniVision
Technologies, Inc. OV2640 Webcam Bus 002 Device 001: ID 1d6b:0002 Linux
Foundation 2.0 root hub Bus 007 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hub Bus 006 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hub Bus 005 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hub Bus 001 Device 001: ID 1d6b:0002 Linux
Foundation 2.0 root hub Bus 004 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hub Bus 003 Device 005: ID 0a5c:4503 Broadcom Corp.
Mouse (Boot Interface Subclass) Bus 003 Device 004: ID 0a5c:4502 Broadcom Corp.
Keyboard (Boot Interface Subclass) Bus 003 Device 003: ID 413c:8126 Dell Computer
Corp. Wireless 355 Bluetooth Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp.
BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth) Bus 003 Device 001: ID 1d6b:0001 Linux
Foundation 1.1 root hub   *-network        description: Network controller        product: BCM4311 802.11a/b/g        vendor: Broadcom Corporation        physical id: 0        bus info: pci@0000:0c:00.0        version: 01        width: 32 bits        clock: 33MHz        capabilities: bus_master cap_list        configuration: driver=b43-pci-bridge
latency=0        resources: irq:17
memory:f9ffc000-f9ffffff   *-network        description: Ethernet interface        product: BCM4401-B0 100Base-TX        vendor: Broadcom Corporation        physical id: 0        bus info: pci@0000:03:00.0        logical name: eth0        version: 02        serial: 00:1d:09:be:96:bd        size: 100Mbit/s        capacity: 100Mbit/s        width: 32 bits        clock: 33MHz        capabilities: bus_master cap_list
ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation        configuration: autonegotiation=on
broadcast=yes driver=b44 driverversion=2.0 duplex=full
ip=192.168.254.6 latency=64 link=yes multicast=yes port=twisted pair
speed=100Mbit/s        resources: irq:17
memory:f9bfe000-f9bfffff   *-network        description: Wireless interface        physical id: 1        logical name: wlan0        serial: 00:1f:3a:12:46:05        capabilities: ethernet physical wireless        configuration: broadcast=yes driver=b43
driverversion=3.13.0-45-generic firmware=666.2 ip=10.42.0.1 link=yes
multicast=yes wireless=IEEE 802.11bg   *-network        description: Network controller        product: BCM4311 802.11a/b/g        vendor: Broadcom Corporation        physical id: 0        bus info: pci@0000:0c:00.0        version: 01        width: 32 bits        clock: 33MHz        capabilities: bus_master cap_list        configuration: driver=b43-pci-bridge
latency=0        resources: irq:17
memory:f9ffc000-f9ffffff   *-network        description: Ethernet interface        product: BCM4401-B0 100Base-TX        vendor: Broadcom Corporation        physical id: 0        bus info: pci@0000:03:00.0        logical name: eth0        version: 02        serial: 00:1d:09:be:96:bd        size: 100Mbit/s        capacity: 100Mbit/s        width: 32 bits        clock: 33MHz        capabilities: bus_master cap_list
ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation        configuration: autonegotiation=on
broadcast=yes driver=b44 driverversion=2.0 duplex=full
ip=192.168.254.6 latency=64 link=yes multicast=yes port=twisted pair
speed=100Mbit/s        resources: irq:17
memory:f9bfe000-f9bfffff   *-network        description: Wireless interface        physical id: 1        logical name: wlan0        serial: 00:1f:3a:12:46:05        capabilities: ethernet physical wireless        configuration: broadcast=yes driver=b43
driverversion=3.13.0-45-generic firmware=666.2 ip=10.42.0.1 link=yes
multicast=yes wireless=IEEE 802.11bg 



Re-ran ls -l /etc/modprobe.d/: 

-rw-r--r-- 1 root root 2507 Feb 13  2013
alsa-base.conf
-rw-r--r-- 1 root root  325 Apr 10  2014
blacklist-ath_pci.conf
-rw-r--r-- 1 root root 1603 Apr 10  2014
blacklist.conf
-rw-r--r-- 1 root root  210 Apr 10  2014
blacklist-firewire.conf
-rw-r--r-- 1 root root  677 Apr 10  2014
blacklist-framebuffer.conf
-rw-r--r-- 1 root root  156 Feb 13  2013
blacklist-modem.conf
lrwxrwxrwx 1 root root   41 Feb  5 17:37
blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r-- 1 root root  583 Apr 10  2014
blacklist-rare-network.conf
-rw-r--r-- 1 root root 1077 Apr 10  2014
blacklist-watchdog.conf
-rw-r--r-- 1 root root  127 Jan 15  2014
dkms.conf
-rw-r--r-- 1 root root  456 Apr 14  2014
fbdev-blacklist.conf
-rw-r--r-- 1 root root  347 Apr 10  2014
iwlwifi.conf
-rw-r--r-- 1 root root  104 Apr 10  2014
mlx4.conf
-rw-r--r-- 1 root root   30 Apr 10  2014
vmwgfx-fbdev.conf


If information is power I hope I haven't
overloaded the circuits.

---

### Post by chili555 on 2015-02-10
> The WIFI network is now connected. We're glad it's working! Please use thread tools at the top to mark Solved.

---

### Post by bryant3 on 2015-02-10
Well it is connected, like it was in message 11, but it doesn't go to the internet or windows network using that connection.  What would you suggest?

---

### Post by chili555 on 2015-02-10
What does this tell us?```
nm-tool
ping -c3 www.ubuntu.com
ping -c3 8.8.8.8
iwconfig
```

---

### Post by bryant3 on 2015-02-11
NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             connected
  Default:           yes
  HW Address:        ===
Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address: xxx.yyy.zzz.a
    Prefix: hh (xxx.yyy.zzz.a)
    Gateway: xxx.yyy.zzz.aaa
 DNS:             192.168.254.254


- Device: wlan0  [WIN_5dc5 1] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connected
  Default:           no
  HW Address: ===

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *WIN_5dc5:       Ad-Hoc, ===, Freq === MHz, Rate 54 Mb/s, Strength 100 WPA2
    WIN_5dc5:        Infra, ===, Freq === MHz, Rate 54 Mb/s, Strength 77 WPA WPA2

  IPv4 Settings:
    Address: xx.yy.z.a
    Prefix:          24 (xxx.yyy.zzz.a)
    Gateway:         0.0.0.0

ping -c3 [www.ubuntu.com]("http://www.ubuntu.com")
PING [www.ubuntu.com]("http://www.ubuntu.com") (91.189.90.58) 56(84) bytes of data.
64 bytes from [www.ubuntu.com]("http://www.ubuntu.com") (91.189.90.58): icmp_seq=1 ttl=50 time=153 ms
64 bytes from [www.ubuntu.com]("http://www.ubuntu.com") (91.189.90.58): icmp_seq=2 ttl=50 time=152 ms
64 bytes from [www.ubuntu.com]("http://www.ubuntu.com") (91.189.90.58): icmp_seq=3 ttl=50 time=152 ms

--- [www.ubuntu.com]("http://www.ubuntu.com") ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 152.166/152.679/153.387/0.607 ms

ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=54 time=56.9 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=54 time=55.3 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=54 time=58.3 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 55.351/56.891/58.394/1.257 ms

iwconfig
wlan0     IEEE 802.11bg  ESSID:"WIN_5dc5"  
          Mode:Ad-Hoc  Frequency:=== GHz  Cell: ======   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.

Thanks,

---

### Post by chili555 on 2015-02-11
Where do I even start!?!?

First, you have a working ethernet connection. We can't effectively troubleshoot your connection when there is a perfectly operating ethernet connection in place. All those great ping results show us is that your ethernet works fine.

Second, please note:> iwconfig
wlan0 IEEE 802.11bg ESSID:"WIN_5dc5"
[COLOR="#FF0000"]Mode:Ad-Hoc [/COLOR]Frequency:2.412 GHz Cell: B2:F6E:15:45:71
Tx-Power=20 dBm
Retry long limit:7 RTS thrff Fragment thrff
Power Managementff
Ad Hoc is for computer-to-computer connections; not for computer to access point. Please detach the ethernet, click the Network Manager icon, select Edit Connections, then Wi-Fi and select Edit. Set the Mode to Infrastructure. Then, in a terminal, restart NM:```
sudo service network-manager restart
```Now try to connect and then let us hear your results.

---

### Post by bryant3 on 2015-02-11
After the first instruction to change the mode to infrastructure and in terminal restart NM, I can no longer connect to the WIFI.  The connection process is looking for Authentication, which, when entered requests the same info a few seconds later.  Running in ADHOC mode, the same password was accepted and a connection was made.

When I try to navigate to a web page, Server not found...

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unavailable
  Default:           no
  HW Address: ---

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address: ...

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    WIN_5dc5:        Infra,---, Freq ,,, MHz, Rate 54 Mb/s, Strength 84 WPA WPA2

---

### Post by chili555 on 2015-02-11
>  Running in ADHOC mode, the same password was accepted and a connection was made.

When I try to navigate to a web page, Server not found...As it always will be because Ad Hoc is incorrect. I suggest you delete the connection in NM, change back to Infrastructure and then reboot.

[ATTACH=CONFIG]259922[/ATTACH]

---

### Post by bryant3 on 2015-02-11
I apologize for letting you know that when running in Ad hoc mode a connection was made, I did not mean to give you the impression that I was attempting to navigate to a web page while in that mode, but in the infrastructure mode.    

What I just did now, moments before hitting send:  Deleted the Wireless Connection (WIFI, Win_5dc5), using the Edit Connections Option; Using Network Connections ICON I then Created a WIFI Connection, entered the appropriate information.  The system immediately indicated it was "Connected".  I unplugged the ethernet cable, and was able to navigate to web pages.

Thank you for your assistance.  Problem solved.

---

### Post by chili555 on 2015-02-11
Awesome! Glad it's working. Have fun!

---

