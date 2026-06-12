---
title: "No longer able to search from address bar in firefox"
date: 2011-09-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by x-shaney-x on 2011-09-25
I have the search bar removed and normally do all my searching directly via the address bar.
After an update today, attempts to search from the address bar result in a "URL invalid" popup.

Could this be related to the change of search provider from google to ask (mentioned a few posts down) or is this a permanent change?

---

### Post by dino99 on 2011-09-25
yes some strange issues, like saving changes into an edited previous post dont work (cant save it, no error given), or inserting icons/tag/colored text/... seems to be deactivated too.

---

### Post by ronacc on 2011-09-25
maybe its time to use chrome or Opera .

---

### Post by dino99 on 2011-09-25
> **ronacc said:**
> maybe its time to use chrome or Opera .

i already use midori as i cant log on launchpad with FF

---

### Post by dsfitzpat on 2011-09-25
Seems to be a bug - an accident with the last update. I'd say wait a day, update, and all should be back to normal.

---

### Post by sammiev on 2011-09-25
This [link]("http://mycroft.mozdev.org/") will fix it for you. :)

---

### Post by enceladus47 on 2011-09-25
I just updated now and it's back to normal

---

### Post by Harry33 on 2011-09-26
Firefox will have a new update soon.
There is the version ( 7.0+build2+nobinonly-0ubuntu4) building in Launchpad right now.

Here:
[https://launchpad.net/ubuntu/oneiric/+source/firefox/7.0+build2+nobinonly-0ubuntu4](https://launchpad.net/ubuntu/oneiric/+source/firefox/7.0+build2+nobinonly-0ubuntu4)

> 
**Changelog**
firefox (7.0+build2+nobinonly-0ubuntu4) oneiric; urgency=low

  * Really fix LP: #858683 - Clean up the symlinks for users who upgraded to
    7.0+build2+nobinonly-0ubuntu2; This means checking for everything before the
    -0ubuntu3 revision since the -0ubuntu2 users already upgraded
    - update debian/firefox.postinst.in
 -- Micah Gersten <email address hidden>   Mon, 26 Sep 2011 01:30:33 -0500


---

