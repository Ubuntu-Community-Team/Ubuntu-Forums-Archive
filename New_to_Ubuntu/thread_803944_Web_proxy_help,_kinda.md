---
title: "Web proxy help, kinda"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by dynamethod on 2008-05-22
Hey there


Basically the deal is i have a LAN at our student accomodation, thers about 5 of us, and im about the only one on the LAN that has any clue about IT in general, and the net connection is under my name


lately some of the guys on the network have found out about torrents... now there using up the monthly cap like nobodys buisness, ive warned them, but they seed without realising, so ok whatever, basically im wondering if theres someway where i can router everyones connection through my pc, with some sort of login interface which they have to login in through to get to the router via my computer, and somehow then log their traffic, like how much they use etc etc, and i can then set a daily cap for everyone, like some sort of web proxy, is this possible at all? any help much appreciated

---

### Post by dynamethod on 2008-05-22
using a Dynalink RTA1025W router btw

---

### Post by dynamethod on 2008-05-24
well i found out about this program called squid,

i sudo apt-get install squid,

i get this:

```
Setting up squid (2.6.18-1ubuntu3) ...
Creating squid spool directory structure
FATAL: Could not determine fully qualified hostname.  Please set 'visible_hostname'

Squid Cache (Version 2.6.STABLE18): Terminated abnormally.
CPU Usage: 0.000 seconds = 0.000 user + 0.000 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0
Aborted
Restarting Squid HTTP proxy: squid* Creating squid spool directory structure
FATAL: Could not determine fully qualified hostname.  Please set 'visible_hostname'

Squid Cache (Version 2.6.STABLE18): Terminated abnormally.
CPU Usage: 0.004 seconds = 0.004 user + 0.000 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0
Aborted
FATAL: Could not determine fully qualified hostname.  Please set 'visible_hostname'

Squid Cache (Version 2.6.STABLE18): Terminated abnormally.
CPU Usage: 0.000 seconds = 0.000 user + 0.000 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0
Aborted
 failed!


```

i dont really know what to do about this

---

### Post by dynamethod on 2008-05-24
i see it complaining about a "visible hostname" so i changed that part of the squid.conf file to this:



#  TAG: visible_hostname darksun
#	If you want to present a special hostname in error messages, etc,
#	define this.  Otherwise, the return value of gethostname()
#	will be used. If you have multiple caches in a cluster and
#	get errors about IP-forwarding you must set them to have individual
#	names with this setting.
#
#Default:
# none


because darksurn is my hostname, still complains though

---

