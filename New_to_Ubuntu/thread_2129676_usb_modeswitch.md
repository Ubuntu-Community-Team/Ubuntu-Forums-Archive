---
title: "usb modeswitch"
date: 2013-03-26
forum: New to Ubuntu
---

### Post by capecrusader on 2013-03-26
Hi 
everyone out there 
i'm quite new to linux, i'm using ubuntu 12.04.
can anyone tell how to use usbmodswitch command in ubuntu coz i dont know how to use it ? I'm tring to install datacard in ubuntu 12.04.

on my terminal i type following command :

 Command : usb_modeswitch -W

Result :DefaultVendor=  not set
DefaultProduct= not set
TargetVendor=   not set
TargetProduct=  not set
TargetClass=    not set
TargetProductList=""

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
QisdaMode=0
GCTMode=0
KobilMode=0
SequansMode=0
MobileActionMode=0
CiscoMode=0
MessageEndpoint=  not set
MessageContent=""
NeedResponse=0
ResponseEndpoint= not set

InquireDevice enabled (default)
Success check disabled
System integration mode disabled

No default vendor/product ID given. Aborting.

Than i type the command

 usb_modeswitch -v 

Result :usb_modeswitch: option requires an argument -- 'v'

Every command with usbmodeswitch give similar type of error

can any body tell me what are the parameter for usb_modeswitch ;?
how to use mode switch ?
how to set defautl vendor ?

The output of lsusb command is followind

Command : lsusb

Result : 

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b159 Chicony Electronics Co., Ltd 
Bus 003 Device 002: ID 03f0:231d Hewlett-Packard 
Bus 002 Device 006: ID 12d1:1506 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard

---

### Post by Mark_in_Hollywood on 2013-04-01
Read this, maybe it will help: [http://ubuntuforums.org/showthread.php?t=1578311](http://ubuntuforums.org/showthread.php?t=1578311)

---

### Post by 3rdalbum on 2013-04-01
Are you absolutely sure you need to use usb-modeswitch by hand? It usually Just Works automatically once you've set up your device in Network Manager. Sometimes, the device will show up as a CD but still work fine as a modem.

Can I confirm that you've at least tried setting up the device in Network Manager and that it doesn't work at all this way? If if it doesn't work, have you tried installing a driver for it?

---

