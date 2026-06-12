---
title: "[SOLVED] AR5007EG/Toshiba P205D-S7802/ubuntu 8.04"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by KC1117 on 2008-11-29
Artheros AR5007EG wireless works in Windows, but not Ubuntu.  
I just got my Ubuntu 8.04 up and running and everything seems to be working fine. I have not added any additional files other than what opened automatically with the disk.  

I did read lots of posts and although it seems there are a gillion ways people have fixed this problem, I decided to follow the MadWifi instructions to get my wireless running.  After it took me forever to figure out where to input code :) I got stuck in downloading the drivers with this instruction:

"Download a MadWifi release from sourceforge.net and unpack it. Open a shell terminal in the MadWifi source directory."

1)I think I downloaded and unpacked it successfully,(I used an "extract" command I found) but I don't know if that is the same as "install."  So I guess that my first question is how to make sure this is installed properly, this one specifically.  I tried to add Hardware Drivers, but don't know what file to open.

2) I don't know how to "open a shell terminal in the MadWifi source directory" for the rest of the commands  OR
should I be doing something completely different?

Any guidance will be appreciated.

The following information came from my computer.  If more is needed please let me know and I won't be offended if you tell me exactly where to find it. 


Toshiba Satellite P205D-S7802
$ lsb_release –d  Ubuntu 8.04

Thank you in advance for your help.  
lspci

11:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
17:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
1d:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
1d:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
1d:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
1d:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller


kelly@kelly-laptop:~$ lsusb
Bus 004 Device 003: ID 046d:c51b Logitech, Inc. 

kelly@kelly-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:04:a4:4f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0xc000 

eth0:	avahi Link encap:Ethernet  HWaddr 00:1e:ec:04:a4:4f  
          inet addr:169.254.6.30  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:220 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:234 errors:0 dropped:0 overruns:0 frame:0
          TX packets:234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12070 (11.7 KB)  TX bytes:12070 (11.7 KB)


kelly@kelly-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

kelly@kelly-laptop:~$ lsmod
wlan                  207728  1 ath_pci
ath_hal               192592  1 ath_pci


dmesg

[  567.214015] r8169: eth0: link down
[  567.215287] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  568.308319] NET: Registered protocol family 17
[  900.240107] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  900.240115] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  900.240121] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.



kelly@kelly-laptop:~$ sudo lshw -C network
[sudo] password for kelly: 
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:11:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:04:a4:4f
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:17:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0

kelly@kelly-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by oilchangeguy on 2008-11-29
the easiest way to get wireless if you're using linux. buy an external usb wireless adapter. they usually work out of the box.

---

### Post by adult swim on 2008-11-29
1.) extracting the file is not the same as installing it.  the file you downloaded was a compressed archive and when you extracted it, it was uncompressed.  
2.) when the tutorial is telling you to open a shell terminal in the source directory, it means  you need to direct the terminal to go to the directory you just extracted.  to do this all  you need to do is run from a terminal ```
cd /path/to/directory
``` for instance if the directory is named madwifi3.0.23 and is on your desktop  you would put in ```
cd Desktop/madwifi3.0.23
```and then run the commands the tutorial is telling you.

---

### Post by KC1117 on 2008-11-29
> **adult swim said:**
> 1.) extracting the file is not the same as installing it.  the file you downloaded was a compressed archive and when you extracted it, it was uncompressed.  
2.) when the tutorial is telling you to open a shell terminal in the source directory, it means  you need to direct the terminal to go to the directory you just extracted.  to do this all  you need to do is run from a terminal ```
cd /path/to/directory
``` for instance if the directory is named madwifi3.0.23 and is on your desktop  you would put in ```
cd Desktop/madwifi3.0.23
```and then run the commands the tutorial is telling you.

Thank you, I'll give that a try and see how far I get.

---

### Post by lkraemer on 2008-11-29
Just follow this HOWTO:
http://ubuntuforums.org/showthread.php?t=792158

lkraemer

---

### Post by KC1117 on 2008-12-14
I basically used the instructions posted above, but needed a little more beginner step by step instructions and found a little more help at
[http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work-2/](http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work-2/)

Thank you for all the help.

---

