---
title: "Hardy and Synaptic touchpad don't like each other..."
date: 2008-07-07
forum: New to Ubuntu
---

### Post by cartisdm on 2008-07-07
I've been running Hardy for a little over a month now and noticed that my synaptics touchpad is buggy.  I installed the GUI touchpad control so I could adjust the sensitivity, tapping, etc.  Now every once in a while my mouse will just freeze.  It won't respond to anything for a few seconds then it will go right back into action.

The bonus annoying part is sometimes when it unfreezes it completely ignores all settings.  The mouse speed goes into hyperdrive, the sensitivity is really high, and the tapping is enabled.  Changing the settings wont do anything so I have to reboot.

---

### Post by neurostu on 2008-07-07
There are quite a few different synaptic packages you should try out the each one seperately, some work better then others with different hardway.

To see which packages are available run:
```

aptitude search synaptic

```
The packages with the **i** on the left are the ones that are installed.  Go through the packages one by one and install them with:
```

sudo apt-get install <package>

```
This will remove whatever synaptic package you currently have installed, and install the new one.

Eventually you should find one that work...

Good luck and post back!

---

