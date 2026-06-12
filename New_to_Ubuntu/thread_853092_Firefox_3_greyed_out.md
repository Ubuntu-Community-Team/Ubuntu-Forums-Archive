---
title: "Firefox 3 greyed out"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by BOMEz on 2008-07-08
This has happened to me 3 times so far.

When running firefox 3, it kind of just greys out on me. Right now as I'm typing this message, everything is all grey.

I can't remember what I was doing the first 2 times, but this time I was just trying to enlarge a photo I was viewing...it greyed out, and then refused to respond to any commands I gave.

Then it came back to life flashing through all the commands I had issued, but it remains grey until I restart the browser

Is this a feature? Maybe I hit something somewhere by accident?

Everything else is colored fine; my mouse, tool bar, desktop and other windows, and I have done all the latest updates.

---

### Post by oliviacond on 2008-07-08
maybe is because of the excessive I/O caused by fsync
to fix it,
go to Edit->Preference->Security
untick suspected attack site and suspected forgery

---

### Post by oliviacond on 2008-07-08
maybe is because of the excessive I/O caused by fsync
to fix it,
go to Edit->Preference->Security
untick suspected attack site and suspected forgery

---

### Post by philinux on 2008-07-08
I think that bug was fixed.

It's likely to be flash. Any messages about npviewer.bin crashing?

Also try running this from terminal

firefox -safe-mode

---

### Post by appi2012 on 2008-07-08
Compiz (desktop effects) greys applications when they are "not responding." That explains why it's greying. Firefox only greys for me sometimes while using flash.

---

### Post by BOMEz on 2008-07-08
I wasn't looking at any flash website at the time, so I'm guessing that it just froze...grayed out and stayed that way. 

Thanks for your time everyone

---

