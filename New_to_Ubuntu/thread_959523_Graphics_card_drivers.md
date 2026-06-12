---
title: "Graphics card drivers"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by mattt4001 on 2008-10-26
Hi, 
   I have had Ubuntu for a few weeks now and I just replaced my existing graphics card with an EVGA 260 GTX. The first time I booted with this new card I got a message saying something along the lines on "Ubuntu is running in low graphics mode." I have tried updating my Nvidia driver but I still get the same message. The max resolution is 800x600. Under hardware drivers it says "No proprietary drivers"

Thanks, mattt4001

---

### Post by SunnyRabbiera on 2008-10-26
Hmm, what version of Ubuntu are you using?

---

### Post by kerboute on 2008-10-26
Problem during installing ubuntu 8.10 beta version, Network card not detected

---

### Post by mattt4001 on 2008-10-26
Hardy

---

### Post by mattt4001 on 2008-10-26
I was running Hard 8.04 but just updated to 8.10. When it started it found a graphics driver under hardware drivers. (driver- NVIDIA accelerated graphics driver version 177) It told me to restart and when it did the low graphics message showed up again. I need help. One thing to note is that under NVIDIA X server settings I get a messages saying- 
```
You do not appear to be using the NVIDIA X driver.
 Please edit your X configuration file (just run `nvidia-xconfig` as root),
 and restart the X server.
```
 I tried 
```
nvidia-xconfig
```
I get
```
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```
The same error still apears when I open NVIDIA X server settings

---

