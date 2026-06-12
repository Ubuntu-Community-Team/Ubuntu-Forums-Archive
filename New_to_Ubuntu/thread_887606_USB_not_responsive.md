---
title: "USB not responsive"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by jfcous on 2008-08-12
I've upgraded to 8.04 on an IBM T-42 Laptop with dual boot.  My USB port(s) work with my printer but will not read a flash drive and will not recognize my palm pilot (Palm TX and jpilot).  The output from lsusb is:

Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

I'm very much a newbie and found the above command on this forum.  Any suggestions would be appreciated.

---

### Post by cmnorton on 2008-08-12
I just rebooted my T61p; looked in the BIOS; and cannot see anything that you would need to set, because you have USB already.

Here us my lsusb output:

Bus 007 Device 001: ID 0000:0000
Bus 006 Device 005: ID 050d:0119 Belkin Components
Bus 006 Device 004: ID 04b3:4485 IBM Corp.
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 003: ID 0a5c:2110 Broadcom Corp.
Bus 001 Device 001: ID 0000:0000

I believe Bus 006/Device 005 is my KVM switch. One of those could be the Thinkpad docking station.

I ran lsusb again during a Palm Synch:

Bus 007 Device 001: ID 0000:0000
Bus 006 Device 005: ID 050d:0119 Belkin Components
Bus 006 Device 004: ID 04b3:4485 IBM Corp.
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 0830:0070 Palm, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 003: ID 0a5c:2110 Broadcom Corp.
Bus 001 Device 001: ID 0000:0000

Both Kubuntu and Ubuntu have pretty good Palm synching. I happen to get gnome-pilot installed through Kubuntu, probably because I use Evolution. Try synching that way.

---

### Post by jfcous on 2008-08-12
Thanks for the suggestion - i'm on my way out but I will try Evolution sync later.

---

### Post by jfcous on 2008-08-12
Evelution sync did not work - still unable to sync palm pilot.

---

### Post by cmnorton on 2008-08-13
When I set up Evolution, it prompted me to make sure a kernel module was installed for "old" style synching. I believe it was the visor module. Is that loaded?

---

