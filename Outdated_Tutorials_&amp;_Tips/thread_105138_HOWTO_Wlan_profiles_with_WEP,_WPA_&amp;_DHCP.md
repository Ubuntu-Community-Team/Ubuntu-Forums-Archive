---
title: "HOWTO: Wlan profiles with WEP, WPA &amp; DHCP"
date: 2005-12-17
forum: Outdated Tutorials &amp; Tips
---

### Post by calt129 on 2005-12-17
Hi there,

Back then under Ubuntu 5.04, and now under 5.10, I was pretty disappointed with the unreliably working Wlan profiles. It was partly due to the ever-changing interface names (which can be solved with /etc/iftab :) and the lack of settings possibilities in network-admin (which can be launched via Gnome's Wlan applet). Furthermore network-admin was really slow everytime I wanted to change profiles quickly. So I've taken the low-level path und stuck with /etc/network/interfaces, which I presume is used by these various tools anyway.

My primary interface is eth1 (Wlan) and I'm using eth0 (cable) very rarely but its configuration is very similar. There are 3 profiles for home (1 with static IP with WPA, 1 with DHCP with WPA and 1 with DHCP with WEP) and 2 profiles for work (1 with static IP with WEP and 1 with DHCP with WEP).

So, here's a sample interfaces file, an accompanying script to detect the current environment based on MAC-addresses of accesspoints, a sample wpa_supplicant.conf file and a small script to bring the interfaces down before suspending/hibernating the computer (they're upped automatically on resume) so that if you change the location during this suspension, your laptop gets automatically a new IP as soon as you power it on again.

I'll assume that you know how to run commands (such as in a terminal) and edit files (with vi, gedit, etc.)

