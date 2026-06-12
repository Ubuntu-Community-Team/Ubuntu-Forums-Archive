---
title: "Problems with 13.10"
date: 2013-12-12
forum: New to Ubuntu
---

### Post by GaryTheCat on 2013-12-12
[COLOR=#000000]Here goes....[/COLOR]

[COLOR=#000000]I tried 13.10 from USB and it worked fine - just had to enable the broadcom driver for WiFi as usual but it was all fine. I've now installed it and for some reason it thinks the wireless card isn't working. I know it is working as I inadvertently left 13.04 on the machine during upgrade.[/COLOR]

[COLOR=#000000]So I have 2 questions:[/COLOR]

[COLOR=#000000]1. How can I get my wireless card working in 13.10? and [/COLOR]
[COLOR=#000000]2. How can I remove 13.04 from grub and the machine and remove the partition so I can do something useful with it?[/COLOR]

[COLOR=#000000]Many thanks[/COLOR]

---

### Post by DuckHook on 2013-12-12
Hi GaryTheCat,

1. You've been around the forums long enough by now to know that we need more far more info to solve your first problem. ;)   HW specs please. Do the lspci ifconfig iwconfig things. Can't help without knowing what we're dealing with.

2. The easiest way to deal with issue #2 is to delete the partition on which 13.04 resides, then run```
sudo update-grub
```But you must make sure that 13.04 is not on the same partition as GRUB, or you will be deleting GRUB along with the OS and won't be able to boot any partition at all. You could use boot rescue to reinstall GRUB and make your remaining partition bootable, but that sort of simple mistake would hurt my pride.

---

### Post by GaryTheCat on 2013-12-12
D'Oh ... It's been ages since I posted any Q's on here... here goes:

> 
lspci

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G84M [GeForce 8600M GT] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)




(where'd the code tags go?)

> 
ifconfig

eth0      Link encap:Ethernet  HWaddr 0e:77:1a:25:e4:1b            UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


eth2      Link encap:Ethernet  HWaddr 00:1d:09:d6:a4:57  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 


eth3      Link encap:Ethernet  HWaddr 00:1f:e1:c8:99:b3  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:e1ff:fec8:99b3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:63801 errors:0 dropped:0 overruns:0 frame:696379
          TX packets:59690 errors:11 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:43409072 (43.4 MB)  TX bytes:15931873 (15.9 MB)
          Interrupt:17 Base address:0xc000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:6448 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6448 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:703341 (703.3 KB)  TX bytes:703341 (703.3 KB)




> lo        no wireless extensions.

eth0      no wireless extensions.


eth2      no wireless extensions.


eth3      IEEE 802.11abg  ESSID:"SKY8EB42_EXT"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 9C:D3:6D:99:8B:9E   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on




NB this was obtained running 13.04 not 13.10

Many thanks

---

### Post by DuckHook on 2013-12-12
The [CODE] tags are not visible in the quick reply box but only in the advanced reply box where they are the "#" tags.

As feared. The dreaded Broadcom chip. Not the Ethernet controller—that one's cool—the one causing you grief is the BCM4312. It uses proprietary firmware in the driver, so isn't autoloaded for fear of kernel taint. The reason that it works in LiveUSB is because Ubuntu compromises and allows the kernel to load it by default, but only in LiveUSB mode so that LiveUSB will work over the greatest variety of HW. When it comes to your actual installation, you will have to take specific measures to load it. Since you are using 13.10, you can open System Settings>Software & Updates>Additional Drivers. You may find an additional driver there if the system detects the Broadcom chip. If so, you can try installing the driver to see if that works. On my system, this autosensed driver does not work and I have to use the old-fashioned method, but then, I have a BCM4311, which is more problematic than yours. If the above technique doesn't work then I'm afraid you will just have to follow instructions [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") and install the driver the old-fashioned way.

Good luck and let us know how it goes.

---

### Post by GaryTheCat on 2014-01-16
Thanks for that - I've completely fixed everything, just needed to plug the machine into my router to solve the dreaded Bradcom issue!

Happy Me!

---

