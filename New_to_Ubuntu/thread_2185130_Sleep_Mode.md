---
title: "Sleep Mode"
date: 2013-11-01
forum: New to Ubuntu
---

### Post by frog3764 on 2013-11-01
Greetings to the Group - My system is a dual boot W7 32 and Ubuntu 12.4. In Windows I have my system set for NEVER going to sleep as I have a nice slide show of personal slides that I like to see when idle. But in Ubuntu the monitor (only) keeps going to sleep even though I have the power settings set to NEVER, so there must be another setting someplace that I need to set, but I can't find it. I did have to install the Compizconfig program to get my screensaver to work but since the monitor keeps "sleeping" after 15 minutes. I never get to see anything. I did check the settings there too and don't see anything to change or set up. Some help here is appreciated as I wnat to keep everything on so that my screensave comes on with my slideshow.

Jim

---

### Post by TQLeaman on 2013-11-01
Hi,

I would examine the settings with dconf Editor. (You can install that via a command line: sudo apt-get install dconf-editor OR search for it via Ubuntu Software Center)

Take a look at the following sets of keys:
[INDENT]org > gnome > desktop > screensaver
org > gnome > settings-daemon > plugins > power[/INDENT]

All the best,

TQ

---

### Post by frog3764 on 2013-11-02
Hey thanks TQ - I'll see what I can find there.

Jim

---