* Installation:*
[LIST=1]
[*]Check if you have the packages **wireless-tools** & **resolvconf**. You should already have wireless-tools and resolvconf is needed if you want to set dns-suffices & nameservers. You can check this either via synaptic or running:```
apt-cache showpkg resolvconf
```.
[*]**Review the MAC-addresses and other settings** in the profiles file. The MACs can be found by calling ```
iwlist eth1 scanning
``` under "Cell xx- Address:..." line
[*]Only then copy the profiles file to /etc/network/profiles (**make a backup of the old file first!!!**)
[*]Copy the script to /usr/local/bin/scan-wireless-mac-address.sh (or wherever you want to but don't forget to change the path for in the profiles file)
[*]Review and copy the WPA-configfile it to /etc/wpa_supplicant.conf if you're using WPA.
[*][This may change] Copy the *interface-down* script to /etc/acpi/suspend.d/48-networking-down.sh (or whatever name you see fit)
[/LIST]

I've included some optional commands such as pre-up, post-down, etc. I'll explain those shortly:
[LIST]
[*]Normally if you want to connect to a WPA-protected AP (accesspoint) you should start the WPA_supplicant first, even just to connect to the AP (correct me if I'm wrong).
[*]After you connect to some AP and got your IP, you can also copy a network-specific hosts file to /etc/hosts, which is simply a list of statically defined IP-numbers to avoid DNS lookups. This step could be done prior to connection, too, but it sounds better this way.
[*]Whenever you bring down an interface, it has no sense anymore that wpa_supplicant runs in the background, so it's safe to kill it in a post-down line.
[/LIST]


The profiles file:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#mapping hotplug
#	script grep
#	map eth1

# The primary network interface
auto eth1
mapping eth1
    script /usr/local/bin/scan-wireless-mac-address.sh
    map eth1 11:22:33:44:55:66 homedhcp
    map eth1 11:22:33:44:55:66 home
    map eth1 11:22:33:44:55:66 homealt
    map eth1 22:33:44:55:66:77 workdhcp
    map eth1 22:33:44:55:66:77 work
    
iface homedhcp inet dhcp
    pre-up wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -q
    post-up cp /etc/hosts.home /etc/hosts
    post-down killall wpa_supplicant
    #post-up ifconfig eth1 mtu 1300

iface home inet static
    pre-up wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -q
    post-up cp /etc/hosts.home /etc/hosts
    post-down killall wpa_supplicant
    network 192.168.100.0
    address 192.168.100.186
    netmask 255.255.255.0
    gateway 192.168.100.1
    dns-nameservers 11.22.33.44 55.66.77.88
    dns-search my.domain
    mtu 1300

iface homealt inet static
    post-up cp /etc/hosts.home /etc/hosts
    wireless-mode managed
    wireless-essid alternate-wlan
    wireless-key s:0123456789 open
    network 192.168.100.0
    address 192.168.100.186
    netmask 255.255.255.0
    gateway 192.168.100.1
    dns-nameservers 11.22.33.44 55.66.77.88
    dns-search my.domain
    mtu 1300
 
iface workdhcp inet dhcp
    #post-up ifconfig eth1 mtu 1300
    wireless-mode managed
    wireless-essid office-wlan
    wireless-key-1 s:1234567890123 open
    wireless-key 012345678990ABCDEF01234567 open
    mtu 1300

iface work inet static
    post-up cp /etc/hosts.work /etc/hosts
    wireless-mode managed
    wireless-essid office-wlan
    wireless-key-1 s:1234567890123 open
    network 10.11.11.0
    address 10.11.11.169
    netmask 255.255.255.0
    gateway 10.11.11.1
    wireless-key 012345678990ABCDEF01234567 open
    #dns-search myworkdomain.com
    #dns-nameservers 10.11.11.3
    mtu 1300

iface eth0 inet dhcp
    mtu 1300

# activating the following line increases bootup time!
# alternatively, one can decrease the timeout value in /etc/dhcp3/dhclient.conf
# auto eth0

```


The script to detect accesspoints, based on their MACs (no change needed):
```

#!/bin/sh

# this script finds out if an Access-Point with the given MAC address is reachable
# prints the profile (last parameter) out
# returns 0 if found, 1 if not
# should be called from /etc/network/interfaces like this:
#   map eth1 11:22:33:44:55:66 homewlan
if [ `id -u` != 0 ]; then
        echo "You have to run this script as root"
            exit 1
            fi
if [ "$1" = "" ] ; then
        echo "You have to pass an interface name, e.g. eth1"
        exit 1
fi
BINIWLIST="/sbin/iwlist"
if [ ! -x $BINIWLIST ]; then
    echo "$BINIWLIST does not exist or is not executable!"
    exit 1
fi

IF="$1"
which=""

while read IFACE MAC PROFILE; do
	if [ "$which" ]; then continue; fi

    echo -n "Checking if access-point $MAC is reachable... " >&2

	if $BINIWLIST $IFACE scanning | grep "Cell" | grep $MAC > /dev/null 2>&1; then
        echo "OK. Using profile $PROFILE" >&2
		which="$PROFILE"
	else
        echo "" >&2
    fi
done

if [ "$which" ]; then echo $which; exit 0; fi
exit 1

```


The script to bring the interfaces down (no changes needed):
```

#!/bin/bash

if [ -e /etc/network/interfaces ]; then
    # bring down all interfaces
    ifdown -a
fi

```

Sample WPA config file (change the SSID & key, more info under [https://wiki.ubuntu.com/WPAHowto]("https://wiki.ubuntu.com/WPAHowto")):
```

# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see 
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
#  configuration parameters.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
network={
        ssid="cu"
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        psk=00112233445566778899aabbccddeeff00112233445566778899aabbccddeeff
}

```

I hope this helps someone. All suggestions and corrections are welcome.

EDIT: I've found this post from another Ubuntu user. Pretty much the same technique (using iwlist & interfaces file), just a bit different. Link: [http://lists.ubuntu.com/archives/ubuntu-users/2005-April/028964.html]("http://lists.ubuntu.com/archives/ubuntu-users/2005-April/028964.html")

Peace and out

---

