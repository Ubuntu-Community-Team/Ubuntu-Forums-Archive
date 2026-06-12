---
title: "Network disconnected - you are now offline"
date: 2012-12-13
forum: New to Ubuntu
---

### Post by OmarR on 2012-12-13
I have just installed Ubuntu and have no idea how to connect to the internet. I have no idea about linux. All I know is that ever since I've first logged in, I have gotten this message "**Network** disconnected - you are now offline". Networking is enabled.

---

### Post by asifnaz on 2012-12-13
what kind of internet connection you have...?

---

### Post by OmarR on 2012-12-13
I've got an 8Mbps wifi connection

---

### Post by GordThompson on 2012-12-13
In System Settings (icon on the dock with a gear and a wrench, or just search for "System Settings") click the "Additional Drivers" icon in the Hardware section. See if a wireless adapter driver shows up in the list of available drivers.

---

### Post by bogan on 2012-12-13
Hi!,** OmarR**,

**Gordthomson **Posted.> . , , ,just search for "System Settings") click the "Additional Drivers" icon in the Hardware section. If you are running  Ubuntu 12.10, then 'Additional Drivers', is in on the right hand Tab of System Settings>System>Software Sources. You can also get there by Right-Clicking on the Desktop Screen, select: 'Change Desktop Background' and the: 'All Settings' Tab.

You Posted: "  Networking is enabled." there should be a 'tick' against: 'Enable Networking', and under it, in the drop-down menu, another 'tick' against: 'Enable Wireless'.

The Network manager Icon varies by the version and flavour of Linux you are running - if you do not know: ```
uname -r 
cat /etc/lsb-release
``` In a terminal, ['Ctrl+Alt+t'] will tell you', - Most likely is a Fan or Shell shaped symbol representing a radio wave.

If Network Manager is scanning for a network a series of chords will move up the icon, Does that happen?

If connection is found the Fan will be full of chords and a Left-Click on the icon will list the networks found, you may need to select the one you want to connect to., and edit the connection. Post if you need more detailed instructions.

If the icon is different it may show one or two blobs rotating, or show two miniature screen symbols.

Please Post results of the above & we can take it from there.

Chao!, **bogan**.

---

### Post by OmarR on 2012-12-14
Hey thanks a lot guys but it shows "this device is not working." above "using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source(proprietary)" I  think I saw a similar thread and ran a command in the terminal so it may have something to do with that.
If I don't have the drivers, how can I get them? Don't I have to go online to get the drivers - I think I can use a USB to transfer them

---

### Post by OmarR on 2012-12-14
> **bogan said:**
> Hi!,** OmarR**,

**Gordthomson **Posted.If you are running  Ubuntu 12.10, then 'Additional Drivers', is in on the right hand Tab of System Settings>System>Software Sources. You can also get there by Right-Clicking on the Desktop Screen, select: 'Change Desktop Background' and the: 'All Settings' Tab.

You Posted: "  Networking is enabled." there should be a 'tick' against: 'Enable Networking', and under it, in the drop-down menu, another 'tick' against: 'Enable Wireless'.

The Network manager Icon varies by the version and flavour of Linux you are running - if you do not know: ```
uname -r 
cat /etc/lsb-release
``` In a terminal, ['Ctrl+Alt+t'] will tell you', - Most likely is a Fan or Shell shaped symbol representing a radio wave.

If Network Manager is scanning for a network a series of chords will move up the icon, Does that happen?

If connection is found the Fan will be full of chords and a Left-Click on the icon will list the networks found, you may need to select the one you want to connect to., and edit the connection. Post if you need more detailed instructions.

If the icon is different it may show one or two blobs rotating, or show two miniature screen symbols.

Please Post results of the above & we can take it from there.

Chao!, **bogan**.
Networking is enabled and yes there is a tick, but above that, it says Wired Network disconnected" (above VPN)

---

### Post by OmarR on 2012-12-14
No Bogan, the chords do not move up and down the shell symbol. That does happen when I connect the ethernet cable.. It still doesn't connect though.

---

### Post by GordThompson on 2012-12-14
Run the following command in a Terminal window and tell us what it says:

```
nm-tool
```

---

### Post by OmarR on 2012-12-15
State: disconnected
- Device: eth0 -----------------------------------------------------------
  Type:                Wired
  Driver:              r8169
  State:               unavailable
  Default:             no
  HW Address:          B8:AC:6F:57:FD:FB

  Capabilities:
    Carrier redirect:  yes

  Wired Properties
    Carrier:           off

---

### Post by GordThompson on 2012-12-15
Based on the experiences of *many* other posters, here is what you'll most likely need to do:

Connect your machine to the internet using the wired network connection (Ethernet cable), then use...

System Settings / Hardware / Additional Drivers

...to install the STA driver for your Broadcom wireless adapter.

---

