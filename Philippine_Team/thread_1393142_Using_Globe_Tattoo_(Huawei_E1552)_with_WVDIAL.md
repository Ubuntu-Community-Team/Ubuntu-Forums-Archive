---
title: "Using Globe Tattoo (Huawei E1552) with WVDIAL"
date: 2010-01-29
forum: Philippine Team
---

### Post by fishfillet on 2010-01-29
Alam ko po na sobrang dali po itong isetup sa Network-Manager.

Pero ang problema po ay AYAW ko pong gumamit ng Network-Manager, ang balak ko pong gamitin ay WICD.

Un nga lang, walang utility si WICD para maconnect is Globe Tattoo.

So ang tingin kong puedeng gamitin ay WVDIAL.

Meron po bang makakatulong sa inyo na maibigay sa akin ng step by step paano mapagana ang Globe Tattoo via WVDIAL?

Eto po output ng lsusb

> Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 04f2:b044 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 1d57:ac01  
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Eto po output ng sudo wvdialconf

> Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- Manufacturer: huawei
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
ttyUSB2<*1>: Modem Identifier: ATI -- Manufacturer: huawei
ttyUSB2<*1>: Speed 9600: AT -- OK
ttyUSB2<*1>: Max speed is 9600; that should be safe.
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttyUSB0.
Modem configuration written to /etc/wvdial.conf.
ttyUSB0<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ttyUSB2<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

Eto naman po laman ng /etc/wvdial.conf

> [Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,&#8221;IP&#8221;,&#8221;http.globe.com.ph&#8221;
Stupid Mode = yes
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = *99#
Modem = /dev/ttyUSB0
Username = globe
Password = globe
Baud = 9600

At ang pinakamasakit, eto po ang output ng wvdial

> --> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,&#8221;IP&#8221;,&#8221;http.globe.com.ph&#8221;
AT+CGDCONT=1,b [1d]IPb [1d],b [1d]http.globe.com.phb [1d]
ERROR
--> Bad init string.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,&#8221;IP&#8221;,&#8221;http.globe.com.ph&#8221;
AT+CGDCONT=1,b [1d]IPb [1d],b [1d]http.globe.com.phb [1d]
ERROR
--> Bad init string.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,&#8221;IP&#8221;,&#8221;http.globe.com.ph&#8221;
AT+CGDCONT=1,b [1d]IPb [1d],b [1d]http.globe.com.phb [1d]
ERROR
--> Bad init string.


Salamat po!

---

### Post by vhinz on 2010-01-29
My wvdial.conf that works for me:

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","http.globe.com.ph",,0,0 
Baud = 9600
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = *99#
Password = globe
Username = globe
Stupid Mode = yes

I think parehas lang tayo.  But try to put the modem sa ibang saksakan ng USB...dahil baka nde un ung USB0.

---

### Post by Samhain13 on 2010-01-30
I suspect that "bad init string" is caused by:
```
Init3 = AT+CGDCONT=1,**”**IP**”**,**”**http.globe.com.ph**”**
```
Notice the *funky quotes*, replace them with normal quotes. I almost had my head checked when I copy-pasted some config from some blog and then encountered the same problem. :D

---

### Post by jepong on 2010-01-31
mali din number nyo... try nyo *99***1#

---

### Post by mocca101 on 2010-03-04
hi! im totaly a noob sa linux and sa ubuntu to be specific.
pwede po nyo i2ro ng step by step kung panu mpagana ang globe tatoo sa karmic koala ubuntu. i min from the start po tlaga. d ko kc magets ung nakapost d2 kc po ignorant pa tlga ako sa mga e2. Salamat sa mga magkakawang gawa..

---

### Post by acp_ on 2010-03-05
Here is my config and its working. try mo base dito

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
#Init3 = AT+CGDCONT=1,"IP","internet"
Init3 = AT+CGDCONT=1,"IP","http.globe.com.ph" 
Modem Type = USB Modem
ISDN = 0
Phone = *99#
New PPPD = yes
Modem = /dev/ttyUSB0   --> mag tail -f /var/log/message ka then place your globe tatoo see kong saan sya dev
#Modem = /dev/ttyACM1
Username = yourusername  ---> leave it as is
Password = yourpassword  ----> leave it as is
Baud = 460800
Idle Seconds = 3000
Auto DNS = 1
Stupid Mode = 1
Compuserve = 0
Baud = 460800
Dial Command = ATD
Ask Password = 0
FlowControl = NO

---

