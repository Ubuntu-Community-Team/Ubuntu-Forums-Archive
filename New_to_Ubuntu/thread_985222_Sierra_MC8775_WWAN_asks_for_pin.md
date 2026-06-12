---
title: "Sierra MC8775 WWAN asks for pin"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by BC7333 on 2008-11-17
Have a laptop with Sierra MC8775

The network manager configuration wizard detected the device, but when trying to use it it asks for the pin.  I put in the sim card pin but it just keeps asking.. and asking.. and asking...

Here some output dmesg, lsusb etc....

Any ideas?

Huge thanks to any and all...

```

brian@brian-flybook:~$ dmesg | grep tty
[    0.004000] console [tty0] enabled
[  734.822546] usb 3-2: Sierra USB modem converter now attached to ttyUSB0
[  734.822724] usb 3-2: Sierra USB modem converter now attached to ttyUSB1
[  734.822897] usb 3-2: Sierra USB modem converter now attached to ttyUSB2
[  921.491110] sierra ttyUSB0: Sierra USB modem converter now disconnected from ttyUSB0
[  921.494083] sierra ttyUSB1: Sierra USB modem converter now disconnected from ttyUSB1
[  921.497183] sierra ttyUSB2: Sierra USB modem converter now disconnected from ttyUSB2
[ 1062.592350] usb 3-2: Sierra USB modem converter now attached to ttyUSB0
[ 1062.594195] usb 3-2: Sierra USB modem converter now attached to ttyUSB1
[ 1062.596301] usb 3-2: Sierra USB modem converter now attached to ttyUSB2
brian@brian-flybook:~$ sudo wvdialconf
[sudo] password for brian: 
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- MC8775V
ttyUSB0<*1>: Speed 9600: AT -- OK
ttyUSB0<*1>: Max speed is 9600; that should be safe.
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB2<*1>: ATQ0 V1 E1 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB2<*1>: Modem Identifier: ATI -- Manufacturer: Sierra Wireless, Inc.
ttyUSB2<*1>: Speed 9600: AT -- OK
ttyUSB2<*1>: Max speed is 9600; that should be safe.
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttyUSB0.
Modem configuration written to /etc/wvdial.conf.
ttyUSB0<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ttyUSB2<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
brian@brian-flybook:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 1199:6812 Sierra Wireless, Inc. MC8775 Device
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
brian@brian-flybook:~$ 
```

---

### Post by BC7333 on 2008-11-20
Well, as long as I'm 'bumping'.. might as well go on a rant.

Ubuntu, I love it..  Would be absolutely fantastic if the world was hard wired, without wireless and stuff like WWAN.

When it comes to OTA networking though, my experience over the last year and a half is that it really is lacking.  Network Manager has never really worked well and even with iwl3945 and networking built into the kernel etc that good old ipw driver with ndiswrapper still works better.

Oh well.. there is hope.. I hope..

---

### Post by BC7333 on 2008-11-21
Maybe I should be posting this in another fourm?

---

### Post by casey02 on 2009-09-27
Bro,

I believe tha is the initialize pin !!

---

### Post by t0p on 2009-09-27
The device asks for a pin... makes me think that when you bought the device, it came with a pin.  Have you used this device before?

It may a pre-set, default pin.  Manufacturers aren't very imaginative when it comes to default pins (though they are getting better) so try some simple numbers like 0000 1111 2222 3333 1234 4321 9876 4567 etc etc.

Call the company who sold it to you or the manufacturer and ask them about default pins.  Because if you haven't changed it, then it will be the same now as when you bought it.

One other thing.   Does this device work okay in Windows without asking for a pin?  Use it with Windows, go into set up or whatever, and set the device to a new pin.  That way, when you try iy with ubuntu and it asks for a pin, you know what it is.

**EDIT:**  I just noticed this thtread dates from Nov 2008.  Why the hell did casey02 bring this up?

---

### Post by freechelmi on 2010-01-15
Hi, Can you confirm that your modem still works on 9.10 ? Sierra says it has a lot of problems which should be corrected for lucid

---

