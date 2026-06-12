---
title: "Prevent Sleep When Lid Closes"
date: 2011-07-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by jlward4th on 2011-07-16
In Oneiric when I close my laptop lid it goes to sleep.  There used to be a way to prevent this behavior but I can't find it.

---

### Post by rapiertg on 2011-07-16
> **jlward4th said:**
> In Oneiric when I close my laptop lid it goes to sleep.  There used to be a way to prevent this behavior but I can't find it.

I think you can find it in gnome-tweak-tool

---

### Post by jlward4th on 2011-07-16
Yeah!  Thanks!  It was in there.  But I wish I could find what it actually changed in my settings.

---

### Post by mc4man on 2011-07-16
Those settings are avail. in dconf-editor and gsettings 
(dconf-editor is part of dconf-tools
screen shows - location in dconf-editor is 
org > gnome > settings daemon > plugins > power

---

### Post by jlward4th on 2011-07-17
Perfect!  Thanks mc4man!!

---

### Post by mc4man on 2011-07-17
Occasionally here may be some settings or more likely the values to a key in dconf-editor that aren't assessable - if so gsetting always works. (and is quite useful  in itself
man gsettings is useful to see commands, ect.

small related ex.
```
$ gsettings range org.gnome.settings-daemon.plugins.power lid-close-battery-action
enum
'blank'
'suspend'
'shutdown'
'hibernate'
'interactive'
'nothing'
doug@doug-XPS-M1330:~$ gsettings set org.gnome.settings-daemon.plugins.power lid-close-battery-action blank
doug@doug-XPS-M1330:~$ gsettings get  org.gnome.settings-daemon.plugins.power lid-close-battery-action 
'blank'


```

---

