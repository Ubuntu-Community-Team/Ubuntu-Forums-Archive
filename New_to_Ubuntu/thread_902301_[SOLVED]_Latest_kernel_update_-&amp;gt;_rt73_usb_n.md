---
title: "[SOLVED] Latest kernel update -&amp;gt; rt73 usb no longer works"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by MegaJim on 2008-08-27
The clue's in the title.

Since the upgrade the rt73 no longer works - meaning it is detected properly, but network manager cannot seem to get it to connect to any network

I am able to use a different wireless card with ndiswrapper without difficulty (except for the fact that ndiswrapper can only connect to unsecured networks).

It was pretty good before, but now without the ability to connect to encrypted networks i'm in a bit of a pickle.

---

### Post by swegner on 2008-08-27
I was having similar trouble with my iwp2200 card.  Is this the kernel update from hardy-proposed?

The solution for me was to remove the hardy-proposed repository, remove the kernel package (linux-image-###-generic), and then reinstall virtual packages linux-generic and linux-image-generic.

This should probably be submitted as a bug, but I didn't have time to gather information.

---

### Post by knattlhuber on 2008-08-27
> **MegaJim said:**
> The clue's in the title.

Since the upgrade the rt73 no longer works - meaning it is detected properly, but network manager cannot seem to get it to connect to any network

I am able to use a different wireless card with ndiswrapper without difficulty (except for the fact that ndiswrapper can only connect to unsecured networks).

It was pretty good before, but now without the ability to connect to encrypted networks i'm in a bit of a pickle.

The Network Manager applet sometimes causes problems. I had an incredibly slow connection using Hardy and an RT73-based USB adpater (D-Link WUA 2340). After installing [Wicd]("http://wicd.sourceforge.net/") (which automatically uninstalls the NWM applet), everything worked just fine.

---

### Post by MegaJim on 2008-08-27
Pretty sure wicd doesn't have VPN support yet and this is essential for me at the moment.

The kernel update was not from the proposed, but the default repositories for 8.04

---

### Post by swegner on 2008-08-27
Hmmm, interesting.  There's a few things you can do to find more info.  In particular, check the system logs and find information related to your wireless card.  For a GUI, you can go to System > Administration > System Log.  Or, from the command-line:

```
grep "rt73" /var/log/*
```

Another option is to try stopping and restarting the kernel module:
```
sudo modprobe -r rt73
sudo modprobe rt73
```

This is assuming "rt73" is the actual name of the kernel module.  You may need to vary your commands slightly.

---

### Post by MegaJim on 2008-08-28
from syslog:
```
Aug 28 12:29:19 cerberus kernel: [ 2499.330950] usbcore: registered new interface driver rt73usb
Aug 28 12:29:19 cerberus NetworkManager: <debug> [1219922959.149192] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_0e_2e_9f_7e_26'). 
Aug 28 12:29:19 cerberus NetworkManager: <debug> [1219922959.210235] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_0e_2e_9f_7e_26_0'). 
Aug 28 12:29:19 cerberus kernel: [ 2499.514714] ADDRCONF(NETDEV_UP): wlan1: link is not ready
Aug 28 12:29:19 cerberus NetworkManager: <info>  wlan1: Device is fully-supported using driver 'rt73usb'. 
Aug 28 12:29:19 cerberus NetworkManager: <info>  wlan1: driver supports SSID scans (scan_capa 0x01). 
Aug 28 12:29:19 cerberus NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Aug 28 12:29:19 cerberus NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Aug 28 12:29:19 cerberus NetworkManager: <info>  Now managing wireless (802.11) device 'wlan1'. 
Aug 28 12:29:19 cerberus NetworkManager: <info>  Deactivating device wlan1. 
```

from kern.log:
```
Aug 28 12:28:51 cerberus kernel: [ 2472.075959] usb 4-3: new high speed USB device using ehci_hcd and address 5
Aug 28 12:28:52 cerberus kernel: [ 2472.347171] usb 4-3: configuration #1 chosen from 1 choice
Aug 28 12:28:52 cerberus kernel: [ 2472.500927] phy4 -> rt2500usb_init_eeprom: Error - Invalid RT chipset detected.
Aug 28 12:28:52 cerberus kernel: [ 2472.500942] phy4 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
```

It seems there is a problem with that driver.

I don't know if rt2500usb is connected to this device in some way or is part of the driver set, but the network card itself has always worked using the rt73usb driver.

Perhaps I need to uninstall/reinstall the driver? (its the one that ships with ubuntu) or build the serialmonkey driver for the rt73?

The only problem is that I can't get the necessary packages to build the driver without being connected, and the only connection I can use only supports port 80.  Is there a way to change apt-get to use port 80 to update?

---

### Post by MegaJim on 2008-08-28
Well I tried building/installing the serialmonkey drivers from source and have the same issue.

Perhaps I can get wpa_supplicant to work with my other network card in ndiswrapper - at the moment it keeps failing on any secured network :(

from kern.log:
```
Aug 28 13:19:13 cerberus kernel: [ 5493.113657] ndiswrapper (iw_set_freq:334): setting configuration failed (C0010015)
```

---

### Post by swegner on 2008-08-28
I did a quick Google search on the log output you posted, and came up with a couple hits.  In particular:

[launchpad bug #249242]("https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/249242")

The solution seems to imply that the actual problem was memory corruption-- is it possible that your memory (or some other hardware) may be going bad?  It might be a good idea to do a memtest.

Also, can you post exactly which kernel and package version you are using?
```
apt-cache show linux-image-`uname -r` | grep "^Version"
```

You can also try booting into a previous kernel.  When you reboot, select a previous entry from the GRUB menu.  (If you don't see the GRUB menu, you will need to press "Esc" during the boot process to get it.)

---

### Post by MegaJim on 2008-08-28
Version: 2.6.24-19.41

I have back to 2.6.24-16, but that doesn't work either.

I'll try a memtest when I'm not so busy with work on this laptop :)

I will also try to blacklist the rt2500 driver just incase this allows it to work.

---

### Post by MegaJim on 2008-08-28
The dongle doesn't seem to work under my other OS (windows) which indicates the problem might well be on that end.  I will try it on my main box (also running 8.04) at home tonight and see if it works there - my main box has been off the internet for a month and the dongle was its connector, so if it doesn't work there (even just to detect some networks of which there are plenty in the area) then i'll know its a faulty dongle.

---

### Post by MegaJim on 2008-09-13
Confirmed this was a faulty dongle, and no fault with Ubuntu.  Closing the thread.

---

