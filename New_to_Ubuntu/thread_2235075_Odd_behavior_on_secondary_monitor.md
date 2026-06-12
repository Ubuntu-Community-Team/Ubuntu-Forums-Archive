---
title: "Odd behavior on secondary monitor"
date: 2014-07-18
forum: New to Ubuntu
---

### Post by CorneliusSneed on 2014-07-18
Ubuntu 14.04LTS/Unity

Probably expected behavior, actually, but I want to make it stop. :)  Recently added a secondary monitor, everything is working fine, but whenever I move the mouse to the lower right corner of the secondary monitor, any application I have open minimizes (somewhat) on each or both screens. It even happens on the primary monitor when only the desktop is open on the secondary monitor. It does not seem to happen when the mouse pointer is on the primary monitor. I think this is probably a "feature" but I have no idea what it is called or where to find it.

---

### Post by ty74 on 2014-07-18
I think you are right ubuntu, by default does not come with many options to fix the monitors. I would suggest to install compizconfig setting manager with the following line.
  sudo apt-get install compizconfig-settings-manager
It has a bunch of options to configure and one of them should be your monitor troubles.
Hope it helps.

---

### Post by coffeecat on 2014-07-18
It sounds as though not only have you already installed compizcofig-settings-manager, but that you have set up a hot corner for window picker.

Open ccsm -> Window Management -> Scale -> Bindings tab. Check both "Initiate Window Picker" and "Initiate Window Picker For All Windows" which have a monitor icon - not the keyboard or mouse icons. I think you'll find that you have set one or the other for the bottom right-hand corner.

---

### Post by CorneliusSneed on 2014-07-19
That was it. Thanks \o/

---

