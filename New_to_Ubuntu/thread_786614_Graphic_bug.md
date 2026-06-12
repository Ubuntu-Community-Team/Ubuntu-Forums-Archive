---
title: "Graphic bug"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by mat087 on 2008-05-08
Hi,

I've attached to this message a screen shot of the bug. This bug occurs when I'm scrolling down (or up) the page. It occurs in Firefox, in Help and even in gnome-terminal. And the bugs only occurs when the window is maximized, or almost maximized (width).

Ubuntu 8.04 : main, universe, restricted, multiverse, hard-security, hardy-updates, hardy-backports 
[latest updates]

Any ideas?

Thanks,
Mathieu

---

### Post by mat087 on 2008-05-08
I've removed some packages that I wasn't aware that they were installed:

```
[REMOVE, NOT USED] libx11-xcb1
[REMOVE, DEPENDENCIES] compiz-fusion-plugins-extra
[REMOVE, DEPENDENCIES] compiz-fusion-plugins-main
[REMOVE] compiz-core
[REMOVE] compiz-gnome
[REMOVE] compiz-plugins
[REMOVE] compizconfig-backend-gconf
[REMOVE] libcompizconfig0
```

then rebooting my computer makes the bug disappears.

Let's see if this was the problem...


Mathieu

---

### Post by warbread on 2008-05-08
By chance, are you using a DVI connector to connect to your monitor?

---

### Post by mister_pink on 2008-05-08
I hate to say it but I'm afraid the connection to the monitor is unlikely to make any difference to a screenshot :P 

I imagine it's some compiz funkyness, I've had to give up on compiz because it just causes far too many graphical glitches.

---

### Post by skymera on 2008-05-08
Just s stab in the dark here.

Is the connector loose?
Or is it dusty? Give it a good blow.

---

### Post by warbread on 2008-05-08
> **mister_pink said:**
> I hate to say it but I'm afraid the connection to the monitor is unlikely to make any difference to a screenshot :P 


Ah, but it's not just a different connector.  Visual data is sent to the monitor as digital information instead of analog voltage fluctuations, as it is with VGA.  A different signal means a different process for encoding/decoding said visual information.  A different process also mean another variable, which needs to be considered.

Also, I've had similar problems since I switched to a DVI signal.

---

### Post by mat087 on 2008-05-08
> **warbread said:**
> By chance, are you using a DVI connector to connect to your monitor?

No, I'm using my laptop's monitor.

---

### Post by mister_pink on 2008-05-08
Try turning off visual effects and see if it still occurs, I imagine that will fix it. Of course, thats not really a fix as such...

As for DVI, it isnt just the shape of the plug, but I think the screenshot is extracted long before the point where data is being sent to the monitor, which is why for example you sometimes get a black box if you try and screenshot a dvd.

---

