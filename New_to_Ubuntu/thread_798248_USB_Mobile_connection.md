---
title: "USB Mobile connection"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by megatronix on 2008-05-18
I have a Nokia S60 phone that uses DKU-2 cable. How do I connect this to the PC running Ubuntu 7.10. Please instruct me on the interface software I should use and what initial configuration I should use. Right now if I attach the phone through the cable it's not detected.:(

---

### Post by rraj.be on 2008-05-20
You need nothing like package or software specialy for this......

all are bbuilt in as default .....

follow this

-->open terminal

-->type

```
wvdialconf
```

--> it will show like 

```

Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

WvModem<*1>: Cannot set information for serial port.
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3
ttyACM0<Info>: Device or resource busy
Modem Port Scan<*1>: ACM0
WvModem<*1>: Cannot get information for serial port.
ttyACM1<*1>: ATQ0 V1 E1 -- OK
ttyACM1<*1>: ATQ0 V1 E1 Z -- OK
ttyACM1<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyACM1<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyACM1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyACM1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyACM1<*1>: Modem Identifier: ATI -- Sony Ericsson W200
ttyACM1<*1>: Speed 4800: AT -- OK
ttyACM1<*1>: Speed 9600: AT -- OK
ttyACM1<*1>: Speed 19200: AT -- OK
ttyACM1<*1>: Speed 38400: AT -- OK
ttyACM1<*1>: Speed 57600: AT -- OK
ttyACM1<*1>: Speed 115200: AT -- OK
ttyACM1<*1>: Speed 230400: AT -- OK
ttyACM1<*1>: Speed 460800: AT -- OK
ttyACM1<*1>: Max speed is 460800; that should be safe.
ttyACM1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found an USB modem on /dev/ttyACM1.
Modem configuration written to /etc/wvdial.conf.
/etc/wvdial.conf<Warn>: Can't write '/etc/wvdial.conf.tmp7097': Permission denied
/etc/wvdial.conf<Warn>: Can't write '/etc/wvdial.conf' ('/etc/wvdial.conf'): Bad file descriptor
ttyACM1<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
raj@raj-dworkstation:~$     
```

--> then open /etc/wvdial.conf as root bby typing 

```
sudo -i
gedit /etc/wvdial.conf
```

it will look like

```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
;Phone = <phone number>
;Password = <password>
;Username = <user name>

```

-->change it as

```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = *99***5#
Password = kk	
Username = kumar

```

where kk is my password, kumar is my user name and *99***5# is my mobile connection dialer number.


-->dont forget to remove  the semicolons
```
;Phone = <phone number>
;Password = <password>
;Username = <user name>
```

--> save it

in terminal type 

```
wvdial
```

it will  show as
 
```

WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT*99***5#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*99***5#
WvDial Modem<*1>: CONNECT
WvDial Modem<*1>: ~[7f]}#@!}!}!} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&} [1b]!Tv[1b]~
WvDial<*1>: Carrier detected.  Waiting for prompt.
WvDial Modem<*1>: ~[7f]}#@!}!}"} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&} [1b]!T:v~
WvDial<*1>: PPP negotiation detected.
WvDial<Notice>: Starting pppd at Tue May 20 20:20:22 2008
WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
WvDial<Err>: --> PAP (Password Authentication Protocol) may be flaky.
WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
WvDial<Err>: --> CHAP (Challenge Handshake) may be flaky.
WvDial<Notice>: Pid of pppd: 5707
WvDial<*1>: Using interface ppp0
WvDial<*1>: pppd: ø[06][08]
WvDial<*1>: pppd: ø[06][08]
WvDial<*1>: pppd: ø[06][08]
WvDial<*1>: pppd: ø[06][08]
WvDial<*1>: pppd: ø[06][08]
WvDial<*1>: pppd: ø[06][08]
WvDial<*1>: local  IP address 117.97.153.254
WvDial<*1>: pppd: ø[06][08]
WvDial<*1>: remote IP address 10.64.64.64
WvDial<*1>: pppd: ø[06][08]
WvDial<*1>: primary   DNS address 202.56.240.5
WvDial<*1>: pppd: ø[06][08]
WvDial<*1>: secondary DNS address 202.56.230.6
WvDial<*1>: pppd: ø[06][08]

```

dont close this terminal untill u close ur net connection..

if u close this ur net connection will be lost

enjoy:)

---

