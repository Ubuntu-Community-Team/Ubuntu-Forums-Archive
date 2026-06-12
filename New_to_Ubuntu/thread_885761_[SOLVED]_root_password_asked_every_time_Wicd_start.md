---
title: "[SOLVED] root password asked every time Wicd starts, after upgrade to 1.5.1"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by gerben1 on 2008-08-10
I upgraded from wicd 1.4.1, using wicd_1.5.1_all.deb. I did nothing special juts double clicked it and let it install it installed without errors or warnings.

When I boot my computer I am asked for the root password after I have logged in. 
A dialog pops up with this text:
"Wicd needs to access your computer's network cards"
underneath is a box where I can enter the password, after I give it the root password, the internet connection is working, but there is no tray icon even though wicd-client has automatically been added to session startup. If I then run wicd-client from the Terminal I get the tray icon.

***
I saw running the command below being suggested in other fora, but it doesn't help:

gerben@gerben-laptop:~$ sudo update-rc.d wicd start 80 2 3 4 5 . stop 20 0 1 6 .
System startup links for /etc/init.d/wicd already exist.

---

### Post by SunnyRabbiera on 2008-08-10
Did you set your install to have a root account by any chance?
If so, not a good move sorry to say.

---

### Post by gerben1 on 2008-08-10
No, I did not.

---

### Post by gerben1 on 2008-08-10
This is the reason acccording to someone in an old thread in which I cannot reply:

