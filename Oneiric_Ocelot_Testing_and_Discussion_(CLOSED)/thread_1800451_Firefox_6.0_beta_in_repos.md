---
title: "Firefox 6.0 beta in repos"
date: 2011-07-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-07-09
Oneiric repos have now a new beta version of Firefox (6.0~b1+build1+nobinonly-0ubuntu1).

Here:
[https://launchpad.net/ubuntu/oneiric/+source/firefox/6.0~b1+build1+nobinonly-0ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/firefox/6.0~b1+build1+nobinonly-0ubuntu1)

---

### Post by iClouseau88 on 2011-07-09
Thank you.  

Just got it via sudo aptitude update && sudo aptitude safe-upgrade

---

### Post by Harry33 on 2011-07-09
> **iClouseau88 said:**
> Thank you.  

Just got it via sudo aptitude update && sudo aptitude safe-upgrade

Otherwise it is working well (after a short testing), but some of the add-ons are not supported (like video-download-helper).

---

### Post by lovinglinux on 2011-07-09
> **Harry33 said:**
> Otherwise it is working well (after a short testing), but some of the add-ons are not supported (like video-download-helper).

You could try to disable compatibility check with [Add-on Compatibility Reporter]("https://addons.mozilla.org/en-US/firefox/addon/15003/"). I have tested Download Helper on FF 6.0b1 and it seems to be working properly.

Keep in mind that in the new Mozilla development model, add-ons are automatically bumped to the beta version compatibility, if they do not have any incompatible code. Which means if they are not compatible yet, then they probably won't work or exhibit weird behaviour with compatibility check disabled. I haven't received the automatic compatibility bump warning from Mozilla yet, so I suppose they haven't done it. So most likely that Download Helper compatibility will be bumped soon.

---

### Post by dext on 2011-07-09
> **Harry33 said:**
> Otherwise it is working well (after a short testing), but some of the add-ons are not supported (like video-download-helper).
use this method ```
 extensions.checkCompatibility.nightly" "false"    
```
 since it aint a Nightly change it to False still

---

### Post by SoFl W on 2011-07-09
Still using 3.6.18, don't know what the fuss is to have the latest.

---

### Post by buzzmandt on 2011-07-09
> **SoFl W said:**
> Still using 3.6.18, don't know what the fuss is to have the latest.
Seems an odd statement.  Isn't that what dev testing is, latest and greatest, bring it on, bleeding edge.

---

### Post by SoFl W on 2011-07-09
> **buzzmandt said:**
> Seems an odd statement.  Isn't that what dev testing is, latest and greatest, bring it on, bleeding edge.


You are absolutely correct, it is the wrong place for my statement.

---

### Post by lovinglinux on 2011-07-09
> **SoFl W said:**
> Still using 3.6.18, don't know what the fuss is to have the latest.

> **SoFl W said:**
> You are absolutely correct, it is the wrong place for my statement.

Well, the most recent beta version of Firefox has a huge performance difference when compared to Firefox 3.6, plus several of new features.

[[IMG]http://www3.picturepush.com/photo/a/5939461/640/5939461.png[/IMG]](http://picturepush.com/public/5939461)

---

