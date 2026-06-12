---
title: "broadcom problems on dell precision m90"
date: 2012-10-17
forum: New to Ubuntu
---

### Post by gamekidmatt96 on 2012-10-17
Hello, this is my first forum post, so yay me!

So, basically, I installed ubuntu 12.04 for the first time today. So far I like it. It's very refreshing from windows.

But there's a problem: Ubuntu doesn't properly configure my wifi adapter. I have a dell precision m90 and am currently tied into the router posting this.

I have been googling the problem for quite some time now. I have tried what other forum threads said would work, like uninstalling the broadcom drivers, then downloading them from the ubuntu software center, etc. I just can't get it to work.

I don't know much about terminal, but I know that it will be involved in the solution, so can you please clearly explain what to do in terminal?

Any help will be appreciated!

---

### Post by daslinkard on 2012-10-18
1st, welcome to the forums!  Please open the terminal by holding down > CTRL+ALT+T

What is the output of the following terminal command
```
lspci
```

---

### Post by gamekidmatt96 on 2012-10-22
Here's the output:

"00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: NVIDIA Corporation G71 [Quadro FX 1500M] (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)"

---

### Post by gamekidmatt96 on 2012-10-22
Wait! I fixed it for now! I mixed quite a few methods together and wireless is working. I'll reboot and see if it still works.

---

### Post by daslinkard on 2012-10-22
> **gamekidmatt96 said:**
> Wait! I fixed it for now! I mixed quite a few methods together and wireless is working. I'll reboot and see if it still works.

I'm curious if this fixed your issue at hand.  If so can you let us know what methods resolved the issue for you?  Looking forward to your response...

---

### Post by Steve J on 2012-11-20
I still have a problem with the Broadcom wifi.  Here''s the lspci output:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: NVIDIA Corporation G71 [Quadro FX 2500M] (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 01)

When I use ndisgtk, it says the driver is installed and the hardware is present.

Any help appreciated.

Steve

---

### Post by newb85 on 2012-11-20
It would be a lot easier to help if we knew what you've tried and what changes you've made to your system in the process of trying.

---

### Post by wildmanne39 on 2012-11-20
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by Steve J on 2012-11-20
Wild Man,

Here's the info you requested:


*************** info trace ****************



**** uname -a ****


Linux steve-laptop 3.2.0-33-generic #52-Ubuntu SMP Thu Oct 18 16:19:45 UTC 2012 i686 i686 i386 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"


**** lspci ****


09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
    Subsystem: Dell Device [1028:01cf]
    Kernel driver in use: tg3
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
    Subsystem: Dell Wireless 1490 Dual Band WLAN Mini-Card [1028:0007]
    Kernel modules: wl, ssb


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 002 Device 003: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 004: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 002 Device 005: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader


**** iwconfig ****




**** rfkill ****


0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
wl                   2646601  0 
lib80211               14040  1 wl
rfcomm                 38139  0 
dm_crypt               22528  0 
bnep                   17830  2 
parport_pc             32114  0 
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
nvidia              10962290  42 
binfmt_misc            17292  1 
joydev                 17393  0 
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  5 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_intel,snd_hda_codec
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                96684  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
wmi                    18744  1 dell_wmi
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
r852                   17901  0 
sm_common              16737  1 r852
nand                   49667  2 r852,sm_common
nand_ids                8547  1 nand
mtd                    35584  2 sm_common,nand
r592                   17808  0 
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
memstick               15857  1 r592
snd                    62064  18 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13077  0 
serio_raw              13027  0 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
firewire_ohci          40180  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
video                  19068  0 
tg3                   137273  0 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.107
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****




**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search ph.cox.net


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


**** dmesg ****


[    1.118917] tg3.c:v3.121 (November 2, 2011)
[    1.118939] tg3 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.118952] tg3 0000:09:00.0: setting latency timer to 64
[    1.142668] tg3 0000:09:00.0: eth0: Tigon3 [partno(BCM5752KFBG) rev 6002] (PCI Express) MAC address <MAC address removed>
[    1.142674] tg3 0000:09:00.0: eth0: attached PHY is 5752 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.142678] tg3 0000:09:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.142682] tg3 0000:09:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   20.288184] wmi: Mapper loaded
[   21.473920] tg3 0000:09:00.0: irq 46 for MSI/MSI-X
[   23.096965] tg3 0000:09:00.0: eth0: Link is up at 100 Mbps, full duplex
[   23.096969] tg3 0000:09:00.0: eth0: Flow control is on for TX and on for RX
[ 2514.236937] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 2514.236948] wl 0000:0c:00.0: setting latency timer to 64


