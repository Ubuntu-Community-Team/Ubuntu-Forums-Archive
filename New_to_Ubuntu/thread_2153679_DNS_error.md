---
title: "DNS error"
date: 2013-06-11
forum: New to Ubuntu
---

### Post by Randika srimal on 2013-06-11
i am new to Ubuntu.I use ubuntu 12.04.my network manager detected my 3g dongle well,but then it doesn't detect my huawei E303 dongle and i cant connect with internet ,then i installed wvdial and it detects my dongle.But when i try to connect to internet chrome shows error 105(dns error) and firefox also,but i can use skype without any problem,

here is my wvdial.conf



[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
Init3 = AT+CGDCONT=1,"IP","mobitel3g"
Auto DNS = 1
Password = { }
Phone = *99***1#
Modem Type = Analog Modem
Stupid Mode = 1
Baud = 9600
;Baud = 9600
Dial Command = ATDT
Modem = /dev/ttyUSB_utps_modem
ISDN = 0
Username = { }
Carrier Check = yes
Check DNS = 1
First DNS = 1
Second DNS = 1

my resolv.conf is empty

here is my networkmanager.conf

[main]
plugins=ifupdown,keyfile
dns=dnsmasq


no-auto-default=38:60:77:06:6B:97,


[ifupdown]
managed=false


i tried lot of things by refering forums,but i couldn,t solve this,if someone can help me ,

---

### Post by zero2xiii on 2013-06-12
Hay,

Strange, but try changing these lines as follow:

```

First DNS = 8.8.8.8
 Second DNS = 8.8.4.4
```

and see if that helps.

If not, then you can try adding a manual DNS entry.

Also try accessing the internet through a IP rather.

Open a browser window and enter this in the address bar:
[http://165.165.38.151](http://165.165.38.151)

This is one of the many IP adresses for google.

Cheers

---

### Post by Randika srimal on 2013-06-12
I added first and second dns as you said,but it doesn't work,but when I entered that ip ,I could go to google,but can't go through any link,i appriciate your reply,thanks so much,but I want much help to fix this,thanks

---

### Post by sandyd on 2013-06-12
try
```

sudo nano /etc/resolv.conf
```
Place the following inside (Level 3 Nameservers)

```

nameserver 209.244.0.3
nameserver 209.244.0.4

```

Press control+x to save.

---

### Post by Randika srimal on 2013-06-12
Thanks,but it doesn't work,These are codes that display on terminal wen i run wvdial

```

--> WvDial: Internet dialer version 1.61
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2
OK
--> Sending: AT+CGDCONT=1,"IP","mobitel3g"
AT+CGDCONT=1,"IP","mobitel3g"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Thu Jun 13 08:24:00 2013
--> Pid of pppd: 5000
--> Using interface ppp0
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> local  IP address 10.224.134.125
--> pppd: &#65533;[7f]
--> remote IP address 10.64.64.64
--> pppd: &#65533;[7f]
--> primary   DNS address 172.19.70.210
--> pppd: &#65533;[7f]
--> secondary DNS address 172.19.70.211
--> pppd: &#65533;[7f]

```

---

### Post by Randika srimal on 2013-06-13
Thanks every one for try to support me.I updated my libraries and network manager through update manager,now everithing is fine

---

