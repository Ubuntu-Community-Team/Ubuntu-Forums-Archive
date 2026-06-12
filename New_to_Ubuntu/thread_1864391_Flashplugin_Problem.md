---
title: "Flashplugin Problem"
date: 2011-10-18
forum: New to Ubuntu
---

### Post by alienexplorers on 2011-10-18
I have been trying to load the Flashplugin-Installer program in synaptic.  I keep getting an error and the loader stops.  I have included a screen snapshot of the error message.  Any help would be appreciated in getting this problem corrected.

---

### Post by lovinglinux on 2011-10-18
Try these on a terminal:

```
sudo apt-get purge adobe-flashplugin
sudo apt-get purge flashplugin-installer
sudo apt-get clean
sudo apt-get install flashplugin-installer
```

If that doesn't help or if you are not familiar with terminal, try [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/).

---

### Post by alienexplorers on 2011-10-18
Still having problems after doing what you said. See new screen snapshot. Seems the system thinks a i386 version of flash is installed and it is causing a conflict with the 64bit version.

---

### Post by lovinglinux on 2011-10-19
> **alienexplorers said:**
> Still having problems after doing what you said. See new screen snapshot. Seems the system thinks a i386 version of flash is installed and it is causing a conflict with the 64bit version.

Try adobe-flashplugin instead.

```
sudo apt-get install adobe-flashplugin
```

---

### Post by Joentokyo on 2011-10-19
> **alienexplorers said:**
> Still having problems after doing what you said. See new screen snapshot. Seems the system thinks a i386 version of flash is installed and it is causing a conflict with the 64bit version.
Looks like there is a conflict between the version you are trying to install and your operating system. Are you running 64-bit AMDt or 32-bit i386? Check to make sure your operating system and the installer version are the same.

---

