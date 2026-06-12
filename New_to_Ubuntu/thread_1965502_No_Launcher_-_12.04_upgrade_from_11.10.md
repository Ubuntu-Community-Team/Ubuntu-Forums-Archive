---
title: "No Launcher - 12.04 upgrade from 11.10"
date: 2012-04-25
forum: New to Ubuntu
---

### Post by edempco on 2012-04-25
After upgrading from 11.10 to 12.04 I have no launcher. Unity is non-existent. The "Appearance" control window affects any window that is open. If the launcher behaviour is changed, for instance, the Appearance window assumes the position and size of the launcher. 

Removing Unity and reinstalling it from the Terminal window had no affect. 

Something is not right, but I don't know where to go from here. 

I have a Toshiba M4 laptop that ran 11.10 great. I can get around without the launcher by opening the dash with the windows key. I don't want to continue this way. Any suggestions would be appreciated.

---

### Post by MG&amp;TL on 2012-04-26
Try:

1. Logging into unity2d and running:

```
unity --reset
```

(this will run for a while, leave it until it appears to be finished)

2. If that doesn't work, purge unity:

```
sudo apt-get remove --purge unity
```

and reinstall:

```
sudo apt-get install unity
```

Another option is to backup and reinstall from a cd. While upgrading is meant to be safe, I remain unconvinced.

---

### Post by edempco on 2012-04-26
Thank you for your suggestions.

I was hopeful, but reset, purging, and installing failed to restore unity. 

During the reset process, I noticed a number of warning messages and statements that "this should never happen ... file a bug report." There were a number of compiz and Gtk errors. I've reloaded compiz from Synaptic, but to no avail.  From this, I assume that there is much more that is wrong with the system. 

If you have any other suggestions, I will be more than happy to read them. I appreciate your time.

---

### Post by KLXDave on 2012-04-30
I am fairly new to this forum so forgive me if I am stepping on any toes.
 
I have the same problem since upgrading from 11.10 to 12.04. I can get into settings and change the background appearance but do not have any of the launcher icons on the left side. I tried to reset unity as suggested and part way through the following came up.
 
WARN 2012-04-30 11:50:26 unity.screeneffectframebufferobject ScreenEffectFramebufferObject.cpp:167 unsupported internal format
compiz (core) - Warn: failed to recieve ConfigureNotify event on 0xc00003
 
compiz (core) - Warn: unhandled ConfigureNotify on 0x1e000a1!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
 
I appreciate any assistance that can be provided.

---

### Post by KLXDave on 2012-05-03
Well I have a solution for my situation that I want to pass on that may help others.  The GPU is an nvidia GeForce 6100 and the current driver package is 295.40.  There are some bug reports that mention using 295.33 instead.  This worked for me.  Hopefully a new driver will be developed with a fix at a later date.

---

### Post by edempco on 2012-05-07
Well, there is a long story to fixing the menu situation. Instead of a long dialogue, here are the bullet points:

[LIST]
[*]I have always used my Toshiba laptop as a desktop, with an extra monitor and keyboard attached; VGA for the screen and USB for the keyboard & mouse.
[*]In the past, there has been no problem upgrading with that configuration.
[*]The update from 11.10 to 12.04 did not recognise "mirrored" displays and the resolution I had selected.
[*]Removing the extra VGA screen and using the laptop screen allowed me to see and use the unity menu ... ironically, I was using the laptop with a digital projector that didn't seem to have the same resolution as the VGA monitor; don't ask me why.
[*]Reconnecting the VGA monitor and changing the resolution (several times) gave me the ability to use the VGA monitor with the laptop again.
[*]I still need to find resolutions that work, because I'm not happy with how it is set up, but I can get work done and that's the important part!
[/LIST]
There were no magic bullets for me; no terminal scripts; no synaptic packages that would help. My finding was to reduce the display resolution until the menu returned and work from there.

---

