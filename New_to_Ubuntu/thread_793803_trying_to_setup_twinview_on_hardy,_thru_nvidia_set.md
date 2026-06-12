---
title: "trying to setup twinview on hardy, thru nvidia settings"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by fignig on 2008-05-14
when i try to apply the changes that i made i get this:

Failed to set MetaMode (1) 'CRT-0: 1024x768@60 @1024x768 +1024+0, DFP-0: 1024x768 @1024x768 +0+0' (Mode 2048x768, id: 54) on X screen 0

Would you like to remove this MetaMode?


what does this mean and how do i get this dual monitor thing working?

---

### Post by KingWilliam on 2008-05-14
Yo don't need to mess with the meta stuff.
I'll try to make you a little screenshot.

---

### Post by alienexplorers on 2008-05-14
Are you running nvidia-settings with gksudo:
> gksudo nvidia-settings

---

### Post by KingWilliam on 2008-05-14
Done :)

First make sure you open the settings manager with sudo. You won't be able to save changes when you don't so do:```
sudo nvidia-settings
```
Now look at my screenshot. Forst choose detect displays. Then use the configure button to set both displays to twinview. You can drag them to the position you want.
When you are done don't forget to save the X configuration file. 
To apply the changes you will need to reboot. (or restart X with CTRL+ALT+BACKSPACE)

---

### Post by alienexplorers on 2008-05-14
gksudo should be used with programs with graphical interfaces and sudo should be used with all other types of programs.

---

### Post by fignig on 2008-05-15
i opened it up w/ gksudo nvidia-settings and i tried setting it up w/ separate X screen and i filled in the resolutions and refresh rate in both of the screen settings. and when i tried to apply these settings i got this error:

Failed to set MetaMode (1) 'CRT-0: 1024x768@60 @1024x768 +0+0' (Mode 1024x768, id: 0) on X screen 0.

dunno what that is. anyone?

---

### Post by fignig on 2008-05-15
> **fignig said:**
> i opened it up w/ gksudo nvidia-settings and i tried setting it up w/ separate X screen and i filled in the resolutions and refresh rate in both of the screen settings. and when i tried to apply these settings i got this error:

Failed to set MetaMode (1) 'CRT-0: 1024x768@60 @1024x768 +0+0' (Mode 1024x768, id: 0) on X screen 0.

dunno what that is. anyone?

okay so i tired auto detecting the resolution and refresh rate and the 2nd monitor turned on, but the 1st monitor cut out. i thought restarting would be the answer but it wasn't. i struggled to turn off a monitor w/ only 1/2 screen vision. i turned 1 monitor off but it would only turn off the 2nd one. so i'm stuck, and j/w if someone could help me.

---

### Post by fignig on 2008-05-15
> **fignig said:**
> okay so i tired auto detecting the resolution and refresh rate and the 2nd monitor turned on, but the 1st monitor cut out. i thought restarting would be the answer but it wasn't. i struggled to turn off a monitor w/ only 1/2 screen vision. i turned 1 monitor off but it would only turn off the 2nd one. so i'm stuck, and j/w if someone could help me.

when i restart, both screens will be on, and everything. but it's when it gets into the login screen that 1 monitor will shutoff and i can't see 1/2 the screen.

anyone know what's causing this?

---

### Post by KingWilliam on 2008-05-15
I don't really understand you :) 

When logged in, is twinview working? 
During the login screen it is normal only 1 screen has contents.

---

