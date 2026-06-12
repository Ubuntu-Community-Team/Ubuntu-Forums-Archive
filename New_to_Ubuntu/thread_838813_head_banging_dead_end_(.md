---
title: "head banging dead end :("
date: 2008-06-23
forum: New to Ubuntu
---

### Post by bluemarble on 2008-06-23
Hi all,

I recently got a USB modem (Option from Virgin) and downloaded the Vodafone driver which work a treat. I have since got a newer model which is a Huawei e220. Unfortunately it does not work with the Vodafone driver. I have tried many things from many threads and still have no internet.

I think I am close but along the way I may have stuffed something up.

When using GnomePPP it almost connects, trys sending the password (which does not exist) but goes no further. With Vodafone driver, it tells me there is no network available which is not true.

I have no more ideas, I think the solutions will be simple but just a little beyond my knowledge :(

Help please, I have no internet so I have to use windows :(

---

### Post by rraj.be on 2008-06-23
Try this.

Open terminal.

```
Application's --> Acessories -->Terminal
```

connect your mobile with computer via USB.

type 

```
sudo wvdialconf
```

it will search for odem and store its configuration in /etc/wvdial.conf.

Then type ```
sudo gedit /etc/wvdial.conf
```.

This will open the configuration file .

It should look like

```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
; Phone = <Target Phone number>
; Password = <Password>
; Username = <<your user name
```

you should edit your file as below.


```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = *99***1#
Password = kumar
Username = raj
```

The importatnt thing is you should remove the semicolan at the beginimg of phone number pasword and user name.

---

### Post by bluemarble on 2008-06-23
My output is below, it does look a bit different to yours. So i should just edit the Dialer and not hsdpa?


[Dialer Defaults] 
Init1 = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
Stupid Mode = 1 
Modem Type = Analog Modem 
ISDN = 0 
Phone = *99***1# 
Modem = /dev/ttyUSB0 
Username = username 
Dial Command = ATDT 
Password = password 
Baud = 9600 
 
[Dialer hsdpa] 
Init2 = ATZ 
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
ISDN = 0 
Modem = /dev/ttyUSB0 
Modem Type = Analog Modem 
Baud = 460800

---

### Post by bluemarble on 2008-06-23
I made the changes but now the system cannot open the modem at all...

---

