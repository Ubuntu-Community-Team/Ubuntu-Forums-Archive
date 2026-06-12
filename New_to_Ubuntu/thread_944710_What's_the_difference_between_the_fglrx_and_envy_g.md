---
title: "What's the difference between the fglrx and envy graphics drivers?"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by WastePotato on 2008-10-11
Hello all,

Just a question: What's the difference between the fglrx and envy ATI graphics drivers?

It appears that both seem to support my card.

BTW: I cant get Compiz to fully work. I can get it as a WM, but I am unable to get effects such as Cube windows to work. 

Any ideas on this? :confused:


Thanks.

---

### Post by bobnutfield on 2008-10-11
fglrx is the proprietory driver from ATI.  Envy is just an application that, when run, reads the hardware you have and dowloads/installs the correct driver.  You probably do no have the correct driver installed which is why compiz is acting this way.

---

### Post by WastePotato on 2008-10-11
Ah. MKay.

Does anyone know what the correct driver is for my card to get 3D acceleration (For the cube)?

---

### Post by bobnutfield on 2008-10-11
If you have one of the newer ATI cards, then Envy will install the correct driver for you, and it will automatically reconfigure your xorg.conf file.  If you don't have envy installed, just install it with apt-get, it will then be in the System section of Applications.  Run the app, and it will install the driver for you.

---

### Post by markbuntu on 2008-10-11
Envy has a lot of problems with the ati drivers, it is using an old driver, 8.6 which is useless or misinstalls for many ati cards. I would reccomend against using it. Your best options would be to enable the restricted driver if one is available or if not, use this guide and follow method 2 to get the latest 8.9 driver from ati:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)


If you are using Intrepid, do not use the proprietary fglrx driver. it is not yet compatible with Xorg7.4. If you do wish to use fglrx, Xorg must be downgraded to 7.3 before installing the driver. ATI is aware of this problem and is working to fix it hopefully before Intrepid is released.

---

