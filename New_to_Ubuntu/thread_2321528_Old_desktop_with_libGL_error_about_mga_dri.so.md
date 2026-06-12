---
title: "Old desktop with libGL error about mga_dri.so"
date: 2016-04-22
forum: New to Ubuntu
---

### Post by tony118 on 2016-04-22
I've install Lubuntu on an old desktop but getting this "laggy" behaviour and CPU usage at 100% when I move a window around on the desktop. The machine has a Matrox Millennium G450 32Mb SDRAM Dual Head graphics card and I see an error from


```

$ glxinfo
libGL error: unable to load driver: mga_dri.so
libGL error: unable to load driver: mga
```

So looking through /var/log/Xorg.0.log I see a few strange things:


```

(EE) open /dev/dri/card0: No such file or directory
(II) MGA(0): Direct rendering enabled
(EE) AIGLX: reverting to software rendering
```

...and a few lines about default values (==) being used as there isn't an xorg.conf file specifying all the different Sections: Layout, Screen, Monitor, Device. Which is perfectly correct as there is no xorg.conf.


So Direct rendering enabled and then reverted, and the laggy 100% CPU behaviour. All seems to make sense BUT how do I go about fixing things? Any help would be most welcome.


Thanks.

---

### Post by DuckHook on 2016-04-22
Welcome to the forums, tony118.

A Matrox Millennium G450. Now, *that* is old. It is no surprise that a 32 MB graphics card is labouring doing much anything. But 100% CPU and your error messages mean that all of your rendering is being done in software. The fact that the driver won't load is the cause. We could try getting it to work, but I'm telling you now that you won't be happy even if we succeeded. That card is positively ancient. Might a newer card purchased through eBay or Kijiji be a better answer? You could even get a decent upgrade scrounging through e-waste cemeteries, probably at no cost.

---

