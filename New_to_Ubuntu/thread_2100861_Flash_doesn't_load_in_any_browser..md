---
title: "Flash doesn't load in any browser."
date: 2013-01-03
forum: New to Ubuntu
---

### Post by tlhIngan on 2013-01-03
Hello, I'm a bit of a noob at Linux, but I do want to figure this system out.
I'm running Lubuntu 12.04 and have an issue with Flash: it doesn't load or crashes upon loading, depending on the browser and page.

I first tried getting flash working with Chromium. I've installed the flash-installer from Synaptic, I've also installed the restricted addons numerous times to no avail.
I noticed the package installer was complaining about not finding libgtk2-perl, so I installed that followed by the restricted addons and flash-installer, still no Flash.
I then installed Chrome, since Flash is built-in. After verifying the Flash plugin was indeed active and enabled, the Flash still doesn't load.
I then downloaded Firefox and reinstalled the restricted addons and the flash-installer, still no Flash.

Could it be my graphics card not having the right driver or simply not being supported? I did have to use the alternate Lubuntu installer to avoid freezing after the file copying.

I am running an AMD Athlon XP 2000+ on an ASUS A7V8X-X board with 2GB RAM and an ATI Radeon 7500 (RV200 chip) with 64 MB and a Creative Labs SoundBlaster Audigy SE.

I'll see about updating the graphics card driver and post back.
Is there anything else I should be looking at?

---

### Post by tlhIngan on 2013-01-03
Installed the fglrx driver, still no Flash in Chrome.
Purged it, then installed open source Radeon driver, still no Flash in Chrome.
I have a few spare graphics card laying around, I'll pop one of them in and see if there's any change.

---

### Post by arpanaut on 2013-01-03
The Athlon XP processor does not have SSE2 capability so the newer versions of flash will not work.  See the link in this post it may provide you a solution.
[http://ubuntuforums.org/showpost.php?p=12431410&postcount=9](http://ubuntuforums.org/showpost.php?p=12431410&postcount=9)

I had to use this method to get flash working on two of my older rigs.
HTH

---

### Post by tlhIngan on 2013-01-03
I'll give that a try and post back.

---

### Post by tlhIngan on 2013-01-03
How do I install this?
I've made links to the .so file in the Firefox plugins directory and the chromium-browser plugins directory, but that's obviously not enough.

---

### Post by tlhIngan on 2013-01-03
Fixed it!
Works on all 3 browsers!
Version 11.1.102.63 works.
To install it, [see here]("http://ubuntuforums.org/showthread.php?t=1953796").

---

### Post by tlhIngan on 2013-01-03
Thanks arpanaut for pointing me in the correct direction.
I don't think anybody knows about SSE2 being a requirement for Flash starting with 11.2.
And thanks lovinglinux for flash-aid!
You guys rock!

---

