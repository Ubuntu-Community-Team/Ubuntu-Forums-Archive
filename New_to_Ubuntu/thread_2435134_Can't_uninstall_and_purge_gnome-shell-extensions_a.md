---
title: "Can't uninstall and purge gnome-shell-extensions and presistant settings"
date: 2020-01-16
forum: New to Ubuntu
---

### Post by richard378 on 2020-01-16
I am on Ubuntu 19.10. I installed a bunch of extensions after which my screen would freeze.  I tried removing all gnome shell extensions.  I could remove them only through clicking x on extensions.gnome.org as
```
apt sudo purge gnome-shell-extensions
``` does not remove the extensions that were installed by installing the gnome-shell-extensions package.  I checked /usr/share/gnome-shell/extensions after removing them with extensions.gnome.org and the folder was empty except for Ubuntu dock.  I tried reinstalling the gnome-shell-extensions and all my settings were preserved.  How do I remove the old settings.  Just to make sure they are not corrupted by the bad extensions, so I can start fresh.

---

### Post by deadflowr on 2020-01-16
Several extensions such as the dash-to-dock extension and the appindictor extensions are stand alone.
They are also depends for the ubuntu-desktop meta package so removing them also remove the meta package.
> ```
apt sudo purge gnome-shell-extensions
```
That command is all sorts of wrong...

> How do I remove the old settings. Just to make sure they are not corrupted by the bad extensions, so I can start fresh.
Tweaks, if installed, has a reset option.
Otherwise try
```
dconf reset -f /org/gnome/shell/extensions/
```
should work.

---

