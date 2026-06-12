---
title: "gateway m-6309 wireless issue"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by janong on 2008-06-20
hello all...i´m new to linux and i got a laptop gateway m-6309 dual booted to vista(1st) and ubuntu 8.04;  as i write this post, i´m connected online through a modem: ¨lynx 210 starbridge network¨ ethernet wired to a wireless router: ¨dlink dir655¨ then ethernet wired  to this laptop. i notice that when i remove the wired connections (both vista and ubuntu) and use wireless option to go online, i can connect to the internet. i read from a post that ¨you should uncheck the item: [COLOR="Red"]allow the computer to turn off this device to save power[/COLOR] under power management in vista which i did already but can solve the problem.
below are some info:

john@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
john@ubuntu:~$ lsusb
Bus 007 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
john@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:e0:b8:e5:3f:e3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.0.183 latency=0 module=r8169 multicast=yes
john@ubuntu:~$ ethernet

please help and thank you in advance.

---

