---
title: "Enltv Tuner Card"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by Mr Pockets151 on 2008-06-07
So I followed this thread
 [http://ubuntuforums.org/showthread.php?t=315379]("http://ubuntuforums.org/showthread.php?t=315379")
and  also this page which is in spanish(I speak fluent)[http://linux-yyo.blogspot.com/2007/08/instalar-encore-tv-fm-tuner-pro-enltv.html]("http://linux-yyo.blogspot.com/2007/08/instalar-encore-tv-fm-tuner-pro-enltv.html").  Then I went to "synaptic package manger" and installed "tv time" but it doesn't work.  

I run tv time and all I see is a box that appears for 1/2 milli second and nothing. 

I want to watch tv with my tv tuner like I did in XP.

---

### Post by quelx on 2008-06-07
Try **xawtv** and try running **tvtime** from a terminal to see the errors, if any and post those here.

**Applications** > **Accessories** > **Terminal**

```
tvtime
``` <enter>

---

### Post by Mr Pockets151 on 2008-06-07
edit

---

### Post by Mr Pockets151 on 2008-06-07
tvtime in term gave me this error ```
xvoutput: No XVIDEO port found which supports YUY2 images.tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: http://gatos.souceforge.net/
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.


```

I tried the http site but I get a page load error.

---

### Post by quelx on 2008-06-07
If you have an ATI card **and** are using the fglrx (restricted driver) edit your */etc/X11/xorg.conf*

and in the **Section "Device"** for the card add *after* **Driver "fglrx"**

from the terminal ```
sudo nano -w /etc/X11/xorg.conf
```

```
Option "VideoOverlay" "on" 
Option "OpenGLOverlay" "off"
``` 

**CTRL-X** to save and exit.

Restart and try **tvtime** again

PS. **xawtv** is a package in Synaptic

---

### Post by Mr Pockets151 on 2008-06-09
This didn't work.  Anyone have any suggestions.  I'm searching up and down to see what ever I can find.

---

