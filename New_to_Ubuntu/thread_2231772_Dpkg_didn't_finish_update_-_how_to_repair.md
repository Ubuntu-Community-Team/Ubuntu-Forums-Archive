---
title: "Dpkg didn't finish update - how to repair?"
date: 2014-06-27
forum: New to Ubuntu
---

### Post by JeQhdMD on 2014-06-27
Hello,

Just finished 2nd install of Linux Lite (based on "buntu 14.04 LTS.   Tried to install broadcom wireless drivrs on a HPtx1000us laptop, but wasn't aware the normal install process now downloads and installs those drivers (if both checkboxes checked at install).

So, the install locked up and upon trying to install another package via synaptic, I get an error popup stating something like "dpkg interupted - repair by manual input of "dpkg configure -a" . . . or something close to that.   Perhaps I'm not typing that into the terminal correctly, as I get a response re the various options to use n running dpkg (which I'm unclear on).

Any help or tips how to do a repair or reset of the package mgmt system is appreciated.

---

### Post by grahammechanical on 2014-06-27
I am sure the correct command is

```
dpkg --configure -a
```

it will configure all partially installed packages. Anyway, that is what we use on Ubuntu. I do not know about Linux Lite.

Regards.

---

### Post by Vladlenin5000 on 2014-06-27
Linux Lite is just another Ubuntu derivative: [https://www.linuxliteos.com/linuxlite.html](https://www.linuxliteos.com/linuxlite.html)
As such, just do ```
sudo dpkg --configure -a
```

---

### Post by JeQhdMD on 2014-06-28
Thank you both!  The command along with sudo worked perfect.  Just had to get the spacing right.

Greg

---

