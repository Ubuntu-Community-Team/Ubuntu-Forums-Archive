---
title: "configuring vgetty"
date: 2013-10-10
forum: New to Ubuntu
---

### Post by farrinux on 2013-10-10
Hi guys.

I am a little bit confused on configuring vgetty.  The manual states the following.....

"vgetty  is  not meant to be run from the command line. It should be run
       from the /etc/inittab file so it can respawn after each call. Here is a
       typical inittab entry:

       S0:345:respawn:/usr/sbin/vgetty ttyS0"

Well after checking the file system there is no /etc/inittab file anymore because of upstart.  I did some more research per this [http://askubuntu.com/questions/34308/where-is-inittab-file](http://askubuntu.com/questions/34308/where-is-inittab-file) .
I took the advice and researched init(5) at [https://help.ubuntu.com/community/UpstartHowto](https://help.ubuntu.com/community/UpstartHowto) At the bottom they talk about gettys and say the following ......

"In /etc/init there is a file named ttyN.conf for each getty that will be started, where N is numbered 1 to 6. Remove any that you do not want."

Sure enough there is, but is this where I would put the above vgetty statement? Do I add it to all six of the ttyN.conf files?  If this is not where I should add the statement then which file would I add it too?

Lastly my modem is a usb modem and wvdial.conf says this.....

```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
; Phone = <Target Phone Number>
; Password = <Your Password>
; Username = <Your Login Name>
```

I would assume I would change this statement ```
S0:345:respawn:/usr/sbin/vgetty ttyS
``` to ```
S0:345:respawn:/usr/sbin/vgetty ttyACM0
```

Any way thanks for any insight or help you can give.

---

### Post by luilver on 2014-08-11
# cat > /etc/init/vgetty.conf

description     "vgetty daemon"

start on runlevel [2345]
stop on runlevel [!2345]

respawn
exec /usr/sbin/vgetty -s 115200 ttyACM0


--
It should works fine. I tested it in ubuntu 13.10
Regards

---

