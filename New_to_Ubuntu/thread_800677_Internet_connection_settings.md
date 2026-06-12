---
title: "Internet connection settings"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by andisandis on 2008-05-20
Hi there everybody, as a newbie I would appreciate seniors help to configure my internet connection via a sonyericsson mobile phone as a modem. I managed to connect it and all seem to work but unfortunately when I run firefox and insert a whatever address firefox cannot connect as if there weren't any connection available.
Below you can see the connection log as diplayed on a terminal window.
****************************************
andi@andi-desktop:~$ wvdial
--> 
WvDial: Internet dialer version 1.60
--> 
Cannot get information for serial port.
--> 
Initializing modem.
--> 
Sending: ATZ
ATZ
OK
--> 
Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> 
Sending: AT+cgdcont=9,"IP","internet.wind"
AT+cgdcont=9,"IP","internet.wind"
OK
--> 
Modem initialized.
--> Sending: ATDT*99***9#
--> 
Waiting for carrier.
ATDT*99***9#
CONNECT
~[7f]}#@!}!}!} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&}8I}"qd|~
--> 
Carrier detected.  Waiting for prompt.
~[7f]}#@!}!}"} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&}8I}"q(}1~
--> 
PPP negotiation detected.
--> 
Starting pppd at Mon May 19 23:21:02 2008
--> 
Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> 
PAP (Password Authentication Protocol) may be flaky.
--> 
Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP 
(Challenge Handshake) may be flaky.
--> Pid of pppd: 6565
--> Using interface ppp0
--> 
pppd: &#65533;&#65533;[06][08]H&#65533;[06][08]&#65533;&#65533;[06][08]
--> 
pppd: &#65533;&#65533;[06][08]H&#65533;[06][08]&#65533;&#65533;[06][08]
--> 
pppd: &#65533;&#65533;[06][08]H&#65533;[06][08]&#65533;&#65533;[06][08]
--> 
pppd: &#65533;&#65533;[06][08]H&#65533;[06][08]&#65533;&#65533;[06][08]
--> 
pppd: &#65533;&#65533;[06][08]H&#65533;[06][08]&#65533;&#65533;[06][08]
--> 
pppd: &#65533;&#65533;[06][08]H&#65533;[06][08]&#65533;&#65533;[06][08]
--> 
local  IP address 151.82.14.128
--> 
pppd: &#65533;&#65533;[06][08]H&#65533;[06][08]&#65533;&#65533;[06][08]
--> 
remote IP address 10.64.64.64
--> 
pppd: &#65533;&#65533;[06][08]H&#65533;[06][08]&#65533;&#65533;[06][08]
--> 
primary   DNS address 193.70.152.25
--> 
pppd: &#65533;&#65533;[06][08]H&#65533;[06][08]&#65533;&#65533;[06][08]
--> 
secondary DNS address 193.70.192.25
--> 
pppd: &#65533;&#65533;[06][08]H&#65533;[06][08]&#65533;&#65533;[06][08]





********************************************
What I'm I missing, are there any restrictions on my account (I'm the only user), or something I have to change on settings.
Thanks a lot

---

### Post by rraj.be on 2008-05-20
Just ppost me  your contents in  /etc/wvdial.conf

it shud be  just like this........

somee variations or some wrong parameters may lead to this


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

---

### Post by rraj.be on 2008-05-20
Just ppost me  your contents in  /etc/wvdial.conf

it shud be  just like this........

somee variations or some wrong parameters may lead to this


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


just try to reconfigure it.........


IM too using sony ericsson mobile for my GPRS connetion and my log is like

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

---

### Post by AstralliS on 2008-05-20
Look what I got. I'm using Nokia 6600 as modem, and Bluetooth USB DONGLE GIGABYTE: GN-BTD02. I tried to connect through GNOME PPP, but only I get is:

```
/home/astrallis/.wvdial.conf<Warn>: Ignoring malformed input line: ";Do NOT edit this file by hand!"
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
WvDial<*1>: Sending: ATM1L3DT*99***1#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATM1L3DT*99***1#
WvDial Modem<*1>: CONNECT
WvDial Modem<*1>: ~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
WvDial<*1>: Carrier detected.  Waiting for prompt.
WvDial Modem<*1>: ~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
WvDial<*1>: PPP negotiation detected.
WvDial<Notice>: Starting pppd at Tue May 20 17:55:30 2008
WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
WvDial<Err>: --> PAP (Password Authentication Protocol) may be flaky.
WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
WvDial<Err>: --> CHAP (Challenge Handshake) may be flaky.
WvDial<Notice>: Pid of pppd: 9410
WvDial<*1>: Using interface ppp0
WvDial<*1>: Disconnecting at Tue May 20 17:55:37 2008
WvDial<*1>: The PPP daemon has died: A modem hung up the phone (exit code = 16)
WvDial<*1>: man pppd explains pppd error codes in more detail.
WvDial<Notice>: Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
```

---

### Post by rraj.be on 2008-05-20
I think your phone is not connected with your computer in phone mode or

It may be busy with a call or it may be in file transfer mode or some other......

just try after restarting your phone anddd your commputer.......

it may solve the problem

---

### Post by andisandis on 2008-05-21
It's ok guys, thank you all, it was just a stupid thing I missed: Firefox offline option was checked so I was trying to surf offline ;-)
Thanks a lot again

---

