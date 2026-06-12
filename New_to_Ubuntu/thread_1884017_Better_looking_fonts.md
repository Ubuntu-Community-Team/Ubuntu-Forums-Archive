---
title: "Better looking fonts?"
date: 2011-11-20
forum: New to Ubuntu
---

### Post by sillyboy on 2011-11-20
I bought a new HP monitor (20"), and was looking for a way to get better looking fonts in Ubuntu. The fonts in my old monitor (15") were rough looking too. I have Ubuntu Tweak, and have used Appearance Preferences, but the fonts still look rough, unless there is the right combination in AP to let them look better. Now I'm talking about ALL the fonts used in Ubuntu, as, File-Edit-View-History-Bookmarks-Tools-Help,even the letters in this post,etc.

I am using a resolution of 1280 X 720. My video card(GeForce FX 5500) will not hold a resolution of 1600 X 900 that is native for this HP monitor.

Also if I make the resoloution any higher, everything is hard to see.

Any suggestions??

Thanks

---

### Post by blackbird34 on 2011-11-20
what about trying the ttf-mscorefonts-installer package in Synaptic ? Might get some extras to choose from...
And use subpixel smoothing in appearance.

---

### Post by Vaphell on 2011-11-20
shouldn't you try to fix the issue of wrong resolution in the first place? using lcd monitors in non-native mode is full of fail.
can you force the native resolution in xorg.conf?

---

### Post by sillyboy on 2011-11-20
> **Vaphell said:**
> shouldn't you try to fix the issue of wrong resolution in the first place? using lcd monitors in non-native mode is full of fail.
can you force the native resolution in xorg.conf?

When I set the resolution to 1600x900 (which is to small for me to see) using the video card settings and reboot the computer, the monitor does an auto-config (every time) and removes my settings.

When I go to System>Monitors, I get the message: "It appears that your graphics driver does not support the necessary extensions to support this tool. Do you want to use your graphics driver vendor's tool instead"?

When I click No, I go to Monitor Preferences.  If I click yes, I go to the Nvidia screen with all the x server info.

?????

Thanks

---

### Post by Vaphell on 2011-11-20
but does the 1600x900 actually work when you switch to it? If so then hardcode the resolution directly in xorg.conf file so the system doesn't do the autodetect part only to fail at it (google a bit how to do that)

as for resolution being too hard on the eyes - you can always bump the DPI setting up in font preferences. It acts as a global zoom for all texts. font size 10 in 120dpi is 25% bigger than the same 10 in default 96dpi. The result would be very similar to running in 1280x720, the only difference being the greater level of detail in case of native res.

---

### Post by sillyboy on 2011-11-20
OK Vaphell, I will try

Thank you

---

