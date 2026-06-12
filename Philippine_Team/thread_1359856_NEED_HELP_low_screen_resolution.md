---
title: "NEED HELP: low screen resolution"
date: 2009-12-20
forum: Philippine Team
---

### Post by ncvaldez on 2009-12-20
[SIZE=3]i just installed an ubuntu 9.10 to my laptop
SiS 671/771 and 1280x800
but the maximum screen resolution available is only up to 800x600
anyone who knows what to do?
i searched this problem and some of the solution is to rewrite the xorg.conf. i tired this but unfortunately the screen resolution did not change
i dont know if im doing something wrong
i really need help cause im new to ubuntu[/SIZE]

---

### Post by Script Warlock on 2009-12-20
na-solve ka na rin to na issue dati sa neo laptop na sis din ang chipset... hintayin lang natin ibang inputs:(

---

### Post by loell on 2009-12-20
try this driver

[http://nacho.larrateguy.com.ar/wp-content/uploads/2009/07/xorg-driver-sisimedia_0.9-1_i386.deb]("http://nacho.larrateguy.com.ar/wp-content/uploads/2009/07/xorg-driver-sisimedia_0.9-1_i386.deb")


you might also need to modify your XOrg,

```
sudo gedit /etc/X11/xorg.conf 
```

edit it and replace the proper  sections with

```

Section "Device"
    Driver "sismedia"
EndSection


```

then restart..




original link  from [http://nacho.larrateguy.com.ar/2009/07/11/drivers-de-sis-771671-para-xorg-1-6-mandriva-2009-1-ubuntu-jaunty-9-04/]("http://nacho.larrateguy.com.ar/2009/07/11/drivers-de-sis-771671-para-xorg-1-6-mandriva-2009-1-ubuntu-jaunty-9-04/")

---

### Post by ncvaldez on 2009-12-20
[SIZE=2]thanks Script Warlock and loell!!! :))

the link loell gave me actually worked! 
grabe after a day of googgling the bug, na-solve na rin! thanks a lot!!!
i love it!
sana maintindihan ko na ng todo ang linux after this cause I bet there will be more bugs to come!

THANKSSSSSSSSSSSSSSS A LOOOOOOOOOOOOT uli :))[/SIZE]

---

### Post by blackberet007 on 2010-08-13
omg finally i found an answer! i tried everything: xrandr, xorg, lahat! eto lang pala ang sagot... thanks again!

---

