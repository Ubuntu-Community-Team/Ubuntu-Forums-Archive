---
title: "installation  of additional drivers fails"
date: 2012-05-08
forum: New to Ubuntu
---

### Post by chatur on 2012-05-08
while updating additional drivers  installation  fails and gives message

Please have a look at the log file for details: /var/log/jockey.log

in Dell Studio-1558........How to fix??

---

### Post by 2F4U on 2012-05-08
What kind of drivers do you attempt to update? If it is for the ATI drivers, I once had a similar problem, but after a reboot I recognized that the drivers were installed properly.

---

### Post by Mark Phelps on 2012-05-08
Obviously, without seeing the contents of the log file, we can't possibly answer your question...

---

### Post by aciddesir on 2012-05-30
I had this same problem trying to activate the broadcom STA driver.  And the log, amongst other things, was giving me this:

```
<jockey.detection.OpenPrintingDriverDB instance at 0xb68d69cc> about HardwareID('modalias', 'pci:v00001022d00007804sv00001025sd0000059Fbc01sc06i01')
2012-05-29 23:49:23,516 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68d69cc> about HardwareID('modalias', 'wmi:83B9D139-CE71-45DB-A7A6-2628D3A65F4C')
2012-05-29 23:49:23,517 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68d69cc> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,BF,CA,CB,E3,ED,EE,F0,ram4,lsfw')
2012-05-29 23:49:23,517 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68d69cc> about HardwareID('modalias', 'input:b0003v058FpB002e0002-e0,1,kD4,ramlsfw')
2012-05-29 23:49:23,517 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb68d69cc> about HardwareID('modalias', 'wmi:FE1DBBDA-3014-4856-870C-5B3A744BF341')
2012-05-29 23:49:23,597 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-29 23:49:23,598 DEBUG: fglrx_updates is not the alternative in use
2012-05-29 23:49:23,704 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-29 23:49:23,777 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-29 23:49:23,778 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-05-29 23:49:24,387 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-29 23:49:24,387 DEBUG: fglrx_updates is not the alternative in use
2012-05-29 23:49:24,493 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-29 23:49:24,493 DEBUG: fglrx_updates is not the alternative in use
2012-05-29 23:49:24,529 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-29 23:49:24,594 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other
```

---

### Post by Mark Phelps on 2012-05-30
> **aciddesir said:**
> I had this same problem trying to activate the broadcom STA driver.  And the log, amongst other things, was giving me this:


That's nice ... but it's been WEEKS now, and the OP has failed to respond.  We're not mind readers here.  IF folks won't help us out with detailed info, we can't help them fix their problems.

---

