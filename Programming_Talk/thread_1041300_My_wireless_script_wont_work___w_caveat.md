---
title: "My wireless script wont work   w/ caveat"
date: 2009-01-16
forum: Programming Talk
---

### Post by braze on 2009-01-16
ive been trying to write a simple (at least i thought it was) script to launch my wireless usb under ubuntu with kde. im using nano.

when i run it from a terminal it works fine, but it just wont run from the script. there is a caveat, but first heres the script.

-------------------------------

#!/bin/bash

sudo ifconfig wlan1 up
sudo iwpriv wlan1 set AuthMode=WPAPSK
sudo iwpriv wlan1 set EncrypType=TKIP
sudo iwpriv wlan1 set WPAPSK=1111111111
sudo iwpriv wlan1 set SSID=network
sudo iwpriv wlan1 set NetworkType=Infra
sudo dhclient wlan1

---------------------------
this is the output

There is already a pid file /var/run/dhclient.pid with pid 13451
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan1/(mac is here)
Sending on LPF/wlan1/(mac is here)
Sending on Socket/fallback
DHCPREQUEST of 192.168.0.444 on wlan1 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.0.444 on wlan1 to 255.255.255.255 port 67
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
Trying recorded lease 192.168.1.444
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping

--------------------------
now heres the twist:

sometimes it asks for a password, sometimes it doesnt

also, if i run the script up to here:
sudo iwpriv wlan1 set NetworkType=Infra

stop it, and run sudo dhclient wlan1 in a terminal, it works!

ive tried running it with sh script, ./script but still no joy. its probably something simple im just missing but im stumpped.

thanx if anyone has any ideas.

---

### Post by mssever on 2009-01-16
Are you running this script in a terminal all the time? sudo requires a terminal. (An alternative if you want GUI functionality would be to drop the sudo altogether and call it with kdesu /path/to/your/script. If you run your script as root, then you don't need sudo for the individual commands.

Also--and this is just a wild stab in the dark--it might be that iwpriv takes a while to apply its settings. I don't know since I've never used iwpriv and I'm too lazy to look it up. But you might try inserting a sleep before dhclient.

---

### Post by skoorbevad on 2009-01-25
Try this:

```

#!/bin/bash
#
set -e

# Probably best to specify our device from command line.
INT=$1 || { echo "Usage: $0 <wireless_device>"; exit 1; }

# We should be root.
whoami | grep root || {
  echo "You much be root to continue."
  exit 1
}

# Is $INT wireless?
# Check me here -- iwconfig has funky output to STDERR.
iwconfig 2>/dev/null | sed 's/ .*$//' || {
  echo "$INT doesn't appear to be wireless.
  exit 1
}

ifconfig $INT up
iwpriv $INT set AuthMode=WPAPSK
iwpriv $INT set EncrypType=TKIP
iwpriv $INT set WPAPSK=1111111111
iwpriv $INT set SSID=network
iwpriv $INT set NetworkType=Infra

if [ ! -f /var/run/dhclient-$INT.pid ];
then
  dhclient $INT || { echo "Can't start DHCP for $INT."; exit 1; }
else
  echo "DHCP appears to already be running for $INT."
fi

```

...fix my typos, there's bound to be some.  But you probably always want to call a script like this with "sudo", or as root directly.  Utilizing sudo from within a script itself is normally bad juju unless you want to get into an expect script, which is also bad juju.

---

### Post by eightmillion on 2009-01-25
> **skoorbevad said:**
> Try this:

```

# We should be root.
whoami | grep root || {
  echo "You much be root to continue."
  exit 1
}

```

...fix my typos, there's bound to be some.  But you probably always want to call a script like this with "sudo", or as root directly.  Utilizing sudo from within a script itself is normally bad juju unless you want to get into an expect script, which is also bad juju.

This is a better way to check if the user is root.
```

if [[ $EUID -ne 0 ]]; then
        echo "You must be root to continue."  1>&2
        exit 1
fi

```

---

### Post by skoorbevad on 2009-01-26
Kudos for that -- I never thought about doing it that way.  I'll tuck that one away next time I need it.

Been writing bash for 10 years and I learn something new about it every day.


> **eightmillion said:**
> This is a better way to check if the user is root.
```

if [[ $EUID -ne 0 ]]; then
        echo "You must be root to continue."  1>&2
        exit 1
fi

```

---

### Post by braze on 2009-01-29
thanx....ill try that tonite after i get home from work

:end

---

