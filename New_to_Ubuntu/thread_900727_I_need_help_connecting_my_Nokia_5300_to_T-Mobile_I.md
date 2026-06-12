---
title: "I need help connecting my Nokia 5300 to T-Mobile Internet with wvdial"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by diablo75 on 2008-08-25
I've used wvdial many times to connect my laptop or PC to T-Mobiles Internet using wvdial.  I am currently trying to help my little sister use her phone to connect.  I've never used a nokia phone before.

Anyway, when I attach the cable, the phone asks me to designate a mode for the USB cable to function for:  Data, Printing and "Nokia Mode".  I put it in Nokia mode.

Next, I ran sudo wvdialconf, which detected the phone as a USB modem.

I modified the wvdial config as shown here:

```
[Dialer Defaults]
Modem = /dev/ttyACM0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = *99#
Username = tmobile
Password = tmobile
Init3 = AT+CGDCONT=1,"IP","internet2.voicestream.com";
Stupid Mode = 1
```

When I run wvdial with this config on my Motorola K1 KRZR, I connect just fine (I'm using it to post this right now).

But when I try to do the same thing with her nokia, I get this loop of attempts that I have to CTRL-C to kill):

```
carolyn@carolyn-desktop:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet2.voicestream.com";
AT+CGDCONT=1,"IP","internet2.voicestream.com";
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Mon Aug 25 16:34:35 2008
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 655
--> Using interface ppp0
--> pppd: x&#65533;[06][08]&#65533;&#65533;[06][08]@&#65533;[06][08]
--> pppd: x&#65533;[06][08]&#65533;&#65533;[06][08]@&#65533;[06][08]
--> pppd: x&#65533;[06][08]&#65533;&#65533;[06][08]@&#65533;[06][08]
--> pppd: x&#65533;[06][08]&#65533;&#65533;[06][08]@&#65533;[06][08]
--> pppd: x&#65533;[06][08]&#65533;&#65533;[06][08]@&#65533;[06][08]
--> pppd: x&#65533;[06][08]&#65533;&#65533;[06][08]@&#65533;[06][08]
--> Disconnecting at Mon Aug 25 16:34:43 2008
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet2.voicestream.com";
AT+CGDCONT=1,"IP","internet2.voicestream.com";
OK
--> Modem initialized.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet2.voicestream.com";
AT+CGDCONT=1,"IP","internet2.voicestream.com";
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Mon Aug 25 16:34:51 2008
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 658
--> Using interface ppp0
--> pppd: x&#65533;[06][08]&#65533;&#65533;[06][08]@&#65533;[06][08]
--> pppd: x&#65533;[06][08]&#65533;&#65533;[06][08]@&#65533;[06][08]
--> pppd: x&#65533;[06][08]&#65533;&#65533;[06][08]@&#65533;[06][08]
--> pppd: x&#65533;[06][08]&#65533;&#65533;[06][08]@&#65533;[06][08]
--> pppd: x&#65533;[06][08]&#65533;&#65533;[06][08]@&#65533;[06][08]
--> pppd: x&#65533;[06][08]&#65533;&#65533;[06][08]@&#65533;[06][08]
--> Disconnecting at Mon Aug 25 16:34:58 2008
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 10 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

```

...and over and over...

I'm not sure how to go about fixing this.  It seems like we're very close to getting it to work.  What can I try?

---

### Post by spiderbatdad on 2008-08-25
Are you running wvdial as root?```
sudo wvdial
```

---

### Post by t0p on 2008-08-25
Just a thought: have you tried the phone in data mode?

---

### Post by diablo75 on 2008-08-26
> **spiderbatdad said:**
> Are you running wvdial as root?```
sudo wvdial
```
Haven't tried it...  Running wvdialconf in sudo matters (because it needs to modify the conf file), but I've never had to run wvdial itself in sudo to get it to work on my own phone.  I'll try it, but doubt it will make all the difference.

> **t0p said:**
> Just a thought: have you tried the phone in data mode?

Data Mode is for accessing the memory card.  Putting it into that mode causes the USB port to behave as if it is an external storage device, and not a modem.

---

