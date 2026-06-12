---
title: "How do I install flash on Chromium in Beta 2?"
date: 2011-09-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by greenelf on 2011-09-24
How do I install flash on Chromium in Oneric Beta 2?
I installed flash on 11.04 by doing this:
```
sudo apt-get install flashplugin-nonfree
```
```
sudo cp /usr/lib/flashplugin-installer/libflashplayer.so /usr/lib/chromium-browser/plugins
```
```
chromium-browser --enable-plugins
```

But when I do this, it says it already has flash installed, but flash content does not work.

---

### Post by buntu63 on 2011-09-24
[SIZE=4]googling: [/SIZE]   [http://www.google.com/search?client=ubuntu&channel=fs&q=How+do+I+install+flash+on+Chromium+in+Oneric+Beta+2%3F&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=How+do+I+install+flash+on+Chromium+in+Oneric+Beta+2%3F&ie=utf-8&oe=utf-8)

---

### Post by VinDSL on 2011-09-24
> **greenelf said:**
> How do I install flash on Chromium in Oneric Beta 2?
I installed flash on 11.04 by doing this:
```
sudo apt-get install flashplugin-nonfree
```
```
sudo cp /usr/lib/flashplugin-installer/libflashplayer.so /usr/lib/chromium-browser/plugins
```
```
chromium-browser --enable-plugins
```

But when I do this, [COLOR="Blue"][SIZE="+1"]it says it already has flash installed[/SIZE][/COLOR], but flash content does not work.
Open Chromium and type these in the addy bar (one-at-a-time):

[LIST]
[*]about:flash
[*]about:plugins
[/LIST]

That should give some clues, as to what's going on.

It might be as simple as enabling Flash in about:plugins (or choosing a different file/version)...

---

### Post by x-shaney-x on 2011-09-24
[HTML]sudo apt-get install flashplugin-installer[/HTML]

---

### Post by greenelf on 2011-09-25
> **x-shaney-x said:**
> [HTML]sudo apt-get install flashplugin-installer[/HTML]
Thanks, that worked!
-------------------------------------------------------
> > **VinDSL said:**
> Open Chromium and type these in the addy bar (one-at-a-time):

[LIST]
[*]about:flash
[*]about:plugins
[/LIST]

That should give some clues, as to what's going on.

It might be as simple as enabling Flash in about:plugins (or choosing a different file/version)...


It says Flash is disabled, but there is no enable option in about: plugins.

---

### Post by xebian on 2011-09-25
IIRC the 32-bit chrome has flash built in.

---

### Post by x-shaney-x on 2011-09-25
Chrome (google branded) does.  Chromium (open source, non google version) does not, or didn't last time I checked.

---

### Post by screaminj3sus on 2011-09-25
I never bother installing it from the repos. I just stick the flash player .so file in ~/.mozilla/plugins and all my browsers (chrome/chromium, opera) pick it up as well. I'm on 64 bit so I need to install it manually anyway to use flash 11 64 bit.

> **x-shaney-x said:**
> Chrome (google branded) does.  Chromium (open source, non google version) does not, or didn't last time I checked.

If you use 64 bit neither does, but that might change when adobe finally releases flash 11 64 bit.

---

