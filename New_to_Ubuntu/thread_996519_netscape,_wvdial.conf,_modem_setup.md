---
title: "netscape, wvdial.conf, modem setup"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by tnothwehr on 2008-11-28
I got enough information from this forum to get Ubuntu working with an external modem dialing to Netscape that I thought I would share.

My wvdial.conf settings:
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 S11=55 +FCLASS=0
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Modem = /dev/ttyS0
Phone = 7635747230
Username = [email]username@netscape.com[/email]
Password = password
Auto DNS =1

Type 'wvdial' at a terminal prompt and it should work if you have the right external modem.  I suffered trying to get a US Robotics USR5686D modem working until I updated the firmware.  It can be found at;

[http://www.usr.com/support/product-template.asp?prod=5686d](http://www.usr.com/support/product-template.asp?prod=5686d)

I also tried a Bocamodem 33,6000bps and it worked just by plugging it in.

Oh yes, I had to open up permissions on /etc/ppp/chap-secrets.

I hope this saves someone the time I spent figuring this out!

---

