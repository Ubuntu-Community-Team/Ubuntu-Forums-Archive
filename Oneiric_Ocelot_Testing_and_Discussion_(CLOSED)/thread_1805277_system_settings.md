---
title: "system settings"
date: 2011-07-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2011-07-15
just noticed that since the last few updates system settings does not appear in the upper right hand corner of the toolbar

---

### Post by mc4man on 2011-07-15
> **rburkartjo said:**
> just noticed that since the last few updates system settings does not appear in the upper right hand corner of the toolbar
Is currently not there - Alt+F2 > type gnome-control (should show after gnome
On locate the .desktop in /usr/share/applications

---

### Post by jbicha on 2011-07-15
The indicators (system menus) are in a bit of flux right now. The Me Menu is going away I believe. There's a new power menu. Settings is supposed to be its own new menu. The session menu is reverting to more how it used to work in Ubuntu 10.10 since it won't need to have a System Settings link.

---

### Post by mc4man on 2011-07-15
The system settings is also available in dash - search settings or sitting in applications as System Settings (gnome-control-center.desktop
The actual command is 
 gnome-control-center --overview

I just add to a Utilities menu icon in the unity launcher as a quicklist - 
Ex. of quicklist entry
```
[SystemSettings Shortcut Group]
Name=System Settings
Exec=gnome-control-center --overview
TargetEnvironment=Unity
```

---

### Post by lidex on 2011-07-15
It shows for me. I have been uninstalling what I thought were old indicators and installing new ones.
The menu actually has 'Lock Screen' at the top.

EDIT: Just ran an update. I assume you installed these, were held back here:
```
The following packages have been kept back:
  gnome-keyring gwibber gwibber-service [COLOR="Red"]indicator-messages indicator-session[/COLOR] seahorse
  yelp

```

---

### Post by mc4man on 2011-07-15
> **lidex said:**
> It shows for me. I have been uninstalling what I thought were old indicators and installing new ones.
The menu actually has 'Lock Screen' at the top.

EDIT: Just ran an update. I assume you installed these, were held back here:
```
The following packages have been kept back:
  gnome-keyring gwibber gwibber-service [COLOR="Red"]indicator-messages indicator-session[/COLOR] seahorse
  yelp

```
The new indicator-session is 
0.2.93-0ubuntu1
and indicator-messages is
(0.4.92-0ubuntu1

should look like as shown here - post 4, not mine
[http://ubuntuforums.org/showthread.php?t=1805075](http://ubuntuforums.org/showthread.php?t=1805075)

---

### Post by lidex on 2011-07-16
> should look like as shown here - post 4, not mine
I like yours better...

---

### Post by mc4man on 2011-07-16
> **lidex said:**
> I like yours better...

I've tried everything to make 'normal', isn't going to happen till 
I do a fresh install next week (just did this install afew hrs. ago

Does point to how you never know what's a bug or just 'who knows'

---

### Post by VinDSL on 2011-07-16
> **jbicha said:**
> The session menu is reverting to more how it used to work in Ubuntu 10.10 since it won't need to have a System Settings link.
Glory! Hallelujah!

System Settings, so called is worthless IMO.

The worst of which, is not being about to revert to a formerly used background image.

Anyway, good riddance to bad rubbish!  :)

---

### Post by jbicha on 2011-07-17
System Settings is definitely not going away nor should you expect it to change much from its current form. In fact, System Settings is supposedly getting its very own system menu (indicator) instead of being a link in the session menu.

---

