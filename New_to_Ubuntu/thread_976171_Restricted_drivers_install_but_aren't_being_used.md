---
title: "Restricted drivers install but aren't being used"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by cisforcojo on 2008-11-09
I know the ATI restricted drivers aren't supported but I believe this problem lies outside of the drivers. I have installed the drivers using System->Admin->Hardware Drivers and it says that they are now being used but glxinfo reports otherwise:

server glx vendor string: SGI
server glx version string: 1.2

client glx vendor string: SGI
client glx version string: 1.4

Direct rendering is supported and Compiz works fine, my issue is that some games require the ATI restricted drivers.

Any ideas???

---

### Post by Peter09 on 2008-11-09
Start by checking what drivers are actually running.

Can you post the output of

```
lshw -C display
```

---

### Post by cisforcojo on 2008-11-16
Sorry for the late reply. Been really bogged down at work and too tired to deal with it when I come home.

> 
 ~$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: M24 1P [Radeon Mobility X600]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=fglrx_pci latency=0 module=fglrx


---

### Post by cisforcojo on 2009-01-01
(Very late) bump!

---

### Post by cisforcojo on 2009-01-01
OK, I have modified gstreamer-properties so that my Video is "X Window System (No Xv)" and videos seem to display alright (maybe a TINY bit choppy) fullscreen with VLC if I change the video output to "X11 video output". 

Totem is still hopeless however fullscreen (windowed it's fine). Anyone else experiencing this? I'm currently looking into if I can change Totem to use X11 video ouput.

---

### Post by Delever on 2009-01-01
Yes, I experienced that with no hope to fix up until i moved to nVidia... :(

Shortly, don't use Compiz.

---

