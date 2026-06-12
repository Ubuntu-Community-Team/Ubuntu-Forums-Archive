---
title: "[SOLVED] USB isn't working at all"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by vvvladut on 2008-08-23
I didn't do anything out of the ordinary, and I just discovered that USB is not working at all. I can't plug in any device (well I can, but nothing at all happens).

This is my *lsusb* output:
```

Bus 004 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```

Logitech must be the wireless mouse and keyboard set, and the Cypress Semiconductor thing must be the USB hub inside my monitor. The mouse and keyboard are working, but nothing else I plug in does. I tried plugging in the same devices in XP and they all work just fine.

Any idea what I can do?

---

### Post by prshah on 2008-08-23
> **vvvladut said:**
> 
just discovered that USB is not working at all. I can't plug in any device (well I can, but nothing at all happens).


Can you post the output of lsusb _after_ plugging in a couple of devices? Also ```
sleep 5 && dmesg | tail
``` after plugging in devices.

---

### Post by vvvladut on 2008-08-28
Something weird happened. I plugged in a card reader, then ran lsusb. It provided the same output as before, but immediately after, the card reader (with a SD card in it) was recognized and mounted! I ran lsusb again and there it is, first one on the list:

```
Bus 004 Device 004: ID 0781:b2b5 SanDisk Corp.
Bus 004 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```

I pulled it out, tried a USB stick, same thing: it won't work unless I run lsusb.

Why can't Ubuntu mount my USB devices automatically? It used to do this until a few days ago... What can I do?

The second piece of code provided this:

```
[ 1198.455758] sd 4:0:0:0: [sdc] Write Protect is off
[ 1198.455766] sd 4:0:0:0: [sdc] Mode Sense: 00 26 00 00
[ 1198.455769] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 1198.458983] sd 4:0:0:0: [sdc] 1015808 512-byte hardware sectors (520 MB)
[ 1198.462099] sd 4:0:0:0: [sdc] Write Protect is off
[ 1198.462107] sd 4:0:0:0: [sdc] Mode Sense: 00 26 00 00
[ 1198.462110] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 1198.462121]  sdc: sdc1
[ 1198.463103] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[ 1198.463182] sd 4:0:0:0: Attached scsi generic sg4 type 0
```

---

### Post by vvvladut on 2008-09-02
...anyone?...

---

### Post by vvvladut on 2008-09-06
bump

---

### Post by cwmoser on 2008-09-06
I just started playing with a 7 port USB hub and was having problems too.

What I found from searching the web is that there is bug in the current Linux kernel dealing with "ehci-hcd" and should be fix with the 2.6.27 kernel.  I have Ubuntu Hardy and it uses kernel 2.6.24.

A temporary fix is to issue this:

sudo  modprobe  -r  ehci-hcd

every time you boot Ubuntu.  What I read is that ehci-hcd handles USB 2.0 and without ehci-hcd you will have degraded to USB 1.1.

Also, I found that while my two USB thumb drives and camera Smart Media reader works just fine in my new USB Hub, I found that neither of my USB hard drives would work.  So, for the time being, I got my USB hard drives connected to direct ports in my PC - i.e. not using the hub.

Carl

---

### Post by vvvladut on 2008-09-13
> **cwmoser said:**
> Also, I found that while my two USB thumb drives and camera Smart Media reader works just fine in my new USB Hub, I found that neither of my USB hard drives would work.  So, for the time being, I got my USB hard drives connected to direct ports in my PC - i.e. not using the hub.


Neither my direct ports nor my USB hub work, unless I run lsusb first. After I do, that, they all work just fine.

Guess I'll have to wait for kernel 2.6.27 then...

---

