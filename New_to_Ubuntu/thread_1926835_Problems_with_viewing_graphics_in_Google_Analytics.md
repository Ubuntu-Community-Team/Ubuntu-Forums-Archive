---
title: "Problems with viewing graphics in Google Analytics"
date: 2012-02-17
forum: New to Ubuntu
---

### Post by gstoilov on 2012-02-17
Dear Forum Members,

I have installed recently Ubuntu 11.10. When tried to open my Google Analytics account however I could not see the graphics which Google analytics normally creates. I only see a grey box. How this issue can be resolved.

---

### Post by Krytarik on 2012-02-17
The Google Analytics website makes heavy use of Flash, so make sure the Flash Player plugin is installed:
```
sudo apt-get install flashplugin-installer
```Or the full "[ubuntu-restricted-extras]("http://packages.ubuntu.com/oneiric/ubuntu-restricted-extras")" meta-package:
```
sudo apt-get install ubuntu-restricted-extras
```If the Flash Player plugin has been installed by this, restart your browser, obviously.

Regards.

---