"This is because the daemon isn't launched on start, and then when the tray sees that there is no daemon it launches it as root so it needs the password. Although I think it is broken right now and it doesn't launch the daemon"
(from: [http://wicd.sourceforge.net/phpbb/viewtopic.php?f=3&t=174](http://wicd.sourceforge.net/phpbb/viewtopic.php?f=3&t=174))

unfortunately nobody offered a solution in that thread...

---

### Post by gerben1 on 2008-08-10
Here is a screenshot of what happens if I try to reinstall the package:

---

### Post by gerben1 on 2008-08-10
Below are the contents of /var/log/wicd/wicd.log 

Does anybody know whether these lines are a problem:
"2008/08/10 19:43:13 :: There is already a pid file /var/run/dhclient.pid with pid"?

```

2008/08/10 19:43:05 :: ---------------------------
2008/08/10 19:43:05 :: wicd initializing...
2008/08/10 19:43:05 :: ---------------------------
2008/08/10 19:43:05 :: checking dhcp...
2008/08/10 19:43:05 :: checking dhcp...
2008/08/10 19:43:05 :: automatically detected wireless interface wlan0
2008/08/10 19:43:05 :: found wireless_interface in configuration wlan0
2008/08/10 19:43:05 :: setting wireless interface wlan0
2008/08/10 19:43:05 :: found wired_interface in configuration eth0
2008/08/10 19:43:05 :: setting wired interface eth0
2008/08/10 19:43:05 :: found wpa_driver in configuration wext
2008/08/10 19:43:05 :: setting wpa driver wext
2008/08/10 19:43:05 :: found always_show_wired_interface in configuration True
2008/08/10 19:43:05 :: found use_global_dns in configuration False
2008/08/10 19:43:05 :: setting use global dns to False
2008/08/10 19:43:05 :: setting use global dns to boolean False
2008/08/10 19:43:05 :: found global_dns_1 in configuration None
2008/08/10 19:43:05 :: found global_dns_2 in configuration None
2008/08/10 19:43:05 :: found global_dns_3 in configuration None
2008/08/10 19:43:05 :: setting global dns
2008/08/10 19:43:05 :: global dns servers are None None None
2008/08/10 19:43:05 :: found auto_reconnect in configuration True
2008/08/10 19:43:05 :: setting automatically reconnect when connection drops
2008/08/10 19:43:05 :: found debug_mode in configuration 0
2008/08/10 19:43:05 :: found wired_connect_mode in configuration 1
2008/08/10 19:43:05 :: found signal_display_type in configuration 0
2008/08/10 19:43:05 :: found dhcp_client in configuration 0
2008/08/10 19:43:05 :: Setting dhcp client to 0
2008/08/10 19:43:05 :: checking dhcp...
2008/08/10 19:43:05 :: checking dhcp...
2008/08/10 19:43:05 :: found link_detect_tool in configuration 0
2008/08/10 19:43:05 :: found flush_tool in configuration 0
2008/08/10 19:43:05 :: Wireless configuration file found...
2008/08/10 19:43:05 :: Wired configuration file found...
2008/08/10 19:43:05 :: chmoding configuration files 0600...
2008/08/10 19:43:05 :: chowning configuration files root:root...
2008/08/10 19:43:05 :: Using wireless interface...wlan0
2008/08/10 19:43:05 :: autoconnecting... wlan0
2008/08/10 19:43:06 :: No wired connection present, attempting to autoconnectto wireless network
2008/08/10 19:43:06 :: trying to automatically connect to...Gerben
2008/08/10 19:43:06 :: Connecting to wireless network Gerben
2008/08/10 19:43:06 :: Putting interface down
2008/08/10 19:43:07 :: Releasing DHCP leases...
2008/08/10 19:43:08 :: Setting false IP...
2008/08/10 19:43:10 :: Stopping wpa_supplicant and any DHCP clients
2008/08/10 19:43:10 :: Flushing the routing table...
2008/08/10 19:43:10 :: Generating psk...
2008/08/10 19:43:10 :: Attempting to authenticate...
2008/08/10 19:43:11 :: Putting interface up...
2008/08/10 19:43:12 :: exiting connection thread
2008/08/10 19:43:08 :: Connecting to wireless network Gerben
2008/08/10 19:43:08 :: Putting interface down
2008/08/10 19:43:08 :: Releasing DHCP leases...
2008/08/10 19:43:10 :: Setting false IP...
2008/08/10 19:43:11 :: Stopping wpa_supplicant and any DHCP clients
2008/08/10 19:43:12 :: Flushing the routing table...
2008/08/10 19:43:12 :: Generating psk...
2008/08/10 19:43:12 :: Attempting to authenticate...
2008/08/10 19:43:12 :: Putting interface up...
2008/08/10 19:43:13 :: Running DHCP
2008/08/10 19:43:13 :: There is already a pid file /var/run/dhclient.pid with pid 134519072
2008/08/10 19:43:13 :: Internet Systems Consortium DHCP Client V3.0.6
2008/08/10 19:43:13 :: Copyright 2004-2007 Internet Systems Consortium.
2008/08/10 19:43:13 :: All rights reserved.
2008/08/10 19:43:13 :: For info, please visit http://www.isc.org/sw/dhcp/
2008/08/10 19:43:13 :: 
2008/08/10 19:43:13 :: wmaster0: unknown hardware address type 801
2008/08/10 19:43:14 :: wmaster0: unknown hardware address type 801
2008/08/10 19:43:14 :: Listening on LPF/wlan0/00:14:a4:6a:b1:ae
2008/08/10 19:43:14 :: Sending on   LPF/wlan0/00:14:a4:6a:b1:ae
2008/08/10 19:43:14 :: Sending on   Socket/fallback
2008/08/10 19:43:14 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
2008/08/10 19:43:15 :: DHCPOFFER of 192.168.1.101 from 192.168.1.1
2008/08/10 19:43:15 :: DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67
2008/08/10 19:43:15 :: DHCPACK of 192.168.1.101 from 192.168.1.1
2008/08/10 19:43:15 :: bound to 192.168.1.101 -- renewal in 42026 seconds.
2008/08/10 19:43:15 :: DHCP connection successful
2008/08/10 19:43:15 :: Connecting thread exiting.
2008/08/10 20:02:31 :: GetWiredProperty: WiredNetwork does not exist

```

---

### Post by gerben1 on 2008-08-10
The cause of the problem was that I still had the old /etc/int.d/wicd script, as in the one from the previous version 1.4.2

The problem seems to be solved by opening the wicd_1.5.1_all.deb file in archive manager, then open the etc/init.d/wicd script that is in the .deb file and copy its contents over the contents of the /etc/init.d/wicd script that is on the hard drive.

No clue why it did not install that file properly when installing wicd_1.5.1_all.deb

---

### Post by RogerM on 2008-08-26
Well I tried the "solution" but the correct script was already in /etc/init.d.

So, I still have to enter the root password every time I start Kubuntu 8.04.1.

Does anybody have other suggestions? Solutions?

---

### Post by imdano on 2008-08-29
Did you install from a .deb or did you build from source?

---

### Post by tedjordan on 2011-02-24
I resolved this problem by doing the following

# sudo apt-get install sysv-rc-conf
# sudo sysv-rc-conf

A window will show.  Arrow down near the end to "wicd".  Use the spacebar
to put an X in 2, 3, 4, & 5.  Enter q to quit.  Reboot.

That did it for me

---

### Post by overdrank on 2011-02-24
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=182255&stc=1&d=1296333044[/IMG]

---

