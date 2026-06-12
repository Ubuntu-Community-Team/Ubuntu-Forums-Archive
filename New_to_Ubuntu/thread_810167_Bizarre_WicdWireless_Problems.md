---
title: "Bizarre Wicd/Wireless Problems"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Alex J. on 2008-05-28
So, I got my wireless up and running with [[COLOR="Red"]these instructions[/COLOR]]("http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html") and Wicd. The thing is, it seems totally by chance when I get wireless. I reboot again and again and again. It seems that the majority of times I can't get wireless, but sometimes it will connect with no problem. I can't find a pattern or a reason as to why it won't connect.

A while ago, Wicd said that it wasn't connected to the wireless, when it actually was connected and I could completely use my wireless.

Just now I attempted to use the "Network Settings" in System>Administration>Network to establish a connection. Still no go. When I rebooted, STILL no go, but when I tried to get Wicd to connect again it said that it was "Removing the old connection" and then froze.

I know that when I installed Wicd that it was suppose to uninstall network manager, but since Wicd tried to remove the settings from the "network settings" 

I've been wondering if network settings is at all connected to network manager? Do they conflict at all? I kinda hope so because that might make the solution easier.
[B]
Any help is appreciated[/B], I'm a total newbie. And I know that these sorts of wireless questions have been floating around a lot recently (and I think I've been through nearly ALL of the wireless threads. UGH)

---

### Post by Alex J. on 2008-05-28
Okay. Wicd just gave me an error message. And then forced me to reboot.

It went into this terminal thingy and then I got:

"[FONT="Fixedsys"]
Stopping any running daemons...
Starting Wicd daemon...
/opt/wicd
wicd daemon: pid 5650

     *starting anac(h)ronistic cron anacron     [ok]
     *starting deferred execution scheduler atd [ok]
     *starting periodic command scheduler crond [ok]
     *checking battery state...                 [ok]
     *Runing local boot scripts (/etc/rc.local) [ok][/FONT]
"

HELP!

---

### Post by imdano on 2008-05-28
> **Alex J. said:**
> A while ago, Wicd said that it wasn't connected to the wireless, when it actually was connected and I could completely use my wireless.This is probably just a known bug in wicd that sometimes crops up.  It'll be fixed in the next version, but it's nothing to worry about.

> **Alex J. said:**
> "Removing the old connection" and then froze.That sounds like a daemon crash of some kind.  Not sure what caused it though.

> **Alex J. said:**
> I know that when I installed Wicd that it was suppose to uninstall network manager, but since Wicd tried to remove the settings from the "network settings"Wicd does uninstall network manager, but could you elaborate on what you mean by wicd trying to remove the settings from "network settings"?  The only thing wicd removes is conflicting network management apps when it gets installed (wlassistant, Network Manager, wifi-radar).

> **Alex J. said:**
> I've been wondering if network settings is at all connected to network manager?Again, not sure what you mean by "network settings" here.  Just know that removing or installing Network Manager has no affect on your computer's ability to make a network connection, NM just makes use of a capability that's already there.


> **Alex J. said:**
> Okay. Wicd just gave me an error message. And then forced me to reboot.

It went into this terminal thingy and then I got:

"[FONT="Fixedsys"]
Stopping any running daemons...
Starting Wicd daemon...
/opt/wicd
wicd daemon: pid 5650

     *starting anac(h)ronistic cron anacron     [ok]
     *starting deferred execution scheduler atd [ok]
     *starting periodic command scheduler crond [ok]
     *checking battery state...                 [ok]
     *Runing local boot scripts (/etc/rc.local) [ok][/FONT]
"The second part of that message (*starting anac(h)ronistic...) isn't related to wicd at all, so don't worry about that.  The first part is just normal output when the wicd daemon is started.  What was the error message wicd gave you?  Alos, wicd shouldn't ever force you to reboot, are you sure it was wicd and not something else?


Let's step back a minute here.  What kind of network are you trying to connect to (as in what kind of encryption, is the essid hidden)?  Do you run into problems with every network you try, or just certain ones?  Were you having more success connecting with NetworkManager?  Have you tried and/or had success connecting manually using just terminal commands?

---

### Post by Alex J. on 2008-05-28
Yeah...that kinda was a lot of random information I gave. :oops:

My network uses WEP, Essid isn't hidden. It has problems with every network I try. I've been on my friend's network and it was the same problem. Sometimes it would connect on reboot, sometimes it wouldn't.  Had no success connecting with Network Manager, but then again, I uninstalled it early on.

