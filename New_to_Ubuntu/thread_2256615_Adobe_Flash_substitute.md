---
title: "Adobe Flash substitute?"
date: 2014-12-13
forum: New to Ubuntu
---

### Post by Greg Mueller on 2014-12-13
Firefox 34
Ubuntu 12.04 with KDE Plasma desktop

This just started and I can't find a way to make it go away.

To the left of the favicon on some webpages is an Adobe Flash notification icon. When I go to a new page it turns red and I have to tell it to let the flash player work on that page, otherwise it is gray.
Is there a way to tell it to work on all pages all the time?

Is there a substitute that I can use instead of Adobe?

Thanks

---

### Post by mörgæs on 2014-12-13
It sounds like Flashblock or a similar plug-in. The purpose is to shut down Flash ads, and what you describe is the intended mode of operation.

Take a look in the plug-in list to see what you have enabled.

---

### Post by Greg Mueller on 2014-12-13
I guess it is blocked because it is an older version (11.2.202.418) and 11.2.202.424 and below has a bug. 

I get this message when I try to update it

[https://blocklist.addons.mozilla.org/en-US/firefox/blocked/p796](https://blocklist.addons.mozilla.org/en-US/firefox/blocked/p796)

Apparently there is 11.2.202.425 version available but I can't get it to update to it

---

### Post by mörgæs on 2014-12-13
Not completely blocked it seems. You can just push a button and get Flash working again.

Anyway, I recommend installing Chrome which has a well maintained Flash player built in.

---

### Post by Greg Mueller on 2014-12-13
I wonder why I can't get it to update to 425?

---

### Post by mörgæs on 2014-12-13
On a fully updated 14.04 I get:


```
apt-cache show flashplugin-installer

Package: flashplugin-installer
Priority: optional
Section: multiverse/web
Installed-Size: 137
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Bart Martens <bartm@knars.be>
Architecture: i386
Source: flashplugin-nonfree
Version: 11.2.202.425ubuntu0.14.04.1
[...]
```

Just run your normal updates and it will come.

---

