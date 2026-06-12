---
title: "How to install Firefox 3 without breaking Firefox 2?"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by vvvladut on 2008-06-22
I've been waiting for Ubuntu to notify me that there is a new version of Firefox available, and offer to update it: no such luck. OK then, I thought to myself, DIY is one of the cornerstones on the Linux philosophy, why don't I search for it myself with Adept? I did that, found FF3, installed it, opened it, only to be pleasantly surprised because it had kept my preferences, history, etc etc, including my addons...but then...

No Tab Mix Plus yet for FF3, it seems. No Fasterfox either, but I'm not sure what that does anyway - but no Tab Mix Plus means no FF3 for me yet - sorry!

So I removed FF3 and opened my old FF2 back. Firstly, it was a good thing to find that FF3 does no override your FF2 installation, like it does in Windows. But still, I found Tab Mix Plus was disabled (??) in FF2, and I couldn't enable it! Also, FF3 had upgraded FireFTP to a newer version, but now FF2 could not use this newer version and would not install the previous version back because this one would not uninstall! Then, for some reason, Forecastfox had forgotten all my custom settings: in short, all this was enough to bug the hell out of me and to reinstall FF2 from scratch (purged everything before).

Now I just realised that nobody is going to read so far so [B]if you don't have time to read through, please just read the stuff in bold:

How can I install FF3 from the repository so that it does not interfere at all with my current FF2 installation? No, I don't want it to detect my current settings and use my current add-ons: I don't want FF3 and FF2 to even know about each other's existence. Is that possible? Thanks![/B]

---

### Post by nowshining on 2008-06-22
try updating ur add-ons - or install [http://www.oxymoronical.com/web/firefox/nightly](http://www.oxymoronical.com/web/firefox/nightly) restart firefox - and in the add-ons select the new buttom make compatible - however note this may screw up ur FF3 browser.

---

### Post by vvvladut on 2008-06-22
I don't want to screw up anything; besides, FF3 screws up things by itself, it does not need my help...

All I want is a method to install it separately from my current FF2 installation.

---

### Post by spirit2 on 2008-06-22
There's a developmental version of Tab Mix Plus at [http://tmp.garyr.net/forum/viewtopic.php?t=7031](http://tmp.garyr.net/forum/viewtopic.php?t=7031) It works perfectly fine for me.

---

### Post by vvvladut on 2008-06-22
That's nice, but it still doesn't answer my question...

---

### Post by alienexplorers on 2008-06-22
In order to run a new firefox 3 installation without messing up firefox 2 you need to make a seperate profile.  Seems that firefox 3 does a job on the firefox 2 profile messing them both up..  Can't remember how to do a dual profile setup do maybe one of the guys on here can help out.

---

### Post by vvvladut on 2008-06-22
Thanks alienexplorers, so I need to set up a separate profile...anyone know how to do that? What's a profile anyway? A profile of what, Firefox?

---

### Post by nowshining on 2008-06-22
in terminal:

firefox --profile-manager

- the reason some add-ons don't work is becuase thye haven't been updated for FF3 since it's a major version, esp. that.

or if they do work the .rdf files max version hasn't been updated yet. however the nightly tester tools make compatible does it for u on ur current add-ons.

a profile is like a diff. account that retains the settings, etc.. of that user, etc..

---

