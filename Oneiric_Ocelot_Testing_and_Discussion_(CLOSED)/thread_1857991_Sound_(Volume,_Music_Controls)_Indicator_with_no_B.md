---
title: "Sound (Volume, Music Controls) Indicator with no Banshee"
date: 2011-10-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by effenberg0x0 on 2011-10-11
Hey,

Is there a way / workaround to have the Sound Indicator when we uninstall Banshee? If not, I believe that should be considered a bug. Having the desktop offer a possibility to easily control the system volume (not only music media, sounds in general) can't be associated to having / not having an specific media player installed.

To reproduce: Uninstall banshee, it will uninstall the indicator. Reboot.

Regards,
Effenberg

---

### Post by effenberg0x0 on 2011-10-11
Fixed. Removing Banshee removed indicator-sound, but reinstalling indicator-sound does not reinstall Banshee.

Regards,
Effenberg

---

### Post by mc4man on 2011-10-11
That's fairly odd - have removed banshee on several occasions & never saw the indicator-sound  removed
There is no dep, recommend or suggest for indicator sound in banshee or banshee-extension-soundmenu

---

### Post by ventrical on 2011-10-11
I also noticed that by default, Banshee has it's audio out set for High Definition Audio (especially if you have a nvidia of my type GF210.

Weird.

I had to manually set to analog speakers to get to pc board chip to squeak out sound.

---

### Post by effenberg0x0 on 2011-10-11
@ventrical I have no idea, both cases. Banshee has been a mess for me since day one. Crashes, locking one CPU to 100% randomly, etc. I'm more used to Clementine. Keeping both in the the system always gave preference to Banshee on media autostart, keyboard shortcurts (XF86Play, etc). Every time I removed Banshee it removed indicator-sound. 

Then I had gave up on this for a couple months and today I managed to  keep indicator-sound, integrate it normally with Clementine, move all  keyboard shortcuts/media-keys to work with it, etc. I had already tried a  couple times some months ago and I'm poretty sure it was not possible  (at least in my setup).

I also have two audio devices: Nvidia GF210 (hdmi output) and Realtek ALC892 (8 jacks plus hdmi).....and the second is currently not fully supported by Alsa.  I've been fighting with it for months.

Regards,
Effenberg

---

