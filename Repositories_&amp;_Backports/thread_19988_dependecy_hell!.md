---
title: "dependecy hell!"
date: 2005-03-14
forum: Repositories &amp; Backports
---

### Post by ba5e on 2005-03-14
Can not start firefox...as you see many problems! just upgraded from warty to hoary and get this all the time when trying to reinstall ubuntu-base


Setting up mozilla-firefox (1.0+dfsg.1-6ubuntu1) ...
Updating mozilla-firefox chrome registry...E: /usr/lib/mozilla-firefox/extensions/installed-extensions.txt still present. Registration might have gone wrong.
mv: cannot stat `/usr/lib/mozilla-firefox/defaults.ini': No such file or directory
dpkg: error processing mozilla-firefox (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mozilla-firefox-gnome-support:
 mozilla-firefox-gnome-support depends on mozilla-firefox (= 1.0+dfsg.1-6ubuntu1); however:
  Package mozilla-firefox is not configured yet.
dpkg: error processing mozilla-firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of yelp:
 yelp depends on mozilla-firefox; however:
  Package mozilla-firefox is not configured yet.
dpkg: error processing yelp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on mozilla-firefox; however:
  Package mozilla-firefox is not configured yet.
 ubuntu-desktop depends on mozilla-firefox-gnome-support; however:
  Package mozilla-firefox-gnome-support is not configured yet.
 ubuntu-desktop depends on yelp; however:
  Package yelp is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mozilla-firefox
 mozilla-firefox-gnome-support
 yelp
 ubuntu-desktop

Failed to apply all changes! Scroll in the terminal buffer to see what went wrong.

---

### Post by Xian on 2005-03-14
It looks like APT is having a fit over your firefox install directory. Try wiping that /usr/lib/mozilla-firefox/extensions/installed-extensions.txt file that APT is complaining about and try again. You may have to remove the entire ~/mozilla/firefox contents and then re-install the application before attempting to set up the ubuntu-base pkg.

---

