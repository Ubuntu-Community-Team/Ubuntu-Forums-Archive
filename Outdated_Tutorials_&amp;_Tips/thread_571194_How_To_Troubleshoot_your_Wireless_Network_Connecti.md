---
title: "How To: Troubleshoot your Wireless Network Connection - Connecting  at Command Line"
date: 2007-10-09
forum: Outdated Tutorials &amp; Tips
---

### Post by kevdog on 2007-10-09
In setting up their wireless connection for the first time, Im discovering many individuals having problems connecting through Network Manager or other GUI wireless connection tools.  In fact my Network Manager is intermittently buggy, connecting sometimes and not others.   This guide benefits all users in case the GUI tools are not working, and is useful for testing a wireless connection during initial installation of wireless drivers since it provides for good debugging output.

[SIZE="3"]**Unencrypted/ WEP / WPA connections will be covered in this guide.**[/SIZE]
[SIZE="2"]**This guide is for anyone attempting to establish a network connection manually at the command line. **[/SIZE] 

**Pre-requisites**
1. Properly installed network driver -- This guide can be used to troubleshoot driver installation to see if it is properly functioning
2. The ESSID of your router must be broadcasted and not hidden
3. Knowlege of your wireless cards driver (please see Prerequisite #4 to determine driver).  [SIZE="2"]**Those using the r8187/r818x driver please see the end of the guide**[/SIZE]
4. Knowledge of your wireless card's Interface Name - The user must know the proper interface of the wireless connection (wlan0, eth1, rausb1, etc).  To discover this information, at command line type:

```
lshw -C network
```

There may be multiple interfaces listed, however look under the section appropriate to your wireless device for the line labeled logical name.  Here is an example:

```

  *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       **[SIZE="2"]logical name: wlan0[/SIZE]**
       version: 03
       serial: 00:12:17:35:17:10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **[SIZE="2"]driver=ndiswrapper+lsbcmnds[/SIZE]** driverversion=1.48rc1+Cisco-Linksys ,LLC.,02/1 ip=192.168.1.101 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c001fff irq:11

```
 
In the example above the interface name is wlan0.  **[SIZE="2"]I will refer to the interface name throughout the rest of this guide as <interface>.[/SIZE]** 

For people first setting up their connection, please note that the above also lists the driver used for the network card.  In the example above, the driver used is ndiswrapper.  [SIZE="2"]**If your network device comes back UNCLAIMED or there is no driver listed, then you have not correctly installed the driver for your device.**[/SIZE]  You must review the procedures for installation of your wireless driver.

____________________________________________________________________________
[SIZE="4"]**Unencrypted Connection**[/SIZE]

All commands typed at the command line:
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>
```

____________________________________________________________________________
[SIZE="4"]**WEP Connection**[/SIZE]

You must have either your 64bit or 128 bit HEX Key or the ASCII Equivalent of your HEX Key.

```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> key HEX_KEY <<<-------- If using ASCII Equivalent, this is s:ASCII_KEY (please make note of the prefix s:)
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>
```

____________________________________________________________________________
[SIZE="4"]**WPA Connection  - WPA-PSK or WPA2-PSK**[/SIZE]

Requirements: In most cases the wpa_supplicant package is required in order to connect via WPA.  If you have a working ethernet or unencrypted/WEP wireless connection, this package may be installed via:
```
sudo aptitude install wpasupplicant
```

If only wireless is available, I would recommend that an unencrypted connection first by established and tested first before directly proceeding to make a WPA connection.  WPA adds another layer of complexity.

1. Creation of /etc/wpa_supplicant.conf file

At command line:
```
gksu gedit /etc/wpa_supplicant.conf
```

Inside the file add the following for WPA(1):

```
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
```

For WPA(2):
```
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant 

network={
        ssid="ESSID_IN_QUOTES"
        scan_ssid=0
        proto=WPA
        key_mgmt=RSN
        psk="ASCII PSK Password in Quotes"
        pairwise=TKIP CCMP
        group=TKIP CCMP
}
```

***Word of caution -- In some cases I have found WPA(2) to have different settings than the above.  Some Broadcom cards use the pairwise/group TKIP cipher for WPA2 rather than CCMP.  **I would suggest all initially use WPA(1)** and then later convert to WPA2 since some variations to the above may be needed

2. Connect via command line
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo wpa_supplicant -w -D<****see footer below***> -i<interface> -c/etc/wpa_supplicant.conf -dd 
sudo ifconfig <interface> up
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>

```

***footer
The value listed here is dependent on the driver you have installed.  Typing man wpa_supplicant at command line will give you the full gamut of choices however a quick reference
ndiswrapper=wext  (use wext and not ndiswrapper despite what documentation might suggest)
ath_pci = madwifi
ipw2100/2200=ipw

____________________________________________________________________________
**[SIZE="4"]A successful connection in all cases will results in this[/SIZE]**:
```
user@computer:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

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
```

The computer in this example has received an IP address of 192.168.1.101

____________________________________________________________________________
[SIZE="3"]** Users of RTL 8180, RTL8185, RTL 8187 using the built in native r8187 / r818x drivers **[/SIZE]

By default the r8187 and r818x drivers are blacklisted due to a know bug.  These drivers are usuable however with a twist to the above methods

If you want to try using these drivers, please load the kernel modules:
```

sudo modprobe r818x
sudo modprobe r8187

```

**[SIZE="2"]These drivers require a bogus or extra letter be suffixed to the essid name in order for these drivers to work**[/SIZE]
For example if your are trying to connect to a router with essid=Router, at he command line you would type essid=Routerx.  Notice the extra x or bogus character.  I have provided an example using the unencrypted connection procedure below, however this extra character needs to be used if attempting to connect to all network types (unencrypted/ WEP / WPA)

```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "Routerx"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>
```

If these drivers work for you, and you would like these drivers to load automatically at startup for you, avoiding to have to type sudo modprobe everytime, please edit your blacklist file:

```

gksu gedit /etc/modprobe.d/blacklist

```

And comment out (or prefix the following lines with a # sign).  You want the following lines to appear as below:
```

#blacklist r8187
#blacklist r818x 

```

____________________________________________________________________________
[SIZE="3"]** Useful Commands **[/SIZE]

**ifconfig** - lists IP address (similar to ipconfig in Windows)
**iwlist scan** - shows wireless networks that are available in the area along with basic encryption information
**lshw -C network** - Shows interface and driver associated with each networking device
**lspci -nn** - Shows hardware connected to the pci bus
**lsusb** - Shows USB connected hardware
**lshw -C usb** - Additional info on USB related hardware (good for USB dongles)
**cat /etc/modprobe.d/blacklist** - List modules that will not be loaded by the Operating System at boot time
**lsmod** - lists currently loaded kernel modules.  (Example usage - lsmod | grep ndiswrapper)
**route -n** - Lists kernel IP routing table -- Good for troubleshooting problems with the gateway
**cat /etc/resolve.conf** - Lists DNS servers associated with network connections
**sudo modprobe ******* - Loads the kernel module **** .  (Example usage - sudo modprobe ndiswrapper, sudo modprobe r818x, sudo modprobe ath_pci)
**sudo modprobe -r ****** - Unloades the kernel module ****.  (Example usage - sudo modprobe -r ndiswrapper)
**sudo ifup/ifdown <interface>** - Brings up/down the interface and clears the routing table for the specified interface
**sudo ifconfig <interface> up/down** - Brings up/down the interface for the specified interface 
**sudo dhclient <interface>** - Request IP address from DNS server for specified interface
**sudo dhclient -r <interface>** - Release IP address associated with specified interface
**sudo iptables -L** - Lists firewall rules 
**dmesg | more** - Lists boot log -- good for troubleshooting problems with modules/drivers not being loaded
**uname -r** - Displays kernel version

**Further references:**
Ra chipsets - rt2500, rt73, rt61, rt2570 drivers - [http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey) - Author diepruis
Ndiswrapper installation for Broadcom chipsets - [http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963) - Author Jamie Jackson
Madwifi website for certain Atheros Chipsets - [http://madwifi.org/](http://madwifi.org/) -- If your Atheros chipset is listed on this website - it should work out of the box with installation of the linux restricted drivers package for your kernel version

---

### Post by GSF1200S on 2007-10-10
Hey thanks alot for this.. this will help me immensely. I dont even run a network manager, so this is especially useful as a result of you listing the CLI to use. Until now Ive been afraid to use WPA 1-2, but I think it will be a good learning experience.

Thanks again...

---

### Post by Lucho77 on 2007-11-21
Thanks kevdog for your post, I can connect with no problem.
Only one thing, after issue 'lshw -C network' in the line:
logical name: wifi0
That labeled logical name did not work for me, so I changed for ath0 and follow the next step for WEP connection and it did the trick.
Thanks again.

---

### Post by kevdog on 2007-11-22
Thanks for pointing that out -- I know the madwifi driver makes a physical interface name for the device -wifi0, and then creates a default virtual interface ath0.  Its possible to make more virtual interfaces if you needed them.  Ive found this out with my own Atheros card.  I dont know of a way to convey this to people specifically b/c wifi0 is mentioned in the lshw -C network statement, and ifconfig/iwlist scan show both the ath0 and wifi0 interfaces (which are actually the same device).  Maybe somebody could help me with this one!

---

### Post by cudds on 2007-12-01
thanks for the help - connection is much more stable - how would I script this up to run at boot for all users? When I run wpa_supplicant it doesn't finish running so I have to bring another terminal up for the rest

---

### Post by chrisN_uk on 2007-12-01
Thanks for the guide. I'm coming across a problem though, 
```
sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
Line 7: invalid key_mgmt 'RSN'
Line 7: no key_mgmt values configured.
Line 7: failed to parse key_mgmt 'RSN'.
Line 11: failed to parse network block.
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.

```

Any idea what's wrong? I think I don't have something installed...

---

### Post by mrpresident on 2007-12-01
hmmm im trying this.
got up to ```
pa_supplicant -w -D bcm43xx -i eth2 -c/etc/wpa_supplicant.conf -dd 
```

but then it tells me that the dirver is unsupported.
 can anyone help a n00b?

i think i am using the bcm43xx driver version 2.6.22-14-generic.
 iremember installing the restricted driver thing when i installed ubuntu on this comp.

---

### Post by kevdog on 2007-12-01
Directly from the man wpa_supplicant pages:

> Available Drivers

The available drivers to specify with the -D option are:

hostap
    (default) Host AP driver (Intersil Prism2/2.5/3). (this can also be used with Linuxant DriverLoader). 
hermes
    Agere Systems Inc. driver (Hermes-I/Hermes-II). 
madwifi
    MADWIFI 802.11 support (Atheros, etc.). 
atmel
    ATMEL AT76C5XXx (USB, PCMCIA). 
wext
    Linux wireless extensions (generic). 
ndiswrapper
    Linux ndiswrapper. 
broadcom
    Broadcom wl.o driver. 
ipw
    Intel ipw2100/2200 driver. 
wired
    wpa_supplicant wired Ethernet driver 
bsd
    BSD 802.11 support (Atheros, etc.). 
ndis
    Windows NDIS driver.

I think you want to use either broadcom or wext for your driver rather than specifying bcm43xx

---

### Post by rabiddachshund on 2007-12-12
I just upgraded from Feisty to Gutsy. I have a linksys wmp54g (using the ralink that worked in Feisty. Gutsy sees the network with ~80% signal but it just won't connect to it. My network is unsecure and broadcasted. I followed your steps but no dice. Here's my terminal; maybe there's something I'm missing:

> david@TheBeast:~$ lshw -C network WARNING: you should run this program as super-user.   *-network                       description: Ethernet interface        product: 82573L Gigabit Ethernet Controller        vendor: Intel Corporation        physical id: 0        bus info: pci@0000:04:00.0        logical name: eth0        version: 01        serial: 00:12:3f:79:66:e8        width: 32 bits        clock: 33MHz        capabilities: bus_master cap_list ethernet physical        configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.4-1 latency=0 module=e1000 multicast=yes   *-network        description: Wireless interface        product: RT2561/RT61 802.11g PCI       vendor: RaLink        physical id: 5        bus info: pci@0000:05:05.0        [COLOR="Red"]logical name: wmaster0 [/COLOR]       version: 00        serial: 00:1a:70:a6:34:6d        width: 32 bits        clock: 33MHz        capabilities: bus_master cap_list logical ethernet physical wireless        configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g 
david@TheBeast:~$ sudo ifconfig wmaster0 down david@TheBeast:~$ sudo dhclient -r wmaster0 
Internet Systems Consortium DHCP Client V3.0.5 Copyright 2004-2006 Internet Systems Consortium. All rights reserved. For info, please visit http://www.isc.org/sw/dhcp/ 
wmaster0: unknown hardware address type 801 
wmaster0: unknown hardware address type 801 
Listening on LPF/wmaster0/
 Sending on   LPF/wmaster0/ 
Sending on   Socket/fallback 
david@TheBeast:~$ sudo ifconfig wmaster0 up 
SIOCSIFFLAGS: Operation not supported 
david@TheBeast:~$ sudo iwconfig wmaster0 essid "default" 
Error for wireless request "Set ESSID" (8B1A) :     SET failed on device wmaster0 ; Operation not supported. 
david@TheBeast:~$ sudo iwconfig wmaster0 mode Managed Error for wireless request "Set Mode" (8B06) :     SET failed on device wmaster0 ; Operation not supported.
david@TheBeast:~$ sudo dhclient wmaster0 There is already a pid file /var/run/dhclient.pid with pid 134519120 Internet Systems Consortium DHCP Client V3.0.5 Copyright 2004-2006 Internet Systems Consortium. All rights reserved. For info, please visit http://www.isc.org/sw/dhcp/  
wmaster0: unknown hardware address type 801 
wmaster0: unknown hardware address type 801 
Listening on LPF/wmaster0/ 
Sending on   LPF/wmaster0/ 
Sending on   Socket/fallback 
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 4 
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 9 
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 14 receive_packet failed on wmaster0: Network is down 
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 4 send_packet: Network is down 
No DHCPOFFERS received. No working leases in persistent database - sleeping. 
david@TheBeast:~$

For some reason Network Manager lists the card as ra0 so I tried it with that:

> david@TheBeast:~$ sudo ifconfig ra0 down 
[sudo] password for david: 
david@TheBeast:~$ sudo dhclient -r ra0 
There is already a pid file /var/run/dhclient.pid with pid 6220 killed old client process, removed PID file Internet Systems Consortium DHCP Client V3.0.5 Copyright 2004-2006 Internet Systems Consortium. All rights reserved. For info, please visit http://www.isc.org/sw/dhcp/  
wmaster0: unknown hardware address type 801 
wmaster0: unknown hardware address type 801 
Listening on LPF/ra0/00:1a:70:a6:34:6d 
Sending on   LPF/ra0/00:1a:70:a6:34:6d 
Sending on   Socket/fallback 
david@TheBeast:~$ sudo ifconfig ra0 up 
david@TheBeast:~$ sudo iwconfig ra0 essid "default" 
david@TheBeast:~$ sudo iwconfig ra0 mode Managed 
david@TheBeast:~$ sudo dhclient ra0 
There is already a pid file /var/run/dhclient.pid with pid 134519120 Internet Systems Consortium DHCP Client V3.0.5 Copyright 2004-2006 Internet Systems Consortium. All rights reserved. For info, please visit http://www.isc.org/sw/dhcp/ 
wmaster0: unknown hardware address type 801 
wmaster0: unknown hardware address type 801
Listening on LPF/ra0/00:1a:70:a6:34:6d 
Sending on   LPF/ra0/00:1a:70:a6:34:6d 
Sending on   Socket/fallback 
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6 
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9 
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 16 No 
DHCPOFFERS received. No working leases in persistent database - sleeping. 
david@TheBeast:~$ 

I tried to format it as closely as possible, but it's not quite right because I'm having to use windows to post this :|

HOLY CRAP! I figured I'd try to connect through network manager one last time before posting this and it worked!
What just happened?

---

### Post by Flare183 on 2007-12-12
Most of the time if you modprobe your wireless card, then type in sudo dhclient will work.

---

### Post by qiemem on 2007-12-17
Thanks for the howto.  A lot clearer than most on the subject.

Ran into a snag however.  I'm using the broadcom drivers (not ndiswrapper), but when I get:
```

$ sudo wpa_supplicant -w -Dbroadcom -ieth1 -c/etc/wpa_supplicant.conf -dd
[sudo] password for headb:
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'broadcom' ctrl_interface 'N/A' bridge 'N/A'
Unsupported driver 'broadcom'.

Failed to add interface eth1
Cancelling scan request
Cancelling authentication timeout

```
'broadcom' is in the man entry as one of the supported drivers.  Also, I do not run into this problem if I try one of the others. (It of course fails to connect however.)

Any ideas?  I tried google and could find much...

From lshw -C network:
```

  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 03
       serial: 00:90:4b:99:10:a1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

```

Thanks!

---

### Post by kevdog on 2007-12-18
I think you have to specify the wext driver rather than broadcom.

Also seems by just googling a lot of people are having problems with the bcm43xx driver and wpa.  Im not saying its not going to work, but ndiswrapper, rather than bcm43xx, in conjuction with wpa supplicant seems by far the more stable solution.  If nothing works then go for ndiswrapper.  Jamie Jackson has written a great post for broadcom users to setup ndiswrapper as contained in the footer of the original instructions.

---

### Post by cakemaster on 2008-02-08
I am using ubuntu 7.10 server edition (gutsy gibbon) with a marvell chipset card (zew1602a) and connecting to a wgt624.  Something is still wrong with my connection, however it is worth mentioning that when starting wpa_supplicant a -B should be added to the end of the line to run supplicant in the background as a daemon or you will have to break the process t return to command line and consequently the dhcp request will fail.  also, the line in wpa_supplicant.conf "scan_ssid=0" would create errors when I tried to run supplicant, and it worked fine when removed.  I believe this setting is 0 by default, and should only need to be set to 1 if your ap uses a hidden ssid.  As I said, my connection is not completely working but I believe it is the router for various reasons.  Before these changes to my procedure the router would list dashes and my mac address instead of the name I gave the box and my local ip.

---

### Post by kevdog on 2008-02-08
I agree with the -B flag for a background process, however if you do that you wont get any debugging output.  Again I'm trying to troubleshoot the connection.  Once you get a connection I would put a -B flag, since Im not concerned with the debugging messages being displayed.  While wpa_supplicant is being run in the foreground on one window, you can always pop open another command window and type sudo dhclient wlan0 and things should work normally.

An updated version of the guide is listed here:
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by Adam.W on 2008-02-25
Hi 
I am using xubuntu on my lifebook B-2131 (love it aswell) and seem to be having a smiler problem. I am very new to linux so please be gentle. I have a belkin usb adapter (F5D7050) and can't get it to work. 
I also have a PCMCIA card (XI-330B) and can't get that to work ether?

My laptop would be perfect if the wireles worked.

Please Help!

---

### Post by kevdog on 2008-02-25
You need to start listing your chipset so we can help you!

---

### Post by Adam.W on 2008-02-26
Where do I fined what chipset to list. I dont know What chipset I've got?

---

### Post by kevdog on 2008-02-26
Take a look at this:
[http://ubuntuforums.org/showthread.php?t=596797](http://ubuntuforums.org/showthread.php?t=596797)

---

