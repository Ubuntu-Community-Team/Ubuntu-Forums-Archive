---
title: "Error while connecting to Internet through my Mobile. Help!!!"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by daringdeer on 2008-04-30
I have followed all the steps at [http://ubuntuforums.org/showthread.php?t=378968&](http://ubuntuforums.org/showthread.php?t=378968&) .

But, when I try to start the terminal and connect using WVDIAL command, It gives the following result. It keeps of repeating until we end it with the CONTROL+C . 

> [root@localhost ~]# wvdial
--> WvDial: Internet dialer version 1.54.0
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed Apr 30 13:18:03 2008
--> pid of pppd: 4743
--> Using interface ppp1
--> pppd: Modem
--> pppd: Modem
--> pppd: Modem
--> pppd: Modem
--> pppd: Modem
--> pppd: Modem
--> Disconnecting at Wed Apr 30 13:18:10 2008
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
--> Modem initialized.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed Apr 30 13:18:21 2008
--> pid of pppd: 4767
--> Using interface ppp1
--> pppd: Modem
--> pppd: Modem
--> pppd: Modem
--> pppd: Modem
--> pppd: Modem
--> pppd: Modem
--> Disconnecting at Wed Apr 30 13:18:27 2008
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
OK
--> Modem initialized.
Caught signal #2!  Attempting to exit gracefully...
--> Disconnecting at Wed Apr 30 13:18:30 2008
[root@localhost ~]# 




Help me!!! Please!!!

---

### Post by daringdeer on 2008-04-30
?? Help me... Please...

---

