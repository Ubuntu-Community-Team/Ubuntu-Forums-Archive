---
title: "Printer driver issues"
date: 2011-11-22
forum: New to Ubuntu
---

### Post by PreacherGein on 2011-11-22
So I just had my friend install Ubuntu 10.10 Maverick on my hp-mini do to the minimal size of the harddrive.  He had the printer driver installed and it worked for a couple days but now it says it cannot connect to that printer anymore I attempted to download a driver from hp in terminal, it wouldn't run so i dunno what to do at this point.  Please help me so I I'm not forced to go back to windows as I primarily use this netbook for work.

---

### Post by neofreud on 2011-11-23
I had a lot of issues with my HP LaserJet P1006 here is[ what I did]("http://livefreelinux.blogspot.com/2011/11/hp-laserjet-p1006-troubleshooting.html"). 

Let me know if it works for you. Good luck!

---

### Post by BC59 on 2011-11-23
Make sure that the HP packages are installed:

```
sudo apt-get install hplip hplip-gui
```

Then you can check here for drivers:

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

---

