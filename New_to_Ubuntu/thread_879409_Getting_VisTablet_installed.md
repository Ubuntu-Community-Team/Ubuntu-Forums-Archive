---
title: "Getting VisTablet installed"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by Sydius on 2008-08-04
My girlfriend has a "VisTablet" tablet that works in Ubuntu, but the pressure sensitivity in GIMP doesn't work.  It's not listed as a device under the input device options, so I thought maybe it wasn't installed properly--there was no information in the xorg.conf file about it.

I tried to follow the instructions in the tablet setup help wiki, and the device calls itself simply "Slim Tablet" so I Google'd which driver to put in the xorg.conf file, but all I found was Aiptek "Slim Tablet"s... but they look exactly the same, just a different logo and case color.  So I went ahead and followed the instructions here:

[https://help.ubuntu.com/community/AiptekTablet](https://help.ubuntu.com/community/AiptekTablet)

But it still doesn't show up under devices in the GIMP preferences for input device (where the pressure sensitivity setting is).

Any advice?

---

### Post by Aquiva on 2009-02-01
*BUMP*

I have a VisTablet too, in fact I just got it a few months ago, and now I am running Ubuntu ... and I really want to have a tablet since I am a graphic artist.

I tried installing the VisTablet Pen Pad Driver with Wine, but no luck, I get an "Internal Application Error".

How on earth can I get my tablet working?
Cause it would really suck if I had to buy a $700 equivalent Wacom.

 ~ Mark

---

### Post by mtrausch on 2010-01-26
Have y'all configured GIMP's input settings to "enable" the tablet?  I have found that GIMP has to be told that there is a tablet in the system before it will recognize things such as pressure sensitivity and the like.

---

### Post by mx32 on 2010-10-17
> **Aquiva said:**
> *BUMP*

I have a VisTablet too, in fact I just got it a few months ago, and now I am running Ubuntu ... and I really want to have a tablet since I am a graphic artist.

I tried installing the VisTablet Pen Pad Driver with Wine, but no luck, I get an "Internal Application Error".

How on earth can I get my tablet working?
Cause it would really suck if I had to buy a $700 equivalent Wacom.

 ~ Mark

Try this:
[http://www.stochasticgeometry.ie/2009/10/06/vistablet-under-debian-squeeze/](http://www.stochasticgeometry.ie/2009/10/06/vistablet-under-debian-squeeze/)

---

