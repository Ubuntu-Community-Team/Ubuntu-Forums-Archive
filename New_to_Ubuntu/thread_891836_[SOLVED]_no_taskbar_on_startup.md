---
title: "[SOLVED] no taskbar on startup??"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-08-16
when i start kubuntu my task bar isnt there,fortunatly i have a konsole icon on my desktop,i have to type kicker to get it going.im not sure how this happened,the only thing ive done is play around with the menu,anyway is there any way i can get it to be there on start up?
Rick

---

### Post by benerivo on 2008-08-16
> **rixtr66 said:**
> when i start kubuntu my task bar isnt there,fortunatly i have a konsole icon on my desktop,i have to type kicker to get it going.im not sure how this happened,the only thing ive done is play around with the menu,anyway is there any way i can get it to be there on start up?
RickThis is only a 'workaround' answer, but you could make /usr/bin/kicker run at login, by adding it to /home/bobby/.kde/Autostart (i think that's the right location).

---

### Post by rixtr66 on 2008-08-16
sorry i dont understand what you mean.this is what i get in the terminal when i start the kicker;
rick@kubuntu:~$ kicker
rick@kubuntu:~$ kicker: ExtensionManager::desktopIconsArea() = [0,0 - 1280x800] screen = 0
kicker: GetButtons
kicker:
kicker: ******WARNING******    Layout is invalid.
kicker: Quicklauncher registered DCOP signal
kicker:
kicker: ******WARNING******    Layout is invalid.
kicker:
kicker: ******WARNING******    Layout is invalid.
kicker: MediaApplet::slotClear
kicker: ExtensionManager::desktopIconsArea() = [0,0 - 1280x800] screen = 0



is this helpful?

---

### Post by benerivo on 2008-08-16
If you open two file manager windows (is it dolphin in kubuntu?), and in one navigate to /usr/bin and in the other go to your /home/yourname/.kde/Autostart folder. Then find and drag the kicker icon from /usr/bin in to the other window and it should give you the option to create a link. If you can do this, then log off and back in, and it should start kicker automatically, just as if you had typed it in to the terminal.

---

### Post by rixtr66 on 2008-08-17
yep!that did it,thanks!
Rick

---