**************** done ********************

---

### Post by Steve J on 2012-11-20
> **newb85 said:**
> It would be a lot easier to help if we knew what you've tried and what changes you've made to your system in the process of trying.


I've tried a LOT of things, including this:
**11.10 (Oneiric Ocelot) - 12.10 (Quantal Quetzal)**

 Open a [Terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and install the bcmwl-kernel-source package:
sudo apt-get update sudo apt-get install bcmwl-kernel-source**Note:**  If you see the message "Module build for the currently running kernel  was skipped since the kernel source for this kernel does not seem to be  installed" then you are missing the appropriate generic linux-header  package(s).
 
To test the driver (and remove the need for a computer restart) use: 
sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma sudo modprobe wlAllow several seconds for the network manager to scan for available networks before attempting a connection. 
The  bcmwl-kernel-source package should automatically blacklist the open  source drivers so that the STA driver is the only one in use.  However,  some **11.10** users may have to manually blacklist the open source modules (please see the [Known Issues]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Known_Issues") section). 
 [Back to top]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Top")

---

### Post by wildmanne39 on 2012-11-20
Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```
Then:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
Reboot
Thanks

---

### Post by Steve J on 2012-11-20
> **wild man said:**
> hi, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```then:
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```then:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```reboot
thanks

ok, i did what you suggested but  no luck.... :(

---

### Post by Steve J on 2012-11-20
> **Wild Man said:**
> Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```Then:
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```Then:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```Reboot
Thanks

BTW, last night I did manage to get some wireless message text to show up when I clicked on the connection icon but it said "no firmware installed".  I then re-booted and that message text disappeared...:(

---

### Post by wildmanne39 on 2012-11-20
Hi, delete the netinfo.txt file in your home folder and run the wireless script again and post the results so we can see the condition of your wireless now.
Thanks

---

### Post by Steve J on 2012-11-20
> **Wild Man said:**
> Hi, delete the netinfo.txt file in your home folder and run the wireless script again and post the results so we can see the condition of your wireless now.
Thanks

OK, here are the results:


*************** info trace ****************



**** uname -a ****


Linux steve-laptop 3.2.0-33-generic #52-Ubuntu SMP Thu Oct 18 16:19:45 UTC 2012 i686 i686 i386 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"


**** lspci ****


09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
    Subsystem: Dell Device [1028:01cf]
    Kernel driver in use: tg3
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
    Subsystem: Dell Wireless 1490 Dual Band WLAN Mini-Card [1028:0007]
    Kernel modules: ssb


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 002 Device 003: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 004: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 002 Device 005: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader


**** iwconfig ****




**** rfkill ****


0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes


**** lsmod ****


Module                  Size  Used by
dm_crypt               22528  0 
rfcomm                 38139  0 
nvidia              10962290  42 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
joydev                 17393  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                96684  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
wmi                    18744  1 dell_wmi
r852                   17901  0 
sm_common              16737  1 r852
nand                   49667  2 r852,sm_common
nand_ids                8547  1 nand
mtd                    35584  2 sm_common,nand
r592                   17808  0 
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
memstick               15857  1 r592
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
mac_hid                13077  0 
serio_raw              13027  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
firewire_ohci          40180  0 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
video                  19068  0 
tg3                   137273  0 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.107
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****




**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search ph.cox.net


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


**** dmesg ****


[    1.109628] tg3.c:v3.121 (November 2, 2011)
[    1.109649] tg3 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.109661] tg3 0000:09:00.0: setting latency timer to 64
[    1.128495] tg3 0000:09:00.0: eth0: Tigon3 [partno(BCM5752KFBG) rev 6002] (PCI Express) MAC address <MAC address removed>
[    1.128500] tg3 0000:09:00.0: eth0: attached PHY is 5752 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.128504] tg3 0000:09:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.128508] tg3 0000:09:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   20.279335] wmi: Mapper loaded
[   21.809782] tg3 0000:09:00.0: irq 46 for MSI/MSI-X
[   23.492169] tg3 0000:09:00.0: eth0: Link is up at 100 Mbps, full duplex
[   23.492173] tg3 0000:09:00.0: eth0: Flow control is on for TX and on for RX


**************** done ********************

---

### Post by Steve J on 2012-11-20
> **Wild Man said:**
> Hi, delete the netinfo.txt file in your home folder and run the wireless script again and post the results so we can see the condition of your wireless now.
Thanks

BTW, thank you for taking the time to help me.  :)

---

### Post by wildmanne39 on 2012-11-20
Hi, when you ran this command ```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
where there any errors?

It shows that you have a soft and hard block we can work on this but I want to make sure there were do problems when you installed the driver and firmware.

You had to have an internet connection when you ran that command also. If any doubt run this command and we will make sure.
```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
```
Then:
```
sudo modprobe b43
```
Thanks

---

### Post by Steve J on 2012-11-20
*Hi, when you ran this command * 	*Code:*
 	*sudo apt-get install b43-fwcutter firmware-b43-installer* 
[I]where there any errors?

[/I]No but here's the output:

steve@steve-laptop:~$ sudo apt-get install b43-fwcutter firmware-b43-installer
[sudo] password for steve: 
Sorry, try again.
[sudo] password for steve: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
firmware-b43-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  diffstat module-assistant quilt
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
steve@steve-laptop:~$

---

### Post by Steve J on 2012-11-20
You had to[I] have an internet connection when you ran that command also. If any doubt run this command and we will make sure.
[/I]  	*Code:*
 	[I]sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer

[/I]OK, here's the output for that command:

steve@steve-laptop:~$ sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  diffstat module-assistant quilt
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 18.9 kB/22.4 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main b43-fwcutter i386 1:015-9 [18.9 kB]
Fetched 18.9 kB in 0s (48.9 kB/s)       
(Reading database ... 187002 files and directories currently installed.)
Preparing to replace b43-fwcutter 1:015-9 (using .../b43-fwcutter_1%3a015-9_i386.deb) ...
Unpacking replacement b43-fwcutter ...
Preparing to replace firmware-b43-installer 1:015-9 (using .../firmware-b43-installer_1%3a015-9_all.deb) ...
Unpacking replacement firmware-b43-installer ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:015-9) ...
Setting up firmware-b43-installer (1:015-9) ...
No chroot environment found. Starting normal installation
This card work with newer 5.10.56.27.3 firmware. Trying to install it.
--2012-11-20 18:08:41--  [http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2)
Resolving mirror2.openwrt.org (mirror2.openwrt.org)... 46.4.11.11
Connecting to mirror2.openwrt.org (mirror2.openwrt.org)|46.4.11.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1596823 (1.5M) [application/x-bzip2]
Saving to: `broadcom-wl-5.10.56.27.3_mipsel.tar.bz2'

100%[======================================>] 1,596,823    521K/s   in 3.0s    

2012-11-20 18:08:45 (521 KB/s) - `broadcom-wl-5.10.56.27.3_mipsel.tar.bz2' saved [1596823/1596823]

Deleting old extracted firmware...
broadcom-wl-5.10.56.27.3/driver/
broadcom-wl-5.10.56.27.3/driver/Makefile
broadcom-wl-5.10.56.27.3/driver/aiutils.c
broadcom-wl-5.10.56.27.3/driver/bcmsrom.c
broadcom-wl-5.10.56.27.3/driver/bcmutils.c
broadcom-wl-5.10.56.27.3/driver/hnddma.c
broadcom-wl-5.10.56.27.3/driver/hndpmu.c
broadcom-wl-5.10.56.27.3/driver/include/
broadcom-wl-5.10.56.27.3/driver/include/UdpLib.h
broadcom-wl-5.10.56.27.3/driver/include/aidmp.h
broadcom-wl-5.10.56.27.3/driver/include/arminc.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcdc.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/aes.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/aeskeywrap.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/bcmccx.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/bn.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/ccx.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/des.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/dh.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/hmac_sha256.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/md4.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/md5.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/passhash.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/prf.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/rc4.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/rijndael-alg-fst.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/sha1.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/sha256.h
broadcom-wl-5.10.56.27.3/driver/include/bcmcrypto/tkhash.h
broadcom-wl-5.10.56.27.3/driver/include/bcmdefs.h
broadcom-wl-5.10.56.27.3/driver/include/bcmdevs.h
broadcom-wl-5.10.56.27.3/driver/include/bcmendian.h
broadcom-wl-5.10.56.27.3/driver/include/bcmnvram.h
broadcom-wl-5.10.56.27.3/driver/include/bcmotp.h
broadcom-wl-5.10.56.27.3/driver/include/bcmparams.h
broadcom-wl-5.10.56.27.3/driver/include/bcmperf.h
broadcom-wl-5.10.56.27.3/driver/include/bcmrobo.h
broadcom-wl-5.10.56.27.3/driver/include/bcmsrom.h
broadcom-wl-5.10.56.27.3/driver/include/bcmsrom_fmt.h
broadcom-wl-5.10.56.27.3/driver/include/bcmsrom_tbl.h
broadcom-wl-5.10.56.27.3/driver/include/bcmstdlib.h
broadcom-wl-5.10.56.27.3/driver/include/bcmutils.h
broadcom-wl-5.10.56.27.3/driver/include/bcmwifi.h
broadcom-wl-5.10.56.27.3/driver/include/bitfuncs.h
broadcom-wl-5.10.56.27.3/driver/include/dmemc_core.h
broadcom-wl-5.10.56.27.3/driver/include/emf/
broadcom-wl-5.10.56.27.3/driver/include/emf/emf/
broadcom-wl-5.10.56.27.3/driver/include/emf/igs/
broadcom-wl-5.10.56.27.3/driver/include/epivers.h
broadcom-wl-5.10.56.27.3/driver/include/epivers.h.in
broadcom-wl-5.10.56.27.3/driver/include/epivers.h.prev
broadcom-wl-5.10.56.27.3/driver/include/etioctl.h
broadcom-wl-5.10.56.27.3/driver/include/flash.h
broadcom-wl-5.10.56.27.3/driver/include/flashutl.h
broadcom-wl-5.10.56.27.3/driver/include/hndarm.h
broadcom-wl-5.10.56.27.3/driver/include/hndchipc.h
broadcom-wl-5.10.56.27.3/driver/include/hndcpu.h
broadcom-wl-5.10.56.27.3/driver/include/hnddma.h
broadcom-wl-5.10.56.27.3/driver/include/hndgige.h
broadcom-wl-5.10.56.27.3/driver/include/hndjtagdefs.h
broadcom-wl-5.10.56.27.3/driver/include/hndmips.h
broadcom-wl-5.10.56.27.3/driver/include/hndpci.h
broadcom-wl-5.10.56.27.3/driver/include/hndpmu.h
broadcom-wl-5.10.56.27.3/driver/include/hndsoc.h
broadcom-wl-5.10.56.27.3/driver/include/linux_gpio.h
broadcom-wl-5.10.56.27.3/driver/include/linux_osl.h
broadcom-wl-5.10.56.27.3/driver/include/linuxver.h
broadcom-wl-5.10.56.27.3/driver/include/min_osl.h
broadcom-wl-5.10.56.27.3/driver/include/mips33_core.h
broadcom-wl-5.10.56.27.3/driver/include/mips74k_core.h
broadcom-wl-5.10.56.27.3/driver/include/mipsinc.h
broadcom-wl-5.10.56.27.3/driver/include/ndiserrmap.h
broadcom-wl-5.10.56.27.3/driver/include/nicpci.h
broadcom-wl-5.10.56.27.3/driver/include/osl.h
broadcom-wl-5.10.56.27.3/driver/include/pci_core.h
broadcom-wl-5.10.56.27.3/driver/include/pcicfg.h
broadcom-wl-5.10.56.27.3/driver/include/pcie_core.h
broadcom-wl-5.10.56.27.3/driver/include/proto/
broadcom-wl-5.10.56.27.3/driver/include/proto/802.11.h
broadcom-wl-5.10.56.27.3/driver/include/proto/802.11e.h
broadcom-wl-5.10.56.27.3/driver/include/proto/802.1d.h
broadcom-wl-5.10.56.27.3/driver/include/proto/bcmeth.h
broadcom-wl-5.10.56.27.3/driver/include/proto/bcmevent.h
broadcom-wl-5.10.56.27.3/driver/include/proto/bcmip.h
broadcom-wl-5.10.56.27.3/driver/include/proto/bcmtcp.h
broadcom-wl-5.10.56.27.3/driver/include/proto/eap.h
broadcom-wl-5.10.56.27.3/driver/include/proto/eapol.h
broadcom-wl-5.10.56.27.3/driver/include/proto/ethernet.h
broadcom-wl-5.10.56.27.3/driver/include/proto/vlan.h
broadcom-wl-5.10.56.27.3/driver/include/proto/wpa.h
broadcom-wl-5.10.56.27.3/driver/include/rts/
broadcom-wl-5.10.56.27.3/driver/include/rts/crc.h
broadcom-wl-5.10.56.27.3/driver/include/sbchipc.h
broadcom-wl-5.10.56.27.3/driver/include/sbconfig.h
broadcom-wl-5.10.56.27.3/driver/include/sbgige.h
broadcom-wl-5.10.56.27.3/driver/include/sbhndarm.h
broadcom-wl-5.10.56.27.3/driver/include/sbhndcpu.h
broadcom-wl-5.10.56.27.3/driver/include/sbhnddma.h
broadcom-wl-5.10.56.27.3/driver/include/sbhndpio.h
broadcom-wl-5.10.56.27.3/driver/include/sbmemc.h
broadcom-wl-5.10.56.27.3/driver/include/sbpcmcia.h
broadcom-wl-5.10.56.27.3/driver/include/sbsdio.h
broadcom-wl-5.10.56.27.3/driver/include/sbsdpcmdev.h
broadcom-wl-5.10.56.27.3/driver/include/sbsdram.h
broadcom-wl-5.10.56.27.3/driver/include/sbsocram.h
broadcom-wl-5.10.56.27.3/driver/include/sbsprom.h
broadcom-wl-5.10.56.27.3/driver/include/sflash.h
broadcom-wl-5.10.56.27.3/driver/include/siutils.h
broadcom-wl-5.10.56.27.3/driver/include/trxhdr.h
broadcom-wl-5.10.56.27.3/driver/include/typedefs.h
broadcom-wl-5.10.56.27.3/driver/include/wlc_ethereal.h
broadcom-wl-5.10.56.27.3/driver/include/wlioctl.h
broadcom-wl-5.10.56.27.3/driver/include/wllmacctl.h
broadcom-wl-5.10.56.27.3/driver/linux_osl.c
broadcom-wl-5.10.56.27.3/driver/nicpci.c
broadcom-wl-5.10.56.27.3/driver/nvram_stub.c
broadcom-wl-5.10.56.27.3/driver/sbutils.c
broadcom-wl-5.10.56.27.3/driver/siutils.c
broadcom-wl-5.10.56.27.3/driver/siutils_priv.h
broadcom-wl-5.10.56.27.3/driver/wl_apsta/
broadcom-wl-5.10.56.27.3/driver/wl_apsta/buildflags.mk
broadcom-wl-5.10.56.27.3/driver/wl_apsta/wl_prebuilt.o
broadcom-wl-5.10.56.27.3/driver/wl_apsta_mini/
broadcom-wl-5.10.56.27.3/driver/wl_apsta_mini/buildflags.mk
broadcom-wl-5.10.56.27.3/driver/wl_apsta_mini/wl_prebuilt.o
broadcom-wl-5.10.56.27.3/driver/wl_dbg.h
broadcom-wl-5.10.56.27.3/driver/wl_export.h
broadcom-wl-5.10.56.27.3/driver/wl_iw.c
broadcom-wl-5.10.56.27.3/driver/wl_iw.h
broadcom-wl-5.10.56.27.3/driver/wl_linux.c
broadcom-wl-5.10.56.27.3/driver/wl_linux.h
broadcom-wl-5.10.56.27.3/driver/wlc_key.h
broadcom-wl-5.10.56.27.3/driver/wlc_pub.h
broadcom-wl-5.10.56.27.3/nas_exe.o
broadcom-wl-5.10.56.27.3/shared/
broadcom-wl-5.10.56.27.3/shared/Makefile
broadcom-wl-5.10.56.27.3/shared/UdpLib.c
broadcom-wl-5.10.56.27.3/shared/bcmcvar.h
broadcom-wl-5.10.56.27.3/shared/bcmtimer.h
broadcom-wl-5.10.56.27.3/shared/ctype.c
broadcom-wl-5.10.56.27.3/shared/linux_timer.c
broadcom-wl-5.10.56.27.3/shared/netconf.h
broadcom-wl-5.10.56.27.3/shared/opencrypto.h
broadcom-wl-5.10.56.27.3/shared/rte_timers.c
broadcom-wl-5.10.56.27.3/shared/shutils.c
broadcom-wl-5.10.56.27.3/shared/shutils.h
broadcom-wl-5.10.56.27.3/shared/wl.c
broadcom-wl-5.10.56.27.3/shared/wl_linux.c
broadcom-wl-5.10.56.27.3/shared/wlutils.h
broadcom-wl-5.10.56.27.3/wl_exe.o
This file is recognised as:
  filename   :  wl_prebuilt.o
  version    :  508.1084
  MD5        :  490d4e149ecc45eb1a91f06aa75be071
Extracting b43/ucode19.fw
Extracting b43/lp0initvals14.fw
Extracting b43/ucode16_lp.fw
Extracting b43/ucode16_sslpn.fw
  ucode revision: 1084
Extracting b43/lp0bsinitvals14.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/sslpn2bsinitvals17.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/ucode16_sslpn_nobt.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/sslpn2initvals17.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/ucode17.fw
Extracting b43/sslpn1bsinitvals20.fw
Extracting b43/ucode14.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/lp0bsinitvals16.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/pcm5.fw
Extracting b43/ucode9.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/ucode20.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/n0bsinitvals16.fw
Extracting b43/lp0initvals15.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/sslpn0initvals16.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/sslpn2initvals19.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/ucode5.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/n0initvals16.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/ucode11.fw
Extracting b43/lp0initvals16.fw
Extracting b43/ucode16_mimo.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/lp0initvals13.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/ucode13.fw
Extracting b43/sslpn2bsinitvals19.fw
Extracting b43/ucode15.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/n0initvals11.fw
Extracting b43/sslpn0bsinitvals16.fw
Extracting b43/sslpn1initvals20.fw
steve@steve-laptop:~$

---

### Post by Steve J on 2012-11-20
steve@steve-laptop:~$ sudo modprobe b3
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Module b3 not found.
steve@steve-laptop:~$

---

### Post by Steve J on 2012-11-20
steve@steve-laptop:~$ sudo modprobe b43
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
steve@steve-laptop:~$

---

### Post by wildmanne39 on 2012-11-20
Hi, my mistake on that last command but you fixed it, 
Give me a minute to research that error we need to fix it.
Thanks

---

### Post by Steve J on 2012-11-20
HAH!  It's working now...THANK YOU VERY MUCH, WILD MAN...

STEVE J.

---

### Post by wildmanne39 on 2012-11-20
Hi, that is great!
Enjoy

---

### Post by Steve J on 2012-11-21
I HAZ A SAD!  After I turned off the machine, the wifi disappeared...

Here's the printout of the script you gave me:


*************** info trace ****************



**** uname -a ****


Linux steve-laptop 3.2.0-33-generic #52-Ubuntu SMP Thu Oct 18 16:19:45 UTC 2012 i686 i686 i386 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"


**** lspci ****


09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
    Subsystem: Dell Device [1028:01cf]
    Kernel driver in use: tg3
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
    Subsystem: Dell Wireless 1490 Dual Band WLAN Mini-Card [1028:0007]
    Kernel modules: ssb


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 002 Device 003: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 004: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 002 Device 005: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader


**** iwconfig ****




**** rfkill ****


0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
dm_crypt               22528  0 
rfcomm                 38139  0 
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
nvidia              10962290  42 
binfmt_misc            17292  1 
joydev                 17393  0 
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
wmi                    18744  1 dell_wmi
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
r592                   17808  0 
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
r852                   17901  0 
sm_common              16737  1 r852
nand                   49667  2 r852,sm_common
nand_ids                8547  1 nand
mtd                    35584  2 sm_common,nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
memstick               15857  1 r592
psmouse                96684  0 
mac_hid                13077  0 
serio_raw              13027  0 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
firewire_ohci          40180  0 
sdhci_pci              18324  0 
firewire_core          56906  1 firewire_ohci
sdhci                  28241  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
video                  19068  0 
tg3                   137273  0 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.105
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****




**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search simplybits.net


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


**** dmesg ****


[    1.091637] tg3.c:v3.121 (November 2, 2011)
[    1.091659] tg3 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.091671] tg3 0000:09:00.0: setting latency timer to 64
[    1.117973] tg3 0000:09:00.0: eth0: Tigon3 [partno(BCM5752KFBG) rev 6002] (PCI Express) MAC address <MAC address removed>
[    1.117979] tg3 0000:09:00.0: eth0: attached PHY is 5752 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.117983] tg3 0000:09:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.117987] tg3 0000:09:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   21.416973] wmi: Mapper loaded
[   22.659460] type=1400 audit(1353475012.328:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=824 comm="apparmor_parser"
[   23.149869] tg3 0000:09:00.0: irq 46 for MSI/MSI-X
[  403.809596] tg3 0000:09:00.0: eth0: Link is up at 100 Mbps, full duplex
[  403.809604] tg3 0000:09:00.0: eth0: Flow control is on for TX and on for RX


**************** done ********************

---

### Post by wildmanne39 on 2012-11-21
Hi, please do:
```
sudo su 
echo b43 >> /etc/modules 
exit

```
I hope you have not tried anything else.
Reboot
Thanks

---

### Post by Steve J on 2012-11-21
> **Wild Man said:**
> Hi, please do:
```
sudo su 
echo b43 >> /etc/modules 
exit

```I hope you have not tried anything else.
Reboot
Thanks

No, I didn't try anything else.

---

### Post by Steve J on 2012-11-21
OK, it works again!  :-)

