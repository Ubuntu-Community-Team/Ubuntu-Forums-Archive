---
title: "Screen remains ON after screen-lock"
date: 2012-09-11
forum: New to Ubuntu
---

### Post by ptosiani on 2012-09-11
Hello,

I have a situation with my laptop (DELL XPS 14Z), whenever y lock the screen, instead of getting a blank screen (LCD off) I get a really bright black screen.

I found some some scripts online to work around this problem by forcing screen off but I want to know how to troubleshoot something like this.

Is there any config file I can check? Is it related to my video driver?  

Thank you.

---

### Post by androssofer on 2012-09-11
> **ptosiani said:**
> Hello,

I have a situation with my laptop (DELL XPS 14Z), whenever y lock the screen, instead of getting a blank screen (LCD off) I get a really bright black screen.

I found some some scripts online to work around this problem by forcing screen off but I want to know how to troubleshoot something like this.

Is there any config file I can check? Is it related to my video driver?  

Thank you.

see the lock screen just sets the screen saver to black.. and its bright because LCDs use backlight even for black. so this would be normal behaviour.

my guess would be to tweak power settings to power down screens.. not sure how to link the two however. Mine goes black then turns off the screen when inactive for 30 mins.

---

### Post by androssofer on 2012-09-11
found this tutorial:

[http://www.howtogeek.com/61836/how-to-turn-off-your-monitor-with-a-hotkey-in-ubuntu/](http://www.howtogeek.com/61836/how-to-turn-off-your-monitor-with-a-hotkey-in-ubuntu/)

if you do it, set the keyboard shortcut to:

> ctrl  alt  L

this will mean gnome-screensaver will start and lock the screen. Then this script will turn the screens off.. thus combining the 2..

not sure if it brings it back by moving the mouse.. so be careful.. 

i might try this when i get home  :-)

---

### Post by ptosiani on 2012-09-11
thank you! Is a nice workaround

---

