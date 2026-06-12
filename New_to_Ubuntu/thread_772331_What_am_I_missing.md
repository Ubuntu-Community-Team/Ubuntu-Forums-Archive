---
title: "What am I missing?"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by sarujin on 2008-04-28
Hello everyone,
I am almost a complete novice.  I have a little experince with Fedora and messing with some live cds.  I came across Wubi and it made the installation of Heron very easy as I need to keep XP for work.

My only problem thus far is WiFi.  I cannot seem to get it working correctly.  There does not seem to be any type of WiFi search tool. I have not had a problem with WiFi on other systems and after reading the forums I have some ideas on what is wrong (broadcom, AMD chipset, etc...) but I would like to get some insight about what I am doing wrong or missing.  I have tried installing wicd and it did not seem to work.

I want to enjoy ubuntu.  Please help!

Here is what I have (probably too much info):

System Manufacturer Dell Inc.
Processor AMD Turion(tm) 64 X2 Mobile Technology TL-60
BIOS Version DELL   - 6040000
Total Physical Memory 895 MB
Available Physical Memory 148 MB

[Devices]
Microsoft AC Adapter Battery
AMD K8 Processor Processor
ACPI Fixed Feature Button System
Programmable interrupt controller System
System timer System
Direct memory access controller System
Standard 101/102-Key or Microsoft Natural PS/2 Keyboard Keyboard
System speaker System
PCI bus System
System CMOS/real time clock System
System board System
Motherboard resources System
Numeric data processor System
Microsoft ACPI-Compliant Embedded Controller System
Microsoft ACPI-Compliant Control Method Battery Battery
ACPI Power Button System
ACPI Lid System
ACPI Sleep Button System
Microsoft Windows Management Interface for ACPI System
Synaptics PS/2 Port TouchPad Mouse
ACPI Thermal Zone System
Microsoft ACPI-Compliant System System
Default Monitor Monitor
SigmaTel High Definition Audio CODEC MEDIA
Conexant HDA D110 MDC V.92 Modem Modem
CD-ROM Drive CDROM
Disk drive DiskDrive
ISAPNP Read Data Port System
Standard Dual Channel PCI IDE Controller hdc
PCI standard PCI-to-PCI bridge System
ATI SMBus System
Standard Enhanced PCI to USB Host Controller USB
Standard OpenHCD USB Host Controller USB
Standard Dual Channel PCI IDE Controller hdc
PCI standard ISA bridge System
PCI standard host CPU bridge System
ATI Radeon Xpress 1150    Display
PCI standard PCI-to-PCI bridge System
PCI standard host CPU bridge System
SDA Standard Compliant SD Host Controller SDHost
Ricoh MMC Host Controller hdc
Broadcom 440x 10/100 Integrated Controller Net
Dell Wireless 1390 WLAN Mini-Card Net
Primary IDE Channel hdc
Secondary IDE Channel hdc
Primary IDE Channel hdc
Secondary IDE Channel hdc
ACPI Multiprocessor PC Computer
Volume Manager System
AFD LegacyDriver
APPDRV LegacyDriver
aswRdr LegacyDriver
Beep LegacyDriver
dmboot LegacyDriver
dmload LegacyDriver
DSproct LegacyDriver
DellSupport UniDriver LegacyDriver
Fips LegacyDriver
Generic Packet Classifier LegacyDriver
HTTP LegacyDriver
i2omgmt LegacyDriver
IP Network Address Translator LegacyDriver
IPSEC driver LegacyDriver
ksecdd LegacyDriver
mnmdd LegacyDriver
mountmgr LegacyDriver
NDIS System Driver LegacyDriver
Remote Access NDIS TAPI Driver LegacyDriver
NDIS Usermode I/O Protocol LegacyDriver
NDProxy LegacyDriver
NetBios over Tcpip LegacyDriver
Network Monitor Driver LegacyDriver
NetGroup Packet Filter Driver LegacyDriver
NSNDIS5 NDIS Protocol Driver LegacyDriver
Null LegacyDriver
PartMgr LegacyDriver
ParVdm LegacyDriver
Remote Access Auto Connection Driver LegacyDriver
RDPCDD LegacyDriver
symlcbrd LegacyDriver
TCP/IP Protocol Driver LegacyDriver
truecrypt LegacyDriver
VgaSave LegacyDriver
VolSnap LegacyDriver
Remote Access IP ARP Driver LegacyDriver
Driver LegacyDriver
Audio Codecs MEDIA
Legacy Audio Drivers MEDIA
Media Control Devices MEDIA
Legacy Video Capture Devices MEDIA
Video Codecs MEDIA
WAN Miniport (L2TP) Net
WAN Miniport (Network Monitor) Net
WAN Miniport (IP) Net
WAN Miniport (PPPOE) Net
WAN Miniport (PPTP) Net
Packet Scheduler Miniport Net
Direct Parallel Net
Terminal Server Keyboard Driver System
Terminal Server Mouse Driver System
Plug and Play Software Device Enumerator System
Microcode Update Device System
Microsoft System Management BIOS Driver System
Microsoft Kernel System Audio Device MEDIA
Microsoft Kernel Wave Audio Mixer MEDIA
Microsoft WINMM WDM Audio Compatibility Driver MEDIA

---

### Post by hyper_ch on 2008-04-28
do a
```

lspci | grep Wire

```

and post the output here...

if that doesn't show anything do:

```

lspci > ~/Desktop/output.txt

```

and then post the content of the output.txt file on your desktop here.

---

### Post by sarujin on 2008-04-28
TaDa!

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)

---

### Post by mikewhatever on 2008-04-28
Take a look at this thread [http://ubuntuforums.org/showthread.php?t=760974&highlight=BCM94311MCG](http://ubuntuforums.org/showthread.php?t=760974&highlight=BCM94311MCG). It might be heading in the right direction.

---

### Post by sarujin on 2008-05-05
I ended up going here: [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)
It worked (at least for now)

---

