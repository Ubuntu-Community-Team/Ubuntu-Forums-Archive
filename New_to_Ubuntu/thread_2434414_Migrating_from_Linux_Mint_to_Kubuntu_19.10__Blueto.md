---
title: "Migrating from Linux Mint to Kubuntu 19.10  Bluetooth problems"
date: 2020-01-05
forum: New to Ubuntu
---

### Post by 507panamagreg on 2020-01-05
Intermittent connection with bluetooth, choppy.   Been reading this is commonplace. Below is my result after running  dmesg | grep -i bluetooth in Konsole:

greg@greg-TravelMate-P243:~$ dmesg | grep -i bluetooth
[   20.242210] Bluetooth: Core ver 2.22
[   20.242234] Bluetooth: HCI device and connection manager initialized
[   20.242238] Bluetooth: HCI socket layer initialized
[   20.242240] Bluetooth: L2CAP socket layer initialized
[   20.242243] Bluetooth: SCO socket layer initialized
[   20.615549] Bluetooth: hci0: BCM: chip id 63
[   20.616544] Bluetooth: hci0: BCM: features 0x07
[   20.632557] Bluetooth: hci0: greg-TravelMate-P243
[   20.633555] Bluetooth: hci0: BCM20702A1 (001.002.014) build 0000
[   20.672991] bluetooth hci0: Direct firmware load for brcm/BCM20702A1-0489-e046.hcd failed with error -2
[   20.672995] Bluetooth: hci0: BCM: Patch brcm/BCM20702A1-0489-e046.hcd not found
[   33.035063] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   33.035066] Bluetooth: BNEP filters: protocol multicast
[   33.035074] Bluetooth: BNEP socket layer initialized
[   54.695632] Bluetooth: RFCOMM TTY layer initialized
[   54.695640] Bluetooth: RFCOMM socket layer initialized
[   54.695653] Bluetooth: RFCOMM ver 1.11

How do you update BCM: Patch brcm/BCM20702A1-0489-e046.hcd.  Been reading for a few days now and have yet to figure it out.  Please keep in mind a total newbie to Kubuntu.  Appreciate any help given.  Otherwise I like the layout of the program/functions.

---