About the terminal commands...been to the Wicd homepage and [[COLOR="Blue"]_here_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=571188"), but I can't piece together what I need to connect using the terminal. Help please?

About the Wicd "Starting Wicd daemon..." thingy. I have no idea. the screen went all black and that came up. I rebooted because I couldn't get out of it at all. May have something to do with it, may not. I was just hoping it was related for an error message rather than just saying, "My wireless won't work!" It hasn't happened again though. Hopefully that was just some random accident I unknowingly made.

---

### Post by sam_delta on 2008-05-28
if the problem is wicd try wifi-radar
```
sudo apt-get install wifi-radar
```
if you still have problems with wifi-radar, then its something else


sam

---

### Post by Alex J. on 2008-05-28
Got the Wifi Radar. Works with my wired connection, as did Wicd.

When I tried to get to the wireless connection it failed and said that it couldn't get an IP address.

Here's what I got from the terminal.[I][B]

"dhclient3 --version 2>&1

Error for wireless request "Set Frequency" (8B04) :

    SET failed on device wlan0 ; Invalid argument.

There is already a pid file /var/run/dhclient.eth1.pid with pid 0

Internet Systems Consortium DHCP Client V3.0.6

Copyright 2004-2007 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



Listening on LPF/wlan0/00:1b:9e:1e:30:82

Sending on   LPF/wlan0/00:1b:9e:1e:30:82

Listening on LPF/eth0/00:1b:38:11:e8:2a

Sending on   LPF/eth0/00:1b:38:11:e8:2a

Sending on   Socket/fallback

Stale pid file.  Removing

Internet Systems Consortium DHCP Client V3.0.6

Copyright 2004-2007 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



Listening on LPF/wlan0/00:1b:9e:1e:30:82

Sending on   LPF/wlan0/00:1b:9e:1e:30:82

Sending on   Socket/fallback

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7"[/B][/I]

---

### Post by imdano on 2008-05-28
From the sounds of things you're probably dealing with a flakey driver, but I'm not 100% sure at this point.  After you aren't connected at boot, are you tring to manually connecting through the wicd GUI?  Have you checked the syslog for errors when you're unable to connect?  Also, whats the output of this command (it'll give me info about your wireless driver): ```
sudo lshw -C network
```

As for connecting with the command line, here's the relevant part of the Manual Connection thread you linked to:> **kevdog said:**
> 
____________________________________________________________________________
[SIZE="4"]**WEP Connection**[/SIZE]

You must have either your 64bit or 128 bit HEX Key or the ASCII Equivalent of your HEX Key.

```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> key HEX_KEY <<<-------- If using ASCII Equivalent, this is s:ASCII_KEY (please make note of the prefix s:)
****Additional Comand that may be needed  -- sudo iwconfig <interface> key open  <<<----See note below
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>
```

***The security mode may be open or restricted, and its meaning depends on the card used. With most cards, in open mode no authentication is used and the card may also accept non-encrypted sessions, whereas in restricted mode only encrypted sessions are accepted and the card will use authentication if available.Running those commands will try to initiate a connection to a WEP network.  Wicd uses a slightly different method, but we can worry about that after seeing if you have success with the command line.

The reboot thing sounds like you might have accidently hit a key combination that killed your X session (which is what provides the GUI in Linux), or maybe some program caused it to crash (probably not wicd, we've never received a bug report with that problem before).  The wicd daemon message, as well as the messages that appeared after it, are normal output that show up when linux boots.  So odds are you somehow got dropped to a terminal and those messages either were left over from when you initially booted or got rerun when you lost your X session.

---

### Post by Alex J. on 2008-05-29
Result of sudo lshw -C network:
[B][I]
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:11:e8:2a
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.101 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:9e:1e:30:82
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.52+,06/21/2007,5.3.0.56 latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
[/I][/B]

Where it says "<interface>" in those commands, do I need to fill something in there?

Going to go look at the system log....never noticed that before. That's pretty handy.

---

### Post by Alex J. on 2008-05-29
What I got from System Log when I tried to connect:
[B][I]
May 28 21:37:42 emmi-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.6
May 28 21:37:42 emmi-laptop dhclient: Copyright 2004-2007 Internet Systems Consortium.
May 28 21:37:42 emmi-laptop dhclient: All rights reserved.
May 28 21:37:42 emmi-laptop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
May 28 21:37:42 emmi-laptop dhclient: 
May 28 21:37:43 emmi-laptop dhclient: Listening on LPF/wlan0/00:1b:9e:1e:30:82
May 28 21:37:43 emmi-laptop dhclient: Sending on   LPF/wlan0/00:1b:9e:1e:30:82
May 28 21:37:43 emmi-laptop dhclient: Sending on   Socket/fallback
May 28 21:37:46 emmi-laptop dhclient: DHCPREQUEST of 192.168.1.149 on wlan0 to 255.255.255.255 port 67
May 28 21:37:53 emmi-laptop dhclient: DHCPREQUEST of 192.168.1.149 on wlan0 to 255.255.255.255 port 67
May 28 21:38:00 emmi-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May 28 21:38:06 emmi-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May 28 21:38:17 emmi-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May 28 21:38:30 emmi-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
May 28 21:38:31 emmi-laptop dhclient: No DHCPOFFERS received.
May 28 21:38:31 emmi-laptop dhclient: Trying recorded lease 192.168.1.149
May 28 21:38:31 emmi-laptop avahi-daemon[5240]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.149.
May 28 21:38:31 emmi-laptop avahi-daemon[5240]: New relevant interface wlan0.IPv4 for mDNS.
May 28 21:38:31 emmi-laptop avahi-daemon[5240]: Registering new address record for 192.168.1.149 on wlan0.IPv4.
May 28 21:38:34 emmi-laptop avahi-daemon[5240]: Withdrawing address record for 192.168.1.149 on wlan0.
May 28 21:38:34 emmi-laptop avahi-daemon[5240]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.149.
May 28 21:38:34 emmi-laptop avahi-daemon[5240]: Interface wlan0.IPv4 no longer relevant for mDNS.
May 28 21:38:34 emmi-laptop avahi-autoipd(wlan0)[7258]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
May 28 21:38:34 emmi-laptop avahi-autoipd(wlan0)[7258]: Successfully called chroot().
May 28 21:38:34 emmi-laptop avahi-autoipd(wlan0)[7258]: Successfully dropped root privileges.
May 28 21:38:34 emmi-laptop avahi-autoipd(wlan0)[7258]: Starting with address 169.254.4.252
May 28 21:38:39 emmi-laptop avahi-autoipd(wlan0)[7258]: Callout BIND, address 169.254.4.252 on interface wlan0
May 28 21:38:39 emmi-laptop avahi-daemon[5240]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.4.252.
May 28 21:38:39 emmi-laptop avahi-daemon[5240]: New relevant interface wlan0.IPv4 for mDNS.
May 28 21:38:39 emmi-laptop avahi-daemon[5240]: Registering new address record for 169.254.4.252 on wlan0.IPv4.
May 28 21:38:43 emmi-laptop avahi-autoipd(wlan0)[7258]: Successfully claimed IP address 169.254.4.252
May 28 21:38:43 emmi-laptop dhclient: No working leases in persistent database - sleeping.
May 28 21:38:44 emmi-laptop avahi-daemon[5240]: Interface wlan0.IPv4 no longer relevant for mDNS.
May 28 21:38:44 emmi-laptop avahi-daemon[5240]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.4.252.
May 28 21:38:44 emmi-laptop avahi-autoipd(wlan0)[7258]: SIOCSIFFLAGS failed: Permission denied
May 28 21:38:44 emmi-laptop avahi-autoipd(wlan0)[7258]: Callout STOP, address 169.254.4.252 on interface wlan0
May 28 21:38:44 emmi-laptop dhclient: receive_packet failed on wlan0: Network is down
May 28 21:38:44 emmi-laptop avahi-daemon[5240]: Withdrawing address record for 169.254.4.252 on wlan0.
May 28 21:38:44 emmi-laptop avahi-autoipd(wlan0)[7259]: client: RTNETLINK answers: No such process
May 28 21:38:44 emmi-laptop kernel: [  189.825962] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 28 21:38:44 emmi-laptop kernel: [  189.911825] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 28 21:38:44 emmi-laptop modprobe: WARNING: /etc/modprobe.d/blacklist line 41: ignoring bad line starting with '“blacklist' 
May 28 21:38:44 emmi-laptop dhclient: There is already a pid file /var/run/dhclient.pid with pid 7424
May 28 21:38:44 emmi-laptop dhclient: removed stale PID file
May 28 21:38:44 emmi-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.6
May 28 21:38:44 emmi-laptop dhclient: Copyright 2004-2007 Internet Systems Consortium.
May 28 21:38:44 emmi-laptop dhclient: All rights reserved.
May 28 21:38:44 emmi-laptop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
May 28 21:38:44 emmi-laptop dhclient: 
May 28 21:38:45 emmi-laptop dhclient: Listening on LPF/wlan0/00:1b:9e:1e:30:82
May 28 21:38:45 emmi-laptop dhclient: Sending on   LPF/wlan0/00:1b:9e:1e:30:82
May 28 21:38:45 emmi-laptop dhclient: Sending on   Socket/fallback
May 28 21:38:46 emmi-laptop dhclient: DHCPREQUEST of 192.168.1.149 on wlan0 to 255.255.255.255 port 67
May 28 21:38:54 emmi-laptop dhclient: DHCPREQUEST of 192.168.1.149 on wlan0 to 255.255.255.255 port 67
May 28 21:39:09 emmi-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May 28 21:39:16 emmi-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May 28 21:39:38 emmi-laptop kernel: [  222.599739] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 28 21:39:38 emmi-laptop modprobe: WARNING: /etc/modprobe.d/blacklist line 41: ignoring bad line starting with '“blacklist' 
May 28 21:39:38 emmi-laptop dhclient: There is already a pid file /var/run/dhclient.pid with pid 0
May 28 21:39:38 emmi-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.6
May 28 21:39:38 emmi-laptop dhclient: Copyright 2004-2007 Internet Systems Consortium.
May 28 21:39:38 emmi-laptop dhclient: All rights reserved.
May 28 21:39:38 emmi-laptop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
May 28 21:39:38 emmi-laptop dhclient: 
May 28 21:39:39 emmi-laptop dhclient: Listening on LPF/wlan0/00:1b:9e:1e:30:82
May 28 21:39:39 emmi-laptop dhclient: Sending on   LPF/wlan0/00:1b:9e:1e:30:82
May 28 21:39:39 emmi-laptop dhclient: Sending on   Socket/fallback
May 28 21:39:39 emmi-laptop dhclient: DHCPREQUEST of 192.168.1.149 on wlan0 to 255.255.255.255 port 67[/I][/B]

---

### Post by Alex J. on 2008-05-29
Yet MORE stuff. This is the output I got when I did the series of commands that imdano gave. 

emmi@emmi-laptop:~$ sudo ifconfig wlan0 up
emmi@emmi-laptop:~$ sudo iwconfig wlan0 essid "Jordan"
emmi@emmi-laptop:~$ sudo iwconfig wlan0 key [WEP key here]
emmi@emmi-laptop:~$ sudo iwconfig wlan0 key restricted
emmi@emmi-laptop:~$ sudo iwconfig wlan0 mode Managed
emmi@emmi-laptop:~$ dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted

---

### Post by sam_delta on 2008-05-29
> **Alex J. said:**
> Yet MORE stuff. This is the output I got when I did the series of commands that imdano gave. 

emmi@emmi-laptop:~$ sudo ifconfig wlan0 up
emmi@emmi-laptop:~$ sudo iwconfig wlan0 essid "Jordan"
emmi@emmi-laptop:~$ sudo iwconfig wlan0 key [WEP key here]
emmi@emmi-laptop:~$ sudo iwconfig wlan0 key restricted
emmi@emmi-laptop:~$ sudo iwconfig wlan0 mode Managed
emmi@emmi-laptop:~$ dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted
for the persmission problems, use the word "sudo" before the command making it look like this ```
sudo dhclient wlan0
```

sam

---

### Post by Alex J. on 2008-05-29
Oops. Yeah, sudo for that would be helpful. Here's the new stuff.

There is already a pid file /var/run/dhclient.pid with pid 16470
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1b:9e:1e:30:82
Sending on   LPF/wlan0/00:1b:9e:1e:30:82
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Alex J. on 2008-05-31
Any more help?

---

### Post by imdano on 2008-06-01
Are you able to connect consistently to open networks?  Everything so far points to a driver issue, particularly these popping up ```
May 28 21:39:38 emmi-laptop kernel: [ 222.599739] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```Driver issues are sort of out of my area of expertise, unfortunately.  All I can really suggest is searching the forums for your card model. :?

---

