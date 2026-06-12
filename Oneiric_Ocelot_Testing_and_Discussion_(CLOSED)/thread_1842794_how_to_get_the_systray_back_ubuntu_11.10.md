---
title: "how to get the systray back ubuntu 11.10"
date: 2011-09-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by reptilezone2002 on 2011-09-12
hi guys 

can u tell me how to get the systra(notifucation tray) back ubuntu 11.10 unity .......... the old method the one i used in 11.04 doesnt work in 11.10

tx

---

### Post by mc4man on 2011-09-12
The systray now works quite well in 11.10, actually much better then in 11.04 - in 11.04 the systray was drawn on the desktop and 'popped' thru the unity panel, now it's drawn on the panel directly

Some qt4 apps will now  automatically get added, nothing to do but enable in the apps settings - one  example of that is vlc  (possibly from the sni-qt package

Otherwise you can add in dconf-editor or by using gsettings - screen shows location in dconf-editor - just click in key till it turns white, edit in & press enter on keyboard to set

or gsetting - use get to see current list, use set to change
get command
```
gsettings get com.canonical.Unity.Panel systray-whitelist
```

Ex. adding wicd to my current whitelist

```
~$ gsettings get com.canonical.Unity.Panel systray-whitelist
['JavaEmbeddedFrame', 'Wine', 'scp-dbus-service', 'Audacious']
```
```
gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Wine', 'scp-dbus-service', 'Audacious', 'wicd']"
```

---

### Post by reptilezone2002 on 2011-09-12
Tx for the tip but it doesn't work .. im trying to get the systray icon for Gyachi this trick worked on 11.04 but still cant get it working on 11.10 may b its still in beta dont know wait & see

---

### Post by awam66 on 2011-09-13
I've tried all of the above to get Skype showing but it still doesn't work!

---

### Post by mc4man on 2011-09-13
skype works fine,  just add to end of string
, 'skype'

---

### Post by mc4man on 2011-10-02
Just a  follow up on vlc - 
the sni-qt indicator for vlc works but [only partially correct]("https://bugs.launchpad.net/ubuntu/+source/sni-qt/+bug/859499"). The systray icon is much better at this point. There was a compiz bug that also inc. using the systray for vlc but thats been fixed

If wanting to use the systray icon instead of the indicator then add vlc to the whitelist & remove the sni-qt package
*
(haven't found a way yet to enable/disable apps individually with sni-qt

---

