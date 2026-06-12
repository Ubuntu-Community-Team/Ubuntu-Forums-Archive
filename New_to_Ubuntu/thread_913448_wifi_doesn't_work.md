---
title: "wifi doesn't work"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by samuelj on 2008-09-07
my connection is ADSL through a motorola modem/belkin N router.

hardware is acer aspire 5720z
windows vista was the original OS

ISP is att.net in the US

Ubuntu version is 8.04

if i use the hard wire, i'm great. if not, there is no wifi.

i am connected through the hardwire to get online access at the moment.

lspci output

samuelj@samuelj-mobile:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
07:00.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:00.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:00.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:00.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
samuelj@samuelj-mobile:~$


lsusb output

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

samuelj@samuelj-mobile:~$ lsusb
Bus 007 Device 002: ID 5986:0102 Bison
Bus 007 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 003: ID 413c:3016 Dell Computer Corp.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
samuelj@samuelj-mobile:~$

lshw -class network output

samuelj@samuelj-mobile:~$ lshw -class network
WARNING: you should run this program as super-user.
*-network
description: Ethernet interface
product: NetLink BCM5787M Gigabit Ethernet PCI Express
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:05:00.0
logical name: eth0
version: 02
serial: 00:1b:38:55:67:20
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5787m-v3.22 ip=192.168.2.3 latency=0 module=tg3 multicast=yes
*-network UNCLAIMED
description: Ethernet controller
product: AR242x 802.11abg Wireless PCI Express Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:06:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=0


i do not dual boot to windows.



another issue is my touchpad no longer works. i have had to start using a wired mouse. no clue as to why though. didn't have problems before. i have wiped the drive and reinstalled ubuntu with no luck on that part.

ndiswrapper has done nothing to help. 
when i do the ndiswrapper update, the only results i get are
ndisgtk
ndiswrapper-common
ndiswrapper-utils 1.9

iwconfig output-

samuelj@samuelj-mobile:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

samuelj@samuelj-mobile:~$

the wireless driver is the ath5k and i have also tried madwifi under under dreamlinux with no luck.

---

### Post by phidia on 2008-09-07
What about "ndiswrapper -l" what does that output?
It looks like the driver isn't installed or if it's installed it's not working. 

You do need to install the windows drivers with ndiswrapper. See the HOWTO [here]("http://ubuntuforums.org/showthread.php?t=792158&highlight=Atheros+ar5007eg") or give the madwifi (no windows driver required) HOWTO [here]("http://ubuntuforums.org/showthread.php?t=795984&highlight=Atheros+ar5007eg").

---

### Post by samuelj on 2008-09-07
cell 4 lists my wireless network - groove machine
i still can't access any wireless networks or anything. 

now what - (this is the furthest i have managed to get. at least i see something new here)


samuelj@samuelj-mobile:~$ sudo iwlist scanning
[sudo] password for samuelj: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:17:3F:58:38:00
                    ESSID:"sparky"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=1/70  Signal level=-94 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:06:25:61:50:D0
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=10/70  Signal level=-85 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:18:F8:1B:60:11
                    ESSID:"Customer ID"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=2/70  Signal level=-93 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:1C:DF:76:23:6F
                    ESSID:"groove machine"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=65/70  Signal level=-30 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
          Cell 05 - Address: 00:1B:2F:B6:F5:A2
                    ESSID:"cindi12"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-72 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101820003a4000027a4000042435e0062322f00
                    Extra:ath_ie=dd0900037f01010035ff7f

samuelj@samuelj-mobile:~$

---

### Post by samuelj on 2008-09-07
finally managed to get a wireless connection. now to figure why my touchpad stopped working

---

