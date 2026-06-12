---
title: "[SOLVED] compiz - where do I find it?"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by bmann11 on 2008-06-19
Looked in synaptic, and it says I have it, but I can't find it anywhere?  Thanks.

---

### Post by atomkarinca on 2008-06-19
System > Preferences > Appearance > Visual Effects. Have you tried that?

---

### Post by bred on 2008-06-19
[COLOR="Blue"]on top left u will find Places > Search for files

search for compiz and u will find it[/COLOR]

---

### Post by forestpixie on 2008-06-19
Once you get it going if you want to use any of the settings you will need to install the settings manager

```
sudo apt-get install compizconfig-settings-manager
```

Then that will be in system> preferences menu

---

### Post by bmann11 on 2008-06-19
Didn't find it in search for files

and, yes, I checked the visual affects stuff, I'm wanting to check out something a bit different.

---

### Post by Victormd on 2008-06-19
If it's not under SYSTEM>PREFERENCES, then you need to install the settings manager
```
sudo apt-get install compizconfig-settings-manager
```

This is where all the animation/windows/eye-candy settings are included.

Also, when you right click on the desktop>change background> and go to the last tab (not on an ubuntu box so can't tell you what the name is, probably effects or something), you can select advanced options as well.

---

### Post by Zenze on 2008-06-19
If you have the manager installed its System > Preferences > Advanced Settings Desktop Manager

---

### Post by bmann11 on 2008-06-19
When i enter the code I get

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by bmann11 on 2008-06-19
Thanks, obrigado.  Got the system manager out of synaptic.

---

