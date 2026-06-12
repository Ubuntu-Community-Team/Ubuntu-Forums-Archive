---
title: "Trying to get my wireless to work"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by trestamanos on 2008-09-15
administrator@administrator-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
**0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)**


----------------------------------------

administrator@administrator-laptop:~$ sudo aptitude install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  comerr-dev gettext-kde hspell kdelibs4-dev kdesdk-scripts libacl1-dev 
  libart-2.0-dev libarts1-dev libartsc0-dev libasound2-dev libaspell-dev 
  libattr1-dev libaudio-dev libaudiofile-dev libavahi-client-dev 
  libavahi-common-dev libavahi-qt3-dev libbz2-dev libcupsys2-dev 
  libdbus-1-dev libdbus-glib-1-dev libesd0-dev libexpat1-dev 
  libfontconfig1-dev libfreetype6-dev libgcrypt11-dev libgl1-mesa-dev 
  libglib2.0-dev libglu1-mesa-dev libgnutls-dev libgnutlsxx13 
  libgpg-error-dev libice-dev libidn11-dev libjasper-dev libjpeg62-dev 
  libkadm55 libkcal2b libkdepim1-dev libkdepim1a libkrb5-dev libktnef1 
  liblcms1-dev liblua50-dev liblualib50-dev liblzo2-dev libmng-dev 
  libnm-util-dev libogg-dev libopencdk10-dev libopenexr-dev libpcre3-dev 
  libpcrecpp0 libpng12-dev libpthread-stubs0 libpthread-stubs0-dev 
  libqt3-headers libqt3-mt-dev libsasl2-dev libsm-dev libssl-dev 
  libtasn1-3-dev libtiff4-dev libtiffxx0c2 libvorbis-dev libx11-dev 
  libxau-dev libxcb-xlib0-dev libxcb1-dev libxcursor-dev libxdmcp-dev 
  libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev 
  libxml2-dev libxmu-dev libxmu-headers libxrandr-dev libxrender-dev 
  libxslt1-dev libxt-dev lua50 mesa-common-dev qt3-dev-tools 
  x11proto-core-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev 
  x11proto-randr-dev x11proto-render-dev x11proto-xext-dev 
  x11proto-xinerama-dev xtrans-dev zlib1g-dev 
The following NEW packages will be automatically installed:
  ndiswrapper-common 
The following NEW packages will be installed:
  ndiswrapper-common ndiswrapper-utils-1.9 
0 packages upgraded, 2 newly installed, 96 to remove and 0 not upgraded.
Need to get 0B/38.3kB of archives. After unpacking 105MB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Media Change: Please insert the disc labeled 'Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)' in the drive '/cdrom/' and press [Enter].

----------------------

Where can i get this disk?

Im trying really hard to leave windows....but i need wireless for my laptop.:)

---

### Post by NullHead on 2008-09-15
Just use the device manager to install the driver. Use it through the menu system like so: System>Administration>Hardware Drivers. 

Your device should be listed in there.

---

### Post by vikramaditya on 2008-09-15
I'm no good with network manager, but a lot of folks report success with wicd.  You can install it from synaptic or terminal.

EDIT:  Sorry, I just saw the line about inserting the disc.  Did you not install ubuntu from a downloaded disc image?

---

