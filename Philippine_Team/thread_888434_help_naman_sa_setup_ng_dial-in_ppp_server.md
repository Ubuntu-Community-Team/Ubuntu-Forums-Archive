---
title: "help naman sa setup ng dial-in ppp server"
date: 2008-08-13
forum: Philippine Team
---

### Post by papichulo on 2008-08-13
mga boss,

sana matulungan nyo ako dito. :)

gusto ko kasing ma-access yung linux box ko sa office through dial-up sa bahay., at makapag-surf na rin sa web.

56kpbs internal modem ang nakalagay sa linux box at na setup ko na rin ang drivers nito.

```

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S2   S3
WvModem<*1>: Cannot get information for serial port.
ttySL0<*1>: ATQ0 V1 E1 -- OK
ttySL0<*1>: ATQ0 V1 E1 Z -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttySL0<*1>: Modem Identifier: ATI -- SmartLink Soft Modem
ttySL0<*1>: Speed 4800: AT -- OK
ttySL0<*1>: Speed 9600: AT -- OK
ttySL0<*1>: Speed 19200: AT -- OK
ttySL0<*1>: Speed 38400: AT -- OK
ttySL0<*1>: Speed 57600: AT -- OK
ttySL0<*1>: Speed 115200: AT -- OK
ttySL0<*1>: Speed 230400: AT -- OK
ttySL0<*1>: Speed 460800: AT -- OK
ttySL0<*1>: Max speed is 460800; that should be safe.
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttySL0.
Modem configuration written to /etc/wvdial.conf.
ttySL0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

```

im using hardy heron 8.04, 
linux version = 2.6.24-19 generic

yun sanang step by step configuration para hindi nakakalito.

maraming salamat.

---

### Post by papichulo on 2008-08-13
up...up...up..

---

### Post by loell on 2008-08-13
[http://derrick-caluag.blogspot.com/2006/10/how-to-setup-dial-in-server-on-linux.html]("http://derrick-caluag.blogspot.com/2006/10/how-to-setup-dial-in-server-on-linux.html")

---

### Post by papichulo on 2008-08-19
> **loell said:**
> [http://derrick-caluag.blogspot.com/2006/10/how-to-setup-dial-in-server-on-linux.html]("http://derrick-caluag.blogspot.com/2006/10/how-to-setup-dial-in-server-on-linux.html")

yup..nabasa ko na..

at...

may mga slight changes na ata sa hardy!

wala na yung - /etc/inittab?

wala na yung - /etc/option.ttySx?

at hindi sya updated.

up...up...up...

---

