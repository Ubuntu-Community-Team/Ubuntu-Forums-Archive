---
title: "Ubuntu 8.04 Runs Slowly with Compiz"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by jeffries101 on 2008-04-24
I've just upgraded to Ubuntu 8.04 from 7.10. I recently installed compiz but everything seems to be running slower than it did on 7.10. I've installed xserver-xgl and i think i have the latest drivers on my ATI X300 graphics card. I'm still very new to this whole operating system and I'm not sure if i'm forgetting anything. Any help would be appreciated, thanks

---

### Post by Thingymebob on 2008-05-11
For an ATI based card I would recommend you follow the guide here:[http://wiki.cchtml.com/index.php/Ubuntu]("http://wiki.cchtml.com/index.php/Ubuntu")

if you still see no improvement open a terminal and type
```
fglrxinfo
```
post the output here, also post the output of
```
cat /etc/X11/xorg.conf
```

---

### Post by Nikunj93 on 2008-05-11
> **Thingymebob said:**
> For an ATI based card I would recommend you follow the guide here:[http://wiki.cchtml.com/index.php/Ubuntu]("http://wiki.cchtml.com/index.php/Ubuntu")

if you still see no improvement open a terminal and type
```
fglrxinfo
```
post the output here, also post the output of
```
cat /etc/X11/xorg.conf
```

what would u suggest for an NVIDIA 8600GT
cause i also feel hardy slow after compiz is on

---

### Post by grannyw on 2008-05-11
How mach RAM do you have???

---

### Post by grannyw on 2008-05-11
How much RAM you use if you check in the "System Monitor"???(just in case its a memory issue)

---

