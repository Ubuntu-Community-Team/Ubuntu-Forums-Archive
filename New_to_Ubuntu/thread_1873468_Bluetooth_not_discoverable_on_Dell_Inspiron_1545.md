---
title: "Bluetooth not discoverable on Dell Inspiron 1545"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by harvindercs on 2011-11-01
Hello, my bluetooth is not working and it is not discoverable, from this forum i found that my Radio is off.
but how do i turn it ON?
here are some commands and solutions which i tried and i am using Ubuntu 11.10 on DELL Inspiron-1545
i am attaching a screen-shot of the commands which i used(found on this forum)
output for command hciconfig -a is 
```
 harry@harry-Inspiron-1545:~$ hciconfig -a
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 00:24:2B:FE:A1:26  ACL MTU: 1021:8  SCO MTU: 64:1
    UP RUNNING PSCAN ISCAN 
    RX bytes:1050 acl:0 sco:0 events:33 errors:0
    TX bytes:883 acl:0 sco:0 commands:33 errors:0
    Features: 0xff 0xff 0x8f 0xfe 0x9b 0xff 0x79 0x83
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF PARK 
    Link mode: SLAVE ACCEPT 
    Name: 'harry-Inspiron-1545-0'
    Class: 0x4a0100
    Service Classes: Networking, Capturing, Telephony
    Device Class: Computer, Uncategorized
    HCI Version: 2.1 (0x4)  Revision: 0x50ad
    LMP Version: 2.1 (0x4)  Subversion: 0x423d
    Manufacturer: Broadcom Corporation (15)

```
[IMG]http://i41.tinypic.com/2b751k.png[/IMG]
[IMG]http://ubuntuforums.org/%3Ca%20href=%22http://www.flickr.com/photos/harry_harvinder/6302422529/%22%20title=%22Selection_005%20by%20Harry_Harry,%20on%20Flickr%22%3E%3Cimg%20src=%22http://farm7.static.flickr.com/6215/6302422529_c6e6bfa942.jpg%22%20width=%22500%22%20height=%22321%22%20alt=%22Selection_005%22%3E%3C/a%3E[/IMG]
[IMG]http://www.flickr.com/photos/harry_harvinder/6302422529/[/IMG]

---

### Post by LowSky on 2011-11-02
sudo service bluetooth restart

if that don't work see this

[http://ubuntuforums.org/showpost.php?p=10448661&postcount=5](http://ubuntuforums.org/showpost.php?p=10448661&postcount=5)

---

### Post by Denny Myself on 2011-11-18
My Inspiron 1545 bluetooth has not worked since I installed Ubuntu 10.10. Most forums suggest fiddling with the ROM (no chance that is gonna happen)or install windows (not an option). I tried 4 distros before I finally gave up on the bluetooth ever working. Has any dell user managed to get their bluetooth going.. this is the result of lsusb.


denis@Denis-Inspiron-1545:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 005: ID 1c4f:0003 SiGma Micro HID controller
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 413c:8162 Dell Computer Corp. 
Bus 003 Device 003: ID 413c:8161 Dell Computer Corp. 
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

HELP!!!

---

