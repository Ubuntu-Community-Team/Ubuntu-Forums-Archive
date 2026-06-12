---
title: "desktop effects do not work in 8.04"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by kylefiechter on 2008-05-05
I have a Latitude C610, so I'm working with a pretty old computer, but I had very little trouble with 7.10 on this computer. I upgraded to 8.04 last night, and found that I could not enable any visual effects, and that the "custom" effects were not even an option. I tried the ol' sudo apt-get install compizconfig-settings-manager, but it said that I already have the latest version of the manager.

In order to get this to work in 7.10, I had to change the device driver to "radeon", and the color depth to 16, and that did the trick.

My card is an ATI Radeon Mobility M6 LY

---

### Post by mmb1 on 2008-05-05
You might want to move this to the "Desktop effects and customizations" forum.  Have you tried using the restricted drivers manager?

---

### Post by kylefiechter on 2008-05-06
I got the effects working, now I just need to figure out how to enable "custom" settings again, and I'll be all set.

---

### Post by tjwoosta on 2008-05-06
go to System-Preferences-Advanced Desktop Effects Settings

(for some reason the custom option doesnt show up on hardy, just click extra)

---

### Post by vishzilla on 2008-05-06
Go to Add/Remove and search for *ccsm*. Be sure you have "All Applications" selected. Install it and go to System>Prefs>Adv. Desktop Effects Settings.

---

