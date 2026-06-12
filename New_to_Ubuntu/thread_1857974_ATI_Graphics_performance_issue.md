---
title: "ATI Graphics performance issue"
date: 2011-10-11
forum: New to Ubuntu
---

### Post by venuraalwis on 2011-10-11
Hi,
I'm new to Ubuntu. I have problem with performance in my grapichs card.It takes bit of a delay when i moved between the opened windows using alt+tab.I can't use the effects like wobbly windows etc.I am using the laptop Pavillion dv6/intel i5 with 8 GB of ram.

Ubuntu version: 10.10
I get the following, when I typed the command :lspci -nn | grep VGA

00:02.0 VGA compatible controller [0300]: Intel Corporation Sandy Bridge Integrated Graphics Controller [8086:0116] (rev 09)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:6740]

Is there any way to improve the graphics performance?
Thanks

---

### Post by ubupirate on 2011-10-11
You might try disabling Compiz effects either from right click desktop -> change desktop background -> visual effects, or via terminal:

```
metacity --replace
```

Also make sure your graphics drivers are up to date.

---

### Post by venuraalwis on 2011-10-12
Thanks for the reply.
I have disabled it (anyway it doesn't allow me to enable throws the error- "Desktop effects could not be enabled").

And I'm using the open source driver (I had problems in starting xwindow after installing the proprietary drivers so i switched back to the open source one).
I have followed the steps as it was stated in the following link:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)



when i checked the Xorg.0.log
I found following:


[    23.567] (II) LoadModule: "vesa"
[    23.567] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    23.567] (II) Module vesa: vendor="X.Org Foundation"
[    23.567] 	compiled for 1.8.99.905, module version = 2.3.0
[    23.567] 	Module class: X.Org Video Driver
[    23.567] 	ABI class: X.Org Video Driver, version 8.0


Any Idea?

Thanks

---

### Post by mastablasta on 2011-10-12
from the lspci report you posted above it is not clear what mode of GPU you are using. However it seems ot me you have two ATI chip and Intel. Since you have a newer Intel CPU i guess the card is also new. There should be new proprietary drivers comming up with the 11.10 release. Perhaps they would serve you better.
 
There is also an option to use newer opensource drivers by installing X-org edgers PPA. Just make sure you read all informtion first before the install:
 
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
 
oh and if the GPU is "newish" then chances are it will have better support with proprietary drivers (perhaps some tweak is needed in your case?) and not so good support with opensource drviers which might explain you issues.

---

### Post by venuraalwis on 2011-10-12
Thanks for the information.I will check the link you mentioned.

---

