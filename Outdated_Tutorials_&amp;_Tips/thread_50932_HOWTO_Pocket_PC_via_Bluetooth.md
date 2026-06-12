---
title: "HOWTO: Pocket PC via Bluetooth"
date: 2005-07-21
forum: Outdated Tutorials &amp; Tips
---

### Post by wisu on 2005-07-21
Refering to this nice HOWTO: Pocket PC Syncing with Evolution, and having bad experience syncing via cable specially with the hotplug scripts. 
I got my self a bluetooth dongle, it costs the same as a retractable sync cable. And here is how I got it up and running 

This howto uses a Bluetooth serial ports for connection.

1. Follow HOWTO: Pocket PC Syncing with Evolution
[http://ubuntuforums.org/showthread.php?t=30936](http://ubuntuforums.org/showthread.php?t=30936) additionally since I use Kubuntu, I added synce-kde

2. Install the following packages (personally I use kynaptic)
> bluez-hcidump
bluez-pin
bluez-utils

3. Plugin the bluetooth dongle and verify that (k)ubuntu likes it

> dmesg | grep Blue

output should look something like this

> Bluetooth: Core ver 2.7
Bluetooth: HCI device and connection manager initialized
Bluetooth: HCI socket layer initialized
Bluetooth: HCI USB driver ver 2.7
Bluetooth: L2CAP ver 2.7
Bluetooth: L2CAP socket layer initialized
Bluetooth: RFCOMM ver 1.5
Bluetooth: RFCOMM socket layer initialized
Bluetooth: RFCOMM TTY layer initialized

4. Edit file "/etc/bluetooth/hcid.conf"
change "Local device class" to either

> 0x104 (workstation)
0x108 (server)
0x10c (laptop)

5. Create file /etc/ppp/peers/dun

> nodefaultroute
noauth
local
192.168.131.102:192.168.131.201
ms-dns (your dns)
linkname synce-device

6. start the dund daemon,

> sudo dund --listen --msdun call dun

7. Register Serial Profile

> 
sudo sdptool add SP

8. Create a connection to your pocket pc, you first must have an existing partnership (previous howto) and make sure dccm is running.

Then on the Pocket PC goto Bluetooth Manager >> New >> ActiveSync via Bluetooth, follow the GUI to discover you Box and check the "ActiveSync partner" checkbox 

To connect the device, goto Bluetooth Manager and tap hold on the ActiveSync shortcut, choose connect. To disconnect tap hold the ActiveSync shortcut and choose disconnect. 

Since i use synce-kde, raki will play the famous connect tone once bluetooth connection is established or disconnected.

Upon connection, I use multisync to sync with Ximian Evolution 2. And I browse contents of my Pocket PC from my Kubuntu Box.

The synce-serial-start/abort command is no longer required.

don't forget to start the following commands upon boot
> 
/usr/bin/dund --listen --msdun call dun
/usr/bin/sdptool add SP
/usr/bin/dccm (not necessary if using **raki**)

Look Ma... No cables...
Now Pocket PC-ing with linux is much more enjoyable....

 :)

---

### Post by Atul_Singh on 2006-11-11
Dude you are great. I had a dell axim x30 which never worked with the serial connections. Now it works fine and I can sync. Thanks a lot.

---

### Post by CAFH on 2007-03-06
I've got a problem...
The connection is made, but when i open multisync and try to sync. it does nothing

---

### Post by cfmunster on 2008-03-10
Thanks for posting this guide. I have almost got everything working, but I have the same problem as CAFH. I can pair my device in the Bluetooth manager, and I can connect via Bluetooth from my pda Activesync window, but when I do, nothing is synced and the ActuveSync app quickly stops trying to sync. Any help is appreciated.

I am running Gutsy 32-bit and my device is a Verizon vx6800 with Windows Mobile 6. Any help anyone has is appreciated.

---

### Post by jrgns on 2008-05-13
It would help if someone could explain exactly what steps in the other HOWTO should be followed, and what should change.

I'm assuming that synce should connect to rfcomm0 (or whatever the bluetooth serial port is) instead of connection to ttyUSB0?

When I run synce-matchmaker create 1 it says the following:
```

[synce_info_from_file:51] unable to open file: /home/jrgns/.synce/active_connection
[rapi_context_connect:100] Failed to get connection info
[main:62] Failed to initialize RAPI

```

Whaddup?

---

### Post by Heiti567 on 2009-09-18
I would need a "how to" about connecting a windows mobile device (HTC Prophet) via bluetooth to synchronice calendar, contacts with evolution. I'm able to pair the devices but I'm not able to sync them via bluetooth. Connection is always refused. Im using ubuntu netbook remix 9.04 jaunty. Sync via usb cable is possible.
Thanks for help

---

