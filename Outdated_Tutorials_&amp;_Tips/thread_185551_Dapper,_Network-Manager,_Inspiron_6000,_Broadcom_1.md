---
title: "Dapper, Network-Manager, Inspiron 6000, Broadcom 1470"
date: 2006-05-31
forum: Outdated Tutorials &amp; Tips
---

### Post by _flyman_ on 2006-05-31
Dapper, Network-Manager and WPA-PSK/TKIP
Dell Inspiron 6000
Broadcom 1470 Dual Band WLAN Mini-PCI Card
Westell 327W Router

*this guide assumes that your wireless driver, via ndiswrapper
was working with breezy or dapper and you are having trouble
with the packages network-manager, network-manager-gnome and
their related components.

---------------------------------------------------------------------------

1. install or upgrade to wpasupplicant version 0.4.8-3 
if you have not done so already...this upgrade will rename your
_unneeded_ wpasupplicant config files to...

/etc/default/wpasupplicant to wpasupplicant.dpkg-bak
and
/etc/wpa_supplicant.conf to wpa_supplicant.conf.dpkg-bak

2. install network-manager 0.6.2-0
3. install network-manager-gnome 0.6.2-0

4. blacklist the bcm43xx driver...
the dapper install on my dell inspiron 6000 did not recognize
my wireless 1470 card and installed the bcm43xx driver instead.
edit /etc/modprobe.d/blacklist
and enter at the bottom of the page... blacklist bcm43xx

5. make sure you have ndiswrapper installed correctly
and/or your particular driver is loaded with the command 'ndiswrapper -l'

6. edit /etc/networking/interfaces

remove all entries other than...
auto lo
iface lo inet loopback

***note*** network-manager does not support static ip yet.

7. configuring network-admin...actually you _need_ to unconfigure
and deactivate all adapters so that they all have a red x and read xxx interface
is not configured.

7.1 reboot the machine.  all of the daemons should be loaded at start up.
(the misc section below lists the daemons involved in making the packages work).

8. now right click on the nm-applet on the top menu bar, this gives the option of
enabling networking and wireless connections, a left click on applet will give you the
following; wireless networks, connect to wireless network, create new wireless network.

9. select 'connect to other wireless network' it will walk you through all of
the wpa settings. (in my case i use the wpa personal with tkip using a westell
327wrouter.) after negotiating with the router you will be asked for a keyring
password which is the same as your login password.

10. you should be connected in a few moments and your good to go.

### problems and bugs ###

if you have any problems connecting...

i.e connecting after switching between eth0 and wlan0
    connecting and reconnecting to the wireless network
    or waking from suspend etc. etc.

try
sudo /etc/init.d/dbus restart
(it has worked every time i have been unable to connect)

sudo /etc/init.d/dbus restart output is...

 * Stopping network-manager dispatcher                               [ ok ]
 * Stopping network-manager daemon                                   [ ok ]
 * Stopping DHCP client manager...                                       [ ok ]
 * Stopping Hardware abstraction layer hald                           [ ok ]
 * Stopping system message bus dbus                                   [ ok ]
 * Starting system message bus dbus                                    [ ok ]
 * Starting Hardware abstraction layer hald                             [ ok ]
 * Starting DHCP client manager...                                         [ ok ]
 * Starting network-manager daemon                                     [ ok ]
 * Starting network-manager dispatcher                                  [ ok ]


### there are some other glitches...i.e. if your access point is not
broadcasting, nm does not cache your past connections and you have to enter your essid
and wpa info and passphrase every time you want to reconnect.  if the ap is broadcasting
your essid, network-manager will reconnect automatically using the keychain.

### on switching to ethernet connections.  i have had to manually uncheck 'enable wireless'
to get the hard line to active.

### processes running and/or launched with network-manager

deamons
---nm-applet
---network-manager
---network-managerdispatcher
---dhcdbd
    ***dhclient ---spawned while connecting to networks

*****wpa_supplicant ---spawned while connecting and continues to run

----------------------------------------------------------------------------

---

### Post by phaed on 2006-06-05
I have a Dell Inspiron E1505 with a Dell Wireless 1390 WLAN MiniCard (Broadcom BCM4311 chipset) working thanks to the Windows drivers and ndiswrapper (followed instructions from elsewhere on these forums).  

I also have Network Manager.  However, it doesn't show me any wireless networks, nor "connect to wireless network" nor "create new wireless network."  However, it does connect to the wireless network, so it must be an issue of having the menu configured properly.

Any thoughts on how to fix this?

---

### Post by phaed on 2006-06-05
Oh yeah, I just thought of another issue.  When my laptop is booting, it hangs on "configuring network interfaces" or something like that for about 2 minutes before continuing the boot process.  Any thoughts on what might be causing that?

---

### Post by toorima on 2006-06-05
Try commenting out everything but lo in /etc/network/interfaces

---

### Post by phaed on 2006-06-05
When I did that, it did hang on boot, but it still didn't bring up the wireless options in the menu, AND it didn't connect to the wireless network either.  Maybe I'll just try to reinstall NetWork Manager and everything else fresh using the above instructions.

---