BTW, is there something like "Ubunto for Dummies" online?

---

### Post by squakie on 2012-11-21
> **Steve J said:**
> OK, it works again!  :-)

BTW, is there something like "Ubunto for Dummies" online?

If that was reversed - dummies for Ubuntu - it would be me! :)  Welcome to the Ubuntu community.  You probably noticed - Wild Man is very knowledgeable and a great help to people here on the forum!

---

### Post by wildmanne39 on 2012-11-21
Hi, if you want a book I recommend buying one from Amazon.

Here are some things that might help.
[http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/](http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/)
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)
Thanks

---

### Post by squakie on 2012-11-21
I think there is also still available a 250 or so page book available for free download yet on the net, but if I remember correctly you had to register (free) at the site.  If I can find that I'll post the link.


Can't remember if this is it or not:  [http://www.linux-books.us/linux_general_0003.php](http://www.linux-books.us/linux_general_0003.php)

Note it will be about linux in general.

---

### Post by Steve J on 2012-11-22
> **wild man said:**
> hi, if you want a book i recommend buying one from amazon.

Here are some things that might help.
[http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/](http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/)
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)
thanks

thanx again!

---

### Post by Steve J on 2012-11-22
[I]Can't remember if this is it or not:  [http://www.linux-books.us/linux_general_0003.php](http://www.linux-books.us/linux_general_0003.php)

