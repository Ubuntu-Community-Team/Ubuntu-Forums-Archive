---
title: "Netgear WG111v2 in 8.04 - noob hitting a brick wall"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by puyanera on 2008-07-29
Hi,

I'm new to Ubuntu and I like the os so far but im having trouble getting my Netgear WG111v2 to work with it.

I followed the instructions in this thread

[http://ubuntuforums.org/showthread.php?t=615568&highlight=wg111](http://ubuntuforums.org/showthread.php?t=615568&highlight=wg111)

and am almost there but i seem to have hit a brick wall and have no idea where to turn to now.

I have installed ndiswrapper,ndiswrapper utils and ndisgtk. I installed the drivers and ndisgtk can see them and it can see my hardware. I can also see the wirless networks that are available. When i try and connect though i don't seem to get any love.

When I type lsusb i get 0846:6a00 as the usbid.

I'm using wpa pre-shared key. And i definitely have the passphrase correct as i can connect with my windows laptop easily enough.

Any ideas and any help at all would be much appreciated.

---

### Post by Haioko on 2008-07-29
I had the EXACT same problem with the EXACT same Netgear device.

Do you know how to access your router's settings?

---

### Post by puyanera on 2008-07-29
Yep, i know how to access the router

---

### Post by Haioko on 2008-07-29
Ok well check the router's IP and the system which has the USB device attached's IP

There should only be two if you only have one computer attached to the router.

It might be 192.168.1.1 for the router and 192.168.1.4 for the PC.

---

### Post by puyanera on 2008-07-29
The ip of the router is 192.168.1.1 although i'm not sure how to check the ip address of the ubuntu system.

---

### Post by Haioko on 2008-07-29
We'll try 192.168.1.4 if it's the same as my setup it should be. Either that or it's 192.168.1.2

Ok go into System > Admin > Network

And click on the wireless connection and go into it's properties.

Change all the Appropriate data

Network Name (ESSID): <Whatever you called your network>
Password Type: WPA Personal
Network Passcode: <Your passcode>

Change the configuration to 'Static IP address'
IP Address: 192.168.1.2 or 192.168.1.4
Subnet Mask: 255.255.255.0 or 255.0.0.0
Gateway Address: 192.168.1.1

Try changing it to that and tell me what happens =]

---

### Post by puyanera on 2008-07-29
ok i tried changing all that but looks like internet still not working.

Do i need to change the setup on the router so that it's static ip address as well? I currently have it set to DHCP

---

### Post by Haioko on 2008-07-29
Yeah try changing that,

---

### Post by puyanera on 2008-07-29
Ok tried that but still nothing.

I'm not getting any errors or anything like that unfortunately. Just seems to be nothing happening at all when I connect.

---

### Post by Saghaulor on 2008-08-03
I can't find the thread I'd like to link you to, so I'm just going to copy and paste the content(I cached the page to my hard disk) and give credit to its author, namely, Kevdog.

So here is Kevdog's post which I have found extremely useful.

>  How To: Manual Network Configuration without the need for Network Manager
In setting up their wireless connection for the first time, Im discovering many individuals having problems connecting through Network Manager or other GUI wireless connection tools. In fact my Network Manager is intermittently buggy, connecting sometimes and not others. This guide benefits all users in case the GUI tools are not working, and is useful for testing a wireless connection during initial installation of wireless drivers since it provides for good debugging output.

Unencrypted/ WEP / WPA connections will be covered in this guide.
This guide is for anyone attempting to establish a network connection manually at the command line.

