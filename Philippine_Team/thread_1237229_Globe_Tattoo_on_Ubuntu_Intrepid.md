---
title: "Globe Tattoo on Ubuntu Intrepid"
date: 2009-08-11
forum: Philippine Team
---

### Post by gsmendoza on 2009-08-11
Hello,

I have just bought a globe tattoo modem. The model is Huawei E1552. I'm trying to make it work with my Ubuntu Intrepid laptop, but so far, plugging the modem does not add Globe Telecom to the Network applet.

I tried to follow the steps at [http://neildecapia.wordpress.com/2009/07/05/globe-tattoo-on-ubuntu-jaunty-9-04/]("http://neildecapia.wordpress.com/2009/07/05/globe-tattoo-on-ubuntu-jaunty-9-04/"), but as you can see, the steps there are for jaunty and not intrepid. Also, Huawei E1552 does not seem to be mentioned at [http://ubuntuforums.org/showthread.php?t=955538]("http://ubuntuforums.org/showthread.php?t=955538").

I appreciate any help on how I can troubleshoot this. Thanks.

Regards,
George

---

### Post by gsmendoza on 2009-08-11
FYI, I has some success before connecting the Ubuntu Intrepid laptop with smartbro prepaid. I followed the steps [here]("http://ubuntuforums.org/showthread.php?t=1017630").

---

### Post by loell on 2009-08-11
attach the usb modem, then type **lsusb** in the command line, post it here.

---

### Post by frustphil on 2009-08-11
I also had some success using it. Just play with the options in the Network Connections manager...

---

### Post by gsmendoza on 2009-08-11
> **loell said:**
> attach the usb modem, then type **lsusb** in the command line, post it here.

Thanks for the response. Here's what I have so far:

this is the lsusb

```

Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 005 Device 005: ID 12d1:1446 Huawei Technologies Co., Ltd. **
Bus 005 Device 003: ID 064e:c108 Suyin Corp. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

This is my usb_modeswitch.conf:

```

########################################################
# ZTE MF628+ (tested version from Telia / Sweden)
# ZTE MF626
#
# Contributor: Joakim Wennergren

DefaultVendor=  0x19d2
DefaultProduct= 0x2000

TargetVendor=   0x19d2
TargetProduct=  0x0031

MessageEndpoint=0x01
MessageContent="55534243123456782000000080000c85010101180101010101000000000000"

########################################################
# Huawei E220 (aka "Vodafone EasyBox II", aka "T-Mobile wnw Box Micro")
# Huawei E270
# Huawei E870
# and probably most other Huawei devices (just adapt product ID)
#
# Two options: 1. removal of "usb-storage"  2. the special control
# message found by Miroslav Bobovsky
#
# Contributor: Hans Kurent, Denis Sutter

;DefaultVendor=  0x12d1;
;DefaultProduct= 0x1446

# choose one of these:
# ;DetachStorageOnly=1
;HuaweiMode=1

```

The ZTE conf is for smartbro. The huawei is for globe tattoo.

This is the dmesg when I plug the modem:

```

[  330.637559] usb-storage: device scan complete
[  330.640802] scsi 11:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
[  330.642814] usb-storage: device scan complete
[  330.646183] scsi 10:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  330.649990] sd 11:0:0:0: [sdb] Attached SCSI removable disk
[  330.650389] sd 11:0:0:0: Attached scsi generic sg2 type 0
[  330.677591] sr1: scsi-1 drive
[  330.679165] sr 10:0:0:0: Attached scsi CD-ROM sr1
[  330.679984] sr 10:0:0:0: Attached scsi generic sg3 type 5
[  343.399306] ISO 9660 Extensions: Microsoft Joliet Level 1
[  343.420567] ISOFS: changing to secondary root

```

Finally, when I run sudo usb_modeswitch, I get this

```

gsmendoza@gsmendoza:/etc$ sudo usb_modeswitch 
[sudo] password for gsmendoza: 

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.6 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for target devices
 No target device found
Looking for default devices
 No default device found. Is it connected? Bye

```

---

### Post by GeorgeVita on 2009-08-11
Hi **gsmendoza**, as Intrepid creates a CDrom for the Huawei modem, can you try the **lsusb** command after ejecting it? It will probably switch to modem mode by itself without using any program.

To test it:

- Boot without the modem
- Attach the modem and **lsusb** after 15 seconds
- Use **dmesg** to see the actual sr**X** number of the CDrom
- From terminal: **sudo eject sr1** (or any other sr**X** from above)
- Wait 5 seconds and try again **lsusb**

If now you have a new ID (12d1:1234) check last lines of **dmesg** for any ttyUSBx port created. If not:
**sudo modprobe usbserial vendor=0x12d1 product=0x1234**
change 1234 with that shown at your last lsusb and check again **dmesg**

Final check of the /dev/ttyUSBx creation is: **ls /dev/ttyU***

Regards,
George

---

### Post by gsmendoza on 2009-08-12
Hi GeorgeVita,

I appreciate your help, I ejected the usb as you said but it did not change the lsusb. Here's the details of the test.

Thanks,
gsmendoza

> **GeorgeVita said:**
> 
- Boot without the modem
- Attach the modem and **lsusb** after 15 seconds


```

Bus 003 Device 004: ID 12d1:1446 Huawei Technologies Co., Ltd.

```

> **GeorgeVita said:**
> 
- Use **dmesg** to see the actual sr**X** number of the CDrom


```

[  300.637688] usb-storage: device scan complete
[  300.640665] usb-storage: device scan complete
[  300.640700] scsi 9:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
[  300.647175] scsi 8:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  300.651116] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[  300.653267] sd 9:0:0:0: Attached scsi generic sg2 type 0
[  300.682907] sr1: scsi-1 drive
[  300.684722] sr 8:0:0:0: Attached scsi CD-ROM sr1
[  300.685726] sr 8:0:0:0: Attached scsi generic sg3 type 5
[  313.397088] ISO 9660 Extensions: Microsoft Joliet Level 1
[  313.410087] ISOFS: changing to secondary root

```

> **GeorgeVita said:**
> 
- From terminal: **sudo eject sr1** (or any other sr**X** from above)
- Wait 5 seconds and try again **lsusb**


```

>> Bus 003 Device 004: ID 12d1:1446 Huawei Technologies Co., Ltd. 

```

The lsusb did not change.

> **GeorgeVita said:**
> 
If now you have a new ID (12d1:1234) check last lines of **dmesg** for any ttyUSBx port created. If not:
**sudo modprobe usbserial vendor=0x12d1 product=0x1234**
change 1234 with that shown at your last lsusb and check again **dmesg**


```

sudo modprobe usbserial vendor=0x12d1 product=0x1446

[  523.077421] usbcore: registered new interface driver usbserial
[  523.081535] usbserial: USB Serial support registered for generic
[  523.082370] usbcore: registered new interface driver usbserial_generic
[  523.082388] usbserial: USB Serial Driver core

```

> **GeorgeVita said:**
> 
Final check of the /dev/ttyUSBx creation is: **ls /dev/ttyU***


```

ls /dev/ttyU*
>> ls: cannot access /dev/ttyU*: No such file or directory

```

---

### Post by GeorgeVita on 2009-08-13
Hi **gsmendoza**,
can you try ideas form thread below?

[http://ubuntuforums.org/showthread.php?t=1211787](http://ubuntuforums.org/showthread.php?t=1211787)

It seems to be a very 'similar modem!

Regards,
George

---

