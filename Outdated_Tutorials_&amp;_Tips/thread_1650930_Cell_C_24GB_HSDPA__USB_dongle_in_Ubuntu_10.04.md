---
title: "Cell C 24GB HSDPA  USB dongle in Ubuntu 10.04"
date: 2010-12-22
forum: Outdated Tutorials &amp; Tips
---

### Post by CBrendan on 2010-12-22
Hi Guys

I recently purchased the HSPA+ USB dongle from Cell C with 24Gb data for 12 months.  Here is how you get it to work under Ubuntu 10.04.

Plug in your USB dongle.

Install "usb_modeswitch" (sudo apt-get install usb_modeswitch).

Run "sudo updatedb"

Locate "usb_modeswitch.conf" the file should be in /etc/usb_modeswitch.conf and add code below to the end of the file

```
########################################################
# Huawei E1752
#
# Contributor:
DefaultVendor=  0x12d1
DefaultProduct= 0x1446
TargetVendor=	0x12d1
TargetProduct=	0x1001
MessageEndpoint=	0x01
MessageContent=	"55534243000000000000000000000011060000000000000000000000000000"
```

Run "sudo usb_modeswitch"

This should say found one(1) device in the terminal

Then go System->Preferences->Network Connections and click on the "Mobile Broadband" tab.

Click "Add".  Check under "Create a connection for this mobile broadband device" that it lists "Huawei E1752" or something similar.

Select "South Africa" and "Cell-c" and plan "Default"
Click "Apply"

Then click on the new connection (Cell-c Default 1) you just added and click the "Edit" button.

There should be default info already in there.  Check "Connect Automatically" and "Available to all users"

Remove the username and enter your PIN.  This should be "0000" by default.

Left click on network connection icon on the top right and select (under Mobile broadband) Cell-c Default 1

A notification will popup to inform you that you're connected.

Start FireFox and browse.

---

