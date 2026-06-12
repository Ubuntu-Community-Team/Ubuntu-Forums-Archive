---
title: "Garmin WebUpdater (Wine installed) can't find Nuvi 3490"
date: 2013-05-07
forum: New to Ubuntu
---

### Post by todorakiggg on 2013-05-07
Guys,
I am relatively new to Ubuntu but I definitely would like to continue using it. The last set up that I need to make to my system is to make my new installation of Ubuntu 13.04 to connect to Garmin_GPS as serial device. I need this because I want to make Garmin WebUpdater to connect to the Nuvi 3490. Garmin software is installed under **Wine **and normally I am able to start it and so on, but it can't find the GPS device. 
I read some manual on the internet that there should be some information for the port where the device is connected, but when I try to read the file there is not
ls -l  /dev/ttyUSB* created and I can't connect it with Garmin WebUpdater
Based on the readings I made here is what I did so far:

[LIST=1]
[*]Garmin_GPS was removed from the blacklist
[*]This is what I get with dmesg:

**dmesg | grep -i garmin**
```

[  199.194772] usb 1-1.2: Manufacturer: Garmin
[  211.375501] scsi 7:0:0:0: Direct-Access     Garmin   nuvi Flash       1.00 PQ: 0 ANSI: 5
[  211.376116] scsi 7:0:0:1: Direct-Access     Garmin   nuvi SD Card     1.00 PQ: 0 ANSI: 5

```
[*]This is what I get with **lsusb**:
```

 lsusb 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
Bus 003 Device 002: ID 0930:0219 Toshiba Corp. 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
[B]Bus 001 Device 005: ID 091e:2560 Garmin International 
[/B] Bus 001 Device 003: ID 04f2:b307 Chicony Electronics Co., Ltd
```
[*]I added this row in the following file:

**sudo gedit /etc/udev/rules.d/51-garmin.rules**
with content:

```
SYSFS{idVendor}=="091e", SYSFS{idProduct}=="2560", MODE="666"
```[/LIST]
but still I can't have Ubuntu start creating the ttyUSB file and I can't find which one is the serial port where the device is connected.

I have none of the popular gps programs installed (gpsd, gpsbabel and so on). Do you think that I have to have them installed as well, so the system will start creating the required information.

Aside of this the device is well recognised as mass storage device and I can see the content on it, but that's all and I can't get any further.

Any ideas on your side? :)

---

### Post by rburkartjo on 2013-05-08
i had a similar problem could get it to work with linux. i had to use my win7 partition. good luck. there might be an answer but i couldnt find it when i tried.

---

### Post by Cheesemill on 2013-05-08
AFAIK the Garmin WepUpdater software doesn't work with Wine, if you take a look at the Wine compatibility database then you can see that the only version that has been tested is 2.4.x which has a bronze rating (which means it doesn't work).
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=4871](http://appdb.winehq.org/objectManager.php?sClass=application&iId=4871)

If you want to be able to use this software from Linux then your only option is to run it in a Windows VM, but for this you will need a Windows license and its installation media to install the VM.

---

### Post by todorakiggg on 2013-05-09
Here is some update to the issue:

Garmin new devices do not support Serial Device mode. (Garmin made this for the new devices for good :) ) They only support Mass Storage, which is how actually the GPS is recognised by Ubuntu.
In order to make Garmin WebUpdater find the nuvi, you have to make some settings in Winecfg. On Driver's tab (when nuvi is connected to the PC) you will see a drive letter for the nuvi. Click on it, then click below on advanced options and change type of the device. You have to select it to be **Floppy **(no kidding), this is the only way that Garmin WebUpdater finds the nuvi, and I got it to work this way.
Changing the type of the device for some reason is not becoming permanent for me (some users report this issue as well) and I had to do it every time I want to connect to the Nuvi. So far so good you would say, but not....
As **cheesemill **reported Garmin WebUpdater is crashing after finding the nuvi and going further to find if there are any available additional updates (voices, languages and so on).
So I guess we will have to wait until Garmin issues a newer version and give it a try again... or even better they start supporting Linux as well ....

---

### Post by squakie on 2013-05-09
To get around doing this every time, you can use a udev rule (and possibly a shell script it can call) to do it for you.  Also, if the device is connected via USB I'm surprised you get anywhere - wine may have changed, but it never supported USB devices (outside of your keyboard, mouse and possibly a printer).

---

### Post by todorakiggg on 2013-05-10
Thanks for this advice, I did not go in the direction of udev rules and scripts because anyway WebUpdater is crashing.
I agree with you about wine, as I said you have to fool Wine, that actually the device is a _floppy_, this way it connects to it properly...

---

