---
title: "Broken icons in notification area - gnome-fallback session"
date: 2011-06-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lucazade on 2011-06-29
Icons in the notification are broken, also using a different icon set like Faenza.
There are not indicators yet for new panel and probably won't come in time for OO release.

In the screenshot icons are missing for battery, bluetooth and network-manager.

I wasn't able to find a bug-report about it in Launchpad. Hints? Ideas why are broken?

---

### Post by dino99 on 2011-06-29
maybe some patience (not so long i guess)

[http://ubuntuforums.org/showpost.php?p=10993685&postcount=11](http://ubuntuforums.org/showpost.php?p=10993685&postcount=11)

---

### Post by lucazade on 2011-06-29
> **dino99 said:**
> maybe some patience (not so long i guess)

[http://ubuntuforums.org/showpost.php?p=10993685&postcount=11](http://ubuntuforums.org/showpost.php?p=10993685&postcount=11)

Patience of course.. unfortunately this is the old legacy notification area and not
the indicators applet.
So i believe is a different issue.. hope to be wrong :)

---

### Post by dino99 on 2011-06-29
about the notification area, i was having trouble to get some icons appearing (when radiotray or clementine was loaded) but today, after tweaking some themes (gnome-tweal-tool), the icons appear again. So i dont know if the latest upgrades have done the trick or if it was related to theme (have choosen radiance, which is a gtk3 updated)

---

### Post by lucazade on 2011-06-29
> **dino99 said:**
> about the notification area, i was having trouble to get some icons appearing (when radiotray or clementine was loaded) but today, after tweaking some themes (gnome-tweal-tool), the icons appear again. So i dont know if the latest upgrades have done the trick or if it was related to theme (have choosen radiance, which is a gtk3 updated)

Tried latest updates of indicators  and switching themes but no luck.
well i'll live with them broken, i'm not in a hurry!

---

### Post by jbicha on 2011-06-29
My blind guess as to why the Gnome Fallback icons aren't working is because Oneiric is using a new GTK that was not tested with gnome-panel 3.0. The GNOME developers are too busy doing other development and haven't released a 3.1.x version of gnome-panel yet. Just a guess; it could be something completely different.

---

### Post by VinDSL on 2011-06-29
I'm on the trot right now, and not at a real PC.  :D

Don't know if this helps - and I'm going by memory, but...

I've been running canned OEM indicators applets lately, and this-or-that indicator disappears from time-to-time; immediately after updates.

Going into Synaptic and installing the gtk2 version (alongside the gtk3 version) takes care of the situation.

---

### Post by sparker256 on 2011-06-29
> **VinDSL said:**
> I'm on the trot right now, and not at a real PC.  :D

Don't know if this helps - and I'm going by memory, but...

I've been running canned OEM indicators applets lately, and this-or-that indicator disappears from time-to-time; immediately after updates.

Going into Synaptic and installing the gtk2 version (alongside the gtk3 version) takes care of the situation.

Did your weather stuff from conky forecast go away with the latest indicator updates? The live data icons on mine are gone at the moment.

Bill

---

### Post by VinDSL on 2011-06-30
> **sparker256 said:**
> Did your weather stuff from conky forecast go away with the latest indicator updates? The live data icons on mine are gone at the moment.

Bill
Indeed! Yes, I just got back to my abode and fired up the PC.

As you can see:  Anything pertaining to conkyForecast has disappeared from my Conky setup.


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-29-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-29-2011.png")[/INDENT]


Somebody needs to contact Mark and let him know conkyForecast is broken in UbuOO.

**[COLOR="DarkOrange"]EDIT[/COLOR]**

Working fine in UbuMM...


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-30-jun-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-30-jun-2011.png")[/INDENT]


Just saying...

---

### Post by sparker256 on 2011-06-30
I sent kaivalagi this screen shot to [http://ubuntuforums.org/showthread.php?t=869328](http://ubuntuforums.org/showthread.php?t=869328) post #3297 so we will see what happens.

Bill

---

### Post by VinDSL on 2011-07-02
> **sparker256 said:**
> [...] we will see what happens.
Good job!

conkyForecast is working fine now, after the wnelson hack.

It seems Walt is still having problems.  Hrm...

Along with the hack, I installed Python 2.6 & python-requests.  I wonder if that made a difference?!?!?

I've been checking the Conky cache file, and it's been automagically updating every half-hour.

Anyway, onwards and upwards...  :)

---