Pre-requisites
1. Properly installed network driver -- This guide can be used to troubleshoot driver installation to see if it is properly functioning
2. The ESSID of your router must be broadcasted and not hidden
3. Knowlege of your wireless cards driver (please see Prerequisite #4 to determine driver). Those using the r8187/r818x driver please see the end of the guide
4. Knowledge of your wireless card's Interface Name - The user must know the proper interface of the wireless connection (wlan0, eth1, rausb1, etc). To discover this information, at command line type:

Code:

lshw -C network

There may be multiple interfaces listed, however look under the section appropriate to your wireless device for the line labeled logical name. Here is an example:

Code:

  *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       logical name: wlan0
       version: 03
       serial: 00:12:17:35:17:10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lsbcmnds driverversion=1.48rc1+Cisco-Linksys ,LLC.,02/1 ip=192.168.1.101 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c001fff irq:11

In the example above the interface name is wlan0. I will refer to the interface name throughout the rest of this guide as <interface>.

For people first setting up their connection, please note that the above also lists the driver used for the network card. In the example above, the driver used is ndiswrapper. If your network device comes back UNCLAIMED or there is no driver listed, then you have not correctly installed the driver for your device. You must review the procedures for installation of your wireless driver.

For those wanting to use static IP addresses, please see section at bottom of guide regarding configuration for static IP addresses

__________________________________________________ __________________________
Unencrypted Connection

All commands typed at the command line:
Code:

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>

__________________________________________________ __________________________
WEP Connection

You must have either your 64bit or 128 bit HEX Key or the ASCII Equivalent of your HEX Key.

Code:

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> key HEX_KEY <<<-------- If using ASCII Equivalent, this is s:ASCII_KEY (please make note of the prefix s:)
****Additional Comand that may be needed  -- sudo iwconfig <interface> key open  <<<----See note below
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>

***The security mode may be open or restricted, and its meaning depends on the card used. With most cards, in open mode no authentication is used and the card may also accept non-encrypted sessions, whereas in restricted mode only encrypted sessions are accepted and the card will use authentication if available.
__________________________________________________ __________________________
WPA Connection - WPA-PSK or WPA2-PSK

For uses of Ra-based chipsets: rt61, rt73, rt2500 please skip directly to the WPA Section entitled WPA with Ra based chipsets

Requirements: In most cases the wpa_supplicant package is required in order to connect via WPA. If you have a working ethernet or unencrypted/WEP wireless connection, this package may be installed via:
Code:

sudo aptitude install wpasupplicant

If only wireless is available, I would recommend that an unencrypted connection first by established and tested first before directly proceeding to make a WPA connection. WPA adds another layer of complexity.

1. Creation of /etc/wpa_supplicant.conf file

At command line:
Code:

gksu gedit /etc/wpa_supplicant.conf

Inside the file add the following for WPA(1):

Code:

ap_scan=1
ctrl_interface=/var/run/wpa_supplicant 

network={
        ssid="ESSID_IN_QUOTES"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="ASCII PSK Password in Quotes"
        pairwise=TKIP
        group=TKIP
}

For WPA(2) (see this thread: [http://ubuntuforums.org/showthread.php?t=607410):](http://ubuntuforums.org/showthread.php?t=607410):)
Code:

ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="ESSID_IN_QUOTES"
        psk="ASCII PSK Password in Quotes"
        key_mgmt=WPA-PSK
        proto=RSN
        pairwise=CCMP
}

***Word of caution -- In some cases I have found WPA(2) to have different settings than the above. Some Broadcom cards use the pairwise/group TKIP cipher for WPA2 rather than CCMP. I would suggest all initially use WPA(1) and then later convert to WPA2 since some variations to the above may be needed

2. Connect via command line
Code:

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo wpa_supplicant -w -D<****see footer below***> -i<interface> -c/etc/wpa_supplicant.conf -dd 
sudo ifconfig <interface> up
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>

***footer
The value listed here is dependent on the driver you have installed. Typing man wpa_supplicant at command line will give you the full gamut of choices however a quick reference
ndiswrapper=wext (use wext and not ndiswrapper despite what documentation might suggest)
ath_pci = madwifi
ipw2100/2200=ipw

WPA with Ra Based Chipsets

Ra cards do not require the wpa_supplicant package to use WPA. Here is how to connect from the command line with these cards:
References: [http://ubuntuforums.org/showthread.p...=serial+monkey](http://ubuntuforums.org/showthread.p...=serial+monkey), [http://rt2x00.serialmonkey.com/wiki/...owto#Using_WPA](http://rt2x00.serialmonkey.com/wiki/...owto#Using_WPA)

WPA(1)
Code:

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <inteface> essid "ESSID_IN_QUOTES"
sudo iwpriv <interface> set AuthMode=WPAPSK
sudo iwpriv <interface> set EncrypType=TKIP
sudo iwpriv <interface> set WPAPSK="YOUR_WPA_PSK_KEY"
sudo dhclient <interface>

For WPA(2), I have no working configuration yet. If someone would like to help me refine these instructions for WPA2 with Ra-based chipsets, I would appreciate your help!

__________________________________________________ __________________________
A successful connection in all cases will results in this:
Code:

user@computer:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:12:17:35:17:10
Sending on   LPF/wlan0/00:12:17:35:17:10
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.1.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.101 -- renewal in 299133 seconds.

The computer in this example has received an IP address of 192.168.1.101

__________________________________________________ __________________________
Users of RTL 8180, RTL8185, RTL 8187 using the built in native r8187 / r818x drivers

By default the r8187 and r818x drivers are blacklisted due to a know bug. These drivers are usuable however with a twist to the above methods

If you want to try using these drivers, please load the kernel modules:
Code:

sudo modprobe r818x
sudo modprobe r8187

These drivers require a bogus or extra letter be suffixed to the essid name in order for these drivers to work
For example if your are trying to connect to a router with essid=Router, at he command line you would type essid=Routerx. Notice the extra x or bogus character. I have provided an example using the unencrypted connection procedure below, however this extra character needs to be used if attempting to connect to all network types (unencrypted/ WEP / WPA)

Code:

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "Routerx"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>

If these drivers work for you, and you would like these drivers to load automatically at startup for you, avoiding to have to type sudo modprobe everytime, please edit your blacklist file:

Code:

gksu gedit /etc/modprobe.d/blacklist

And comment out (or prefix the following lines with a # sign). You want the following lines to appear as below:
Code:

#blacklist r8187
#blacklist r818x


__________________________________________________ __________________________
Static IP Addresses

Im going to give an example of how to configure your interface using a static IP address using an unencrypted wireless connection. The two lines highlighted below however can be used with WEP and WPA connections. Values in italics must be customized to meet your particular situation

Code:

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> 192.168.1.100 netmask 255.255.255.0 up
sudo route add default gw 192.168.1.1
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>

If when using static IP addresses you are getting a problem with name resolution, you will have to specifiy specific dns (domain name servers) in order to translate URLs to IP addresses. Unfortunately there is not an easy way to configure this from the command line. This requires that you edit the /etc/resolv.conf file and manually enter the domain name server(s) you want to use. In many cases users can specifiy their router, their internet service providers dns servers, or use opendns (or use all three). Please note that changes made to the /etc/resolv.conf file will not be retained between reboots. To make the nameservers permanent, the /etc/dhcp3/dhclient.conf file needs to be edited as instructed here: [http://ubuntuforums.org/showthread.php?t=282034](http://ubuntuforums.org/showthread.php?t=282034)

Code:

sudo gedit /etc/resolv.conf

and add the nameservers you want to use, one to a line, in the following format.
Code:

nameserver <nameserver>

You can add as many as you want but most isps normally provide two (primary and secondary).

__________________________________________________ __________________________
Setting the Wireless Interface to Connect at Boot ***Courtesy of Maricaibo

If you are successful in bringing up the Interface Manually, the commands may be placed inside the /etc/rc.local file to run the commands at boot, and establish a wireless connection. There is no GUI to give visual confirmation of the connection. The user should type ifconfig at the command line to verify an IP address has indeed been granted by the router.

The process of adding the commands to the /etc/rc.local file is documented below (this connects to an unencrypted network -- to connect to a WEP or WPA encrypted network, some modifications as used above will need to be added):


Code:

gksu gedit /etc/rc.local

This opens up the file in the gedit utility and allows you to make changes and save the file

Code:

ifconfig <wired network connection interface> down
ifconfig <wireless network connection interface> down
dhclient -r <wireless_interface>
iwconfig <wireless_interface> essid <router name>
iwconfig <wireless_interface> mode Managed
ifconfig <wireless_interface> up
dhclient <wireless_interface>

Be sure this text goes into the /etc/rc.local file BEFORE the line reading "exit 0".

Save and close the /etc/rc.local file.

Open up a Terminal window (the shell) and type in:

Code:

sudo chmod +x /etc/rc.local

This command turns the rc.local file into an executable that will run at startup. Here's an example of what the /etc/rc.local file should contain. Your device names may be different:

Code:

#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

ifconfig eth0 down
ifconfig wlan0 down
dhclient -r wlan0
iwconfig wlan0 essid "ESSID_IN_QUOTES"
iwconfig wlan0 mode Managed
ifconfig wlan0 up
dhclient wlan0

exit 0

NOTE: The first line in the rc.local file downs your wired connection, so if for some reason you need the wired connection back just open up a Terminal window (shell) and type:

sudo <wired_interface> up
sudo dhclient <wired_interface>
__________________________________________________ __________________________
Useful Commands

ifconfig - lists IP address (similar to ipconfig in Windows)
iwlist scan - shows wireless networks that are available in the area along with basic encryption information
lshw -C network - Shows interface and driver associated with each networking device
lspci -nn - Shows hardware connected to the pci bus
lsusb - Shows USB connected hardware
lshw -C usb - Additional info on USB related hardware (good for USB dongles)
cat /etc/modprobe.d/blacklist - List modules that will not be loaded by the Operating System at boot time
lsmod - lists currently loaded kernel modules. (Example usage - lsmod | grep ndiswrapper)
route -n - Lists kernel IP routing table -- Good for troubleshooting problems with the gateway (netstat -rn = equivalent command)
sudo route add default gw 192.168.1.1 - Example of how to set the default gateway to 192.168.1.1
sudo route del default gw 192.168.1.1 - Example of how to delete the default gateway setting
sudo modprobe ***** - Loads the kernel module **** . (Example usage - sudo modprobe ndiswrapper, sudo modprobe r818x, sudo modprobe ath_pci)
sudo modprobe -r **** - Unloades the kernel module ****. (Example usage - sudo modprobe -r ndiswrapper)
sudo ifup/ifdown <interface> - Brings up/down the interface and clears the routing table for the specified interface
sudo ifconfig <interface> up/down - Brings up/down the interface for the specified interface
sudo dhclient <interface> - Request IP address from DNS server for specified interface
sudo dhclient -r <interface> - Release IP address associated with specified interface
sudo iptables -L - Lists firewall rules
dmesg | more - Lists boot log -- good for troubleshooting problems with modules/drivers not being loaded
uname -r - Displays kernel version
/etc/iftab (Feisty and pre-releases (Edgy, etc)) - /etc/udev/rules.d/70-persistent-net.rules (Gutsy) - File which assigns logical names (eth0, wlan0, etc) to MAC addresses
cat /etc/resolv.conf - Lists DNS servers associated with network connections (Network Manager)
/etc/dhcp3/dhclient.conf - File which sets or modifies dns (domain name servers) settings

Further references:
Official Broadcom site for bcm43xx firmware - [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
Broadcom 64bit Drivers for Use with Ndiswrapper - [http://www.linuxant.com/driverloader/drivers.php](http://www.linuxant.com/driverloader/drivers.php)
Ra chipsets - Serial Monkey Drivers - rt2500, rt73, rt61, rt2570 drivers - [http://ubuntuforums.org/showthread.p...=serial+monkey](http://ubuntuforums.org/showthread.p...=serial+monkey) - Author diepruis
Rutilt - A Network Manager Like GUI for Ra Chipsets - [http://ubuntuforums.org/showthread.p...ghlight=rutilt](http://ubuntuforums.org/showthread.p...ghlight=rutilt) - Author sulilogs
Ndiswrapper installation for Broadcom chipsets - [http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963) - Author Jamie Jackson
Ndiswrapper General Installation Guide - SVN, Troubleshooting Tips (My Personal Guide) - [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501) - Author KevDog
Madwifi website for certain Atheros Chipsets - [http://madwifi.org/](http://madwifi.org/) -- If your Atheros chipset is listed on this website - it should work out of the box with installation of the linux restricted drivers package for your kernel version
Does your madwifi connection keep dropping??? Possible solution -- [http://ubuntuforums.org/showthread.php?t=540101](http://ubuntuforums.org/showthread.php?t=540101) = Author robnz/tranalbert
Realtek win98 driver - [http://www.majorgeeks.com/Realtek_RT...0XP_d5165.html](http://www.majorgeeks.com/Realtek_RT...0XP_d5165.html) - For use with ndiswrapper if native r818x, r8187 driver is buggy
Realtek win98 driver installation - [http://ubuntuforums.org/showthread.p...highlight=8187](http://ubuntuforums.org/showthread.p...highlight=8187) - Author Panurge
Realtek - Installation with Native Driver - [http://ubuntuforums.org/showthread.php?t=567505](http://ubuntuforums.org/showthread.php?t=567505)
DNS related problems?? - Configuration for OpenDNS servers - [http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659) - Author noob12
Turn off/Disable IPv6 - [http://ubuntuforums.org/showthread.php?t=282034](http://ubuntuforums.org/showthread.php?t=282034) - Author handy
General Linux Page Discussing Network Setups - Default Gateways - [http://linux-ip.net/html/basic-changing.html](http://linux-ip.net/html/basic-changing.html)
Log Files -- Your Friend to Debug almost anything on your System - [https://help.ubuntu.com/community/Li...f98267e009db55](https://help.ubuntu.com/community/Li...f98267e009db55)

Other things Linux
Control Programs Kept in Swap vs Memory - [http://ubuntuforums.org/showpost.php...&postcount=150](http://ubuntuforums.org/showpost.php...&postcount=150)
Realtek 8187B Native Patch for Realtek 818x USB Devices -- Relevant only to USB wireless devices - [http://www.datanorth.net/~cuervo/rtl8187b/](http://www.datanorth.net/~cuervo/rtl8187b/) - Author Cuervo
If your Wireless Freezes after Suspend/Resume - Check here - [http://ubuntuforums.org/showpost.php...7&postcount=12](http://ubuntuforums.org/showpost.php...7&postcount=12) - Author Harty83

I must apologize, as the formatting from Kevdog's original post has been corrupted when it copied and pasted. Anyways, some of these commands are very helpful.

---

### Post by Techboy on 2008-08-03
Perfect!  Gets my card working FINALLY!  

Now a next question:  If I've done that editing manually to get it to connect to my WEP'd system at home, do I have to edit it again when I go to the outside world to open connections?

I'm using a Cisco AIR-CB21AG-A-K9 card in a Lenovo T61 laptop.  Atheros drivers are showing as active in Restricted Drivers.  Network Manager doesn't even show the interface.  I tried WICD (which had worked previously, but mysteriously stopped).  But the command line changes have me running.

---

