---
title: "lsusb shows hubs, but no power running to sockets"
date: 2012-12-05
forum: New to Ubuntu
---

### Post by raicho on 2012-12-05
Hi all

I have a bit of a weird problem I'm having trouble solving.  I've recently installed Lubuntu and after a little fiddling with the wireless thought it to be working flawlessly.

However having just tried to plug a USB stick in, it appears the sockets are all dead.  I've tried running lsusb and it shows the root hubs, but there doesn't seem to be any power running through the sockets.  It's not a physical issue as the BIOS boots from USB just fine.

Not much to go on I know, but if anyone has any generic suggestions to try I'm all ears!

Make/Model: HP Compaq Presario B1900
OS: Lubuntu 12.10

```
genshen@B1900:~$ sudo lsusb
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by cariboo on 2012-12-07
I'd suggest you open a terminal, and just after you have plug a usb device in, type:

```
dmesg | tail -n10
```

to see if the device is detected. The output should look something like this:

```
dmesg | tail -n10
[ 3878.488647] sd 5:0:0:0: [sdc] Write Protect is off
[ 3878.488652] sd 5:0:0:0: [sdc] Mode Sense: 43 00 00 00
[ 3878.489643] sd 5:0:0:0: [sdc] No Caching mode page present
[ 3878.489649] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 3878.496023] sd 5:0:0:0: [sdc] No Caching mode page present
[ 3878.496029] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 3878.497151]  **sdc: sdc1**
[ 3878.502767] sd 5:0:0:0: [sdc] No Caching mode page present
[ 3878.502772] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 3878.502775] sd 5:0:0:0: [sdc] Attached SCSI removable disk
```

Look for something similar to the portion that is in bold.

---

### Post by skullnbones on 2012-12-13
Bump 

I just bought a webcam and it seems like when I start it with cheese the usb my wireless  is connected to turns off and then the cam turns off as well.  No power.   I have to restart my computer in order for the wireless card to work again.  But as soon as I use the webcam it all turns off.

  I think it's an issue with power management to the usb ports but I can't find a solution either.

---

