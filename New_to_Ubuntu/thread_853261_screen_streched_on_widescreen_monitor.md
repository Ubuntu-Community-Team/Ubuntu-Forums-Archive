---
title: "screen streched on widescreen monitor"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by saratchandra on 2008-07-08
Just installed ubuntu on my friends computer with a samsung 17" widescreen monitor and the screen seems to be stretched a lot. I've changed the monitor settings correctly, but its still stretched. Screen resolution is 1280x720. Thats the optimum resolution for that monitor.

---

### Post by sydbat on 2008-07-08
Looks right to me. Nice actually.

---

### Post by saratchandra on 2008-07-08
He says the icons and right click are stretched. I'm not sure either. I've never used a widescreen monitor before.

---

### Post by oldsoundguy on 2008-07-08
You need to go into the System and re-set the monitor and check the video display properties (may require an unsupported driver)(you need to have the card specifications and type).  That resolution is for a standard aspect ratio monitor.  The resolution should be (at a minimum) 1280 x 1024
My HP cinema is 1600 x 1024. That was achieved by installing the NVida card using Envy (a third party install program) and then MANUALLY selecting and installing the monitor.

---

### Post by saratchandra on 2008-07-08
> **oldsoundguy said:**
> You need to go into the System and re-set the monitor and check the video display properties (may require an unsupported driver)(you need to have the card specifications and type).  That resolution is for a standard aspect ratio monitor.  The resolution should be (at a minimum) 1280 x 1024
My HP cinema is 1600 x 1024. That was achieved by installing the NVida card using Envy (a third party install program) and then MANUALLY selecting and installing the monitor.

I already installed nvidia drivers. The manual for the monitor says 1280 x 720 is the maximum possible resolution.

---

### Post by saratchandra on 2008-07-08
Should I install the driver from envy or enable restricted driver?

---

### Post by sydbat on 2008-07-08
If it is a limitation of the monitor itself, I don't think there is an option that won't break the monitor (which would be bad and cost $$$).

---

### Post by oldsoundguy on 2008-07-08
first, you need to learn about aspect ratio:
[http://compreviews.about.com/od/multimedia/a/LCDSpecs.htm](http://compreviews.about.com/od/multimedia/a/LCDSpecs.htm)

1280x720 is not a resolution for a wide aspect ratio monitor.  

Get the MANUAL (Google is your friend) and do not rely on what "system" tells you are the figures.  As noted, you may have to MANUALLY install the monitor as right now you are using an SVGA setting for standard aspect ratio LCD monitors.

---

### Post by saratchandra on 2008-07-08
> **oldsoundguy said:**
> first, you need to learn about aspect ratio:
[http://compreviews.about.com/od/multimedia/a/LCDSpecs.htm](http://compreviews.about.com/od/multimedia/a/LCDSpecs.htm)

1280x720 is not a resolution for a wide aspect ratio monitor.  

Get the MANUAL (Google is your friend) and do not rely on what "system" tells you are the figures.  As noted, you may have to MANUALLY install the monitor as right now you are using an SVGA setting for standard aspect ratio LCD monitors.

Actually, I just read the manual of the monitor in the installation CD and it says 1280 x 720 is the maximum possible. I can change it to 1280 x 800, but the desktop is bigger than the screen.

---

### Post by overdrank on 2008-07-08
> **saratchandra said:**
> Actually, I just read the manual of the monitor in the installation CD and it says 1280 x 720 is the maximum possible. I can change it to 1280 x 800, but the desktop is bigger than the screen.

Hi and have you install the nvidia settings from synaptic manager? Then you can use the command ```
gksu nvidia-settings 
``` and make some adjustments there.

---

### Post by saratchandra on 2008-07-08
> **overdrank said:**
> Hi and have you install the nvidia settings from synaptic manager? Then you can use the command ```
gksu nvidia-settings 
``` and make some adjustments there.

Yes, I installed nvidia-settings, but it says the monitor is a crt monitor while it is an lcd in reality.

---

### Post by overdrank on 2008-07-08
> **saratchandra said:**
> Yes, I installed nvidia-settings, but it says the monitor is a crt monitor while it is an lcd in reality.

Well now that you mention it mine is shown as a CRT and it is a 19 LCD. :)

---

### Post by saratchandra on 2008-07-12
Sorry for the late reply, but I think he's just trying to find something wrong with this wonderful OS. I convinced him by installing the clock screenlet and showing that it is a perfect circle and not an ellipse. He loves ubuntu now. On a side note, I'm thinking about buying a widescreen monitor too, its really cool.

---