Note it will be about linux in general.

[/I]That will also work...

---

### Post by Steve J on 2012-11-22
> **squakie said:**
> i think there is also still available a 250 or so page book available for free download yet on the net, but if i remember correctly you had to register (free) at the site.  If i can find that i'll post the link.


Can't remember if this is it or not:  [http://www.linux-books.us/linux_general_0003.php](http://www.linux-books.us/linux_general_0003.php)

note it will be about linux in general.

the link works & that's what i need to begin to learn...

---

### Post by DuckHook on 2012-11-22
> **Steve J said:**
> is there something like "Ubunto for Dummies" online?

For Ubuntu specifically,

[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

For the Linux command line, there are numerous resources. The sticky at the top of this forum points to a great collection at:

[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

---

### Post by wildmanne39 on 2012-11-22
Hi, time to get this thread back on topic to wireless issues.
Thanks

---

### Post by realarvo on 2012-11-28
Hi Folks,

So what happened there? I have what sounds like the same problem (Dell M90, Broadcom WiFi and Ubuntu 12.04)

Is it possible to summarise the bits of that, that did the trick?

Many thanks

Arvo

---

### Post by wildmanne39 on 2012-11-28
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by realarvo on 2012-11-28
Okey dokey.

There was this:

```
#!/bin/bash
#Script created by anewguy, tested by chili555 and edited by krytarik, llua and wildmanne39
exec > netinfo.txt 2> /dev/null
echo -e "\n*************** info trace ****************\n"
echo -e "\n\n**** uname -a ****\n\n"
uname -a
echo -e "\n\n**** lsb-release ****\n\n"
cat /etc/lsb-release
echo -e "\n\n**** lspci ****\n\n"
lspci -nnk | grep -iA2 net
echo -e "\n\n**** lsusb ****\n\n"
lsusb
echo -e "\n\n**** iwconfig ****\n\n"
iwconfig
echo -e "\n\n**** rfkill ****\n\n"
rfkill list all
echo -e "\n\n**** lsmod ****\n\n"
lsmod
echo -e "\n\n**** nm-tool ****\n\n"
nm-tool
echo -e "\n\n**** NetworkManager.state ****\n\n"
cat /var/lib/NetworkManager/NetworkManager.state
echo -e "\n\n**** NetworkManager.conf ****\n\n"
cat /etc/NetworkManager/NetworkManager.conf
echo -e "\n\n**** NetworkManager.conf-10.04 ****\n\n"
cat /etc/NetworkManager/nm-system-settings.conf
echo -e "\n\n**** interfaces ****\n\n"
cat /etc/network/interfaces | sed 's/wpa-psk [[:graph:]:]\+/wpa-psk <WPA key removed>/'
echo -e "\n\n**** iwlist ****\n\n"
[ -t 0 ] && sudo iwlist scan
[ ! -t 0 ] && gksudo iwlist scan
echo -e "\n\n**** resolv ****\n\n"
cat /etc/resolv.conf
echo -e "\n\n**** blacklist.conf ****\n\n"
cat /etc/modprobe.d/blacklist.conf
echo -e "\n\n**** dmesg ****\n\n"
dmesg | egrep 'air|ath|carl|at7|iwl|ipw|rtl8|rt2|rt3|rt6|rt7|r818|r871|rtl8|tg3|ssb|wl|b43|bcma|brcm|b44|eth1|ndis|wmi|wlan0'
echo -e "\n\n**************** done ********************\n\n"
sed -i 's/\([[:alnum:]][[:alnum:]]:\)\{5\}[[:alnum:]][[:alnum:]]/<MAC address removed>/' netinfo.txt
```


And this:


```
*************** info trace ****************



**** uname -a ****


Linux arvo-Precision-M90 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 i686 i386 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"


**** lspci ****


09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
	Subsystem: Dell Device [1028:01cf]
	Kernel driver in use: tg3
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
	Kernel modules: wl, ssb


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 002 Device 003: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 002 Device 004: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 001 Device 003: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 001 Device 004: ID 04f9:018c Brother Industries, Ltd DCP-115C


**** iwconfig ****




**** rfkill ****


0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no


**** lsmod ****


Module                  Size  Used by
usblp                  17885  0 
usb_storage            39646  0 
vesafb                 13516  1 
rfcomm                 38139  0 
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
nvidia              10962290  42 
joydev                 17393  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_hda_codec_idt      60251  1 
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
video                  19068  0 
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
mac_hid                13077  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
r592                   17808  0 
r852                   17901  0 
wmi                    18744  1 dell_wmi
sm_common              16737  1 r852
nand                   49667  2 r852,sm_common
nand_ids                8547  1 nand
mtd                    35584  2 sm_common,nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
memstick               15857  1 r592
wl                   2646601  0 
soundcore              14635  1 snd
psmouse                86486  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lib80211               14040  1 wl
serio_raw              13027  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
tg3                   141369  0 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.9
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****



[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****




**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


**** dmesg ****


[    1.145498] tg3.c:v3.121 (November 2, 2011)
[    1.145518] tg3 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.145530] tg3 0000:09:00.0: setting latency timer to 64
[    1.176559] tg3 0000:09:00.0: eth0: Tigon3 [partno(BCM5752KFBG) rev 6002] (PCI Express) MAC address <MAC address removed>
[    1.176563] tg3 0000:09:00.0: eth0: attached PHY is 5752 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.176567] tg3 0000:09:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.176570] tg3 0000:09:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   14.054860] wl: module license 'MIXED/Proprietary' taints kernel.
[   14.090824] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.090834] wl 0000:0c:00.0: setting latency timer to 64
[   14.124143] wmi: Mapper loaded
[   15.868688] type=1400 audit(1354124805.523:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=818 comm="apparmor_parser"
[   16.188000] tg3 0000:09:00.0: irq 46 for MSI/MSI-X
[   17.889477] tg3 0000:09:00.0: eth0: Link is up at 100 Mbps, full duplex
[   17.889481] tg3 0000:09:00.0: eth0: Flow control is off for TX and off for RX


**************** done ********************
```

Sorry about the length there but I couldn't get the paper clip attach-y thing to work :(

---

### Post by audiomick on 2012-11-28
> **realarvo said:**
> 
Sorry about the length there but I couldn't get the paper clip attach-y thing to work :(

You can use the # button at the top of the post window to put code tags around long output like that. Click on it, and put the text [noparse] ```
 here 
``` [/noparse] to put it in

```
a nice box like this
that puts a scroll bar
on the side if the text is too long
```

That also has the advantage that the text is shown literally without having something like this
```
some numbers (5, 6, 6, 8)
``` turn into this
some numbers (5, 6, 6, 8)

---

### Post by wildmanne39 on 2012-11-28
Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
```
sudo modprobe b43
```
Thanks

---

### Post by realarvo on 2012-11-28
> **Wild Man said:**
> Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
```
sudo modprobe b43
```
Thanks

Man you rock! :guitar:

So to backtrack a little for a numpty, what we did there was delete all the old drivers, install a new one and check that happened?

Fantastic.

Thanks so much

realarvo

---

### Post by realarvo on 2012-11-28
> **audiomick said:**
> You can use the # button at the top of the post window to put code tags around long output like that. Click on it, and put the text [noparse] ```
 here 
``` [/noparse] to put it in

```
a nice box like this
that puts a scroll bar
on the side if the text is too long
```

That also has the advantage that the text is shown literally without having something like this
```
some numbers (5, 6, 6, 8)
``` turn into this
some numbers (5, 6, 6, 8)

Thanks audiomick! Will try and be less of a numpty henceforth :)

Will likely be back a few times if I get stuck over the next day or so as I've just upgraded to 10.04 by completely rewriting my HD and removing a winxp partition!

Cheers all

realarvo

---

### Post by wildmanne39 on 2012-11-28
Your welcome! glad to help.
Enjoy

---

