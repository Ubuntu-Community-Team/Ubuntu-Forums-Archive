---
title: "How to set up the DWL G630 D. under Ubuntu/Windows"
date: 2006-05-15
forum: Outdated Tutorials &amp; Tips
---

### Post by Z3r0- on 2006-05-15
The AR5005G (AR5212) chipset is a wlan (wireless local area network) chipset which is compliant with wireless standards 802.11 b/g

This page provides information about how where to find drivers and how to set up Windows XP or Ubuntu Linux Dapper with the AR5005G (AR5212) chipset

There are a vast amount of wireless lan manufacturers who include the AR5005G as the main chip in their wlan cards and resell it, for instance the D-Link DWL G630 Rev C & D. (Australia) a PC-card for Laptops is based on this chip.

D-Link haven't updated their buggy drivers in a while so it was necessary to find new drivers from the chipset manufacturer

The latest windows drivers for the Atheros chipset can be found here (4.2.2.14):

Don't worry they are English!

[http://www.fmworld.net/cgi-bin/driversearch/drvdownload.cgi?DRIVER_NUM=E1003096](http://www.fmworld.net/cgi-bin/driversearch/drvdownload.cgi?DRIVER_NUM=E1003096)

The latest drivers for Linux are included with ubuntu dapper

Index
1 Connecting to a router under Windows XP with WPA/WPA2
2 Connecting to a router under Ubuntu Linux with WPA/WPA2

1 Connecting to a router under Windows XP
--------------------------------------------------------

These instructions are for the gigabyte utility which as smart setup, the newer drivers haven't been customised to include smart setup by the other manufacturer

For connecting directly to a adsl/cable wireless router

Firstly install the AR5005G drivers above.

After installing, reboot, go to control panel -> network connections, if you can't see your wireless card in the control panel go to system settings and install drivers manually

Run the home networking wizard to correctly configure your card, if connecting through a router you can choose other -> this computer connects to the internet directly through a hub, other computers on my network connect directly through this hub

Your wireless card will now be assigned an IP address by the router using DHCP

Now we must configure the card correctly,

Go to control panel -> network connections -> right click on the wireless adapter -> go to properties -> configure

For the AR5005G you have these options
802.11b Preamble -> Long and Short
Map registers -> 256
Network Address -> Not present
Power Save Mode -> Normal
Radio On/Off -> On
Scan Valid Interval -> 60

Now go to the system tray -> right click on atheros icon -> Open Gigabyte client utilty

Click on smart setup 3 -> The wireless access point should appear, click ok

Set up a profile name then go to advanced
Transmit power level -> 100% #once again lower power may be better for a laptop and won't cause much speed decrease at close range
Power Save Mode -> Normal #set to normal so that it comes out of powersaving mode for large file sizes and transfers faster but then goes back to max power saving mode
Network Type -> Infrastructure
802.11b preamble -> long & short
Wireless mode -> Tick 2.4Ghz 54Mbps & Extended range #you can check or uncheck 11Mbps, doesn't matter
QoS -> tick #why not?


WPA can be set up quite simply go to Security tab and set it up there

I suggest WPA2 with AES




2 Connecting to a router under Ubuntu Linux with WPA/WPA2
------------------------------------------------------------------------------

This is pretty straightforward, sometimes the card isn't detected under linux, if you do dmesg | grep ath and can't see anything that means the device wasn't detected (as the madwifi drivers come with ubuntu)

The CPU was unable to access the PCI bus of the PC Card.

open a terminal and become superuser with su

You can resolve this by: 

editing the grub bootloader options by sudo gedit /boot/grub/menu.lst and adding pci=assign-busses to the following line as so 

kernel /boot/vmlinuz-2.6.15-20-386 root=/dev/hda2 ro quiet splash vga=0x323 pci=assign-busses

reboot

The lights on the device now alternate as it has been detected by linux and drivers loaded

set up your card under the ubuntu network connection manager and allow it to be configured by DHCP 

to set up WPA you need to do
wpa_passphrase myrouter my63letterpasswordhere > /home/%user%/a.txt
wpa_supplicant -B -Dmadwifi -iath0 -c/home/%user%/a.txt
dhclient

To get the card to work at bootup do this

gedit /etc/rc.local &

add wpa_supplicant -B -Dmadwifi -iath0 -c/home/%user%/a.txt

add dhclient ath0

---

