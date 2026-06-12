---
title: "Synaptics touchpad gestures not working"
date: 2012-07-19
forum: New to Ubuntu
---

### Post by suvam8694 on 2012-07-19
For : HP 630 Notebook PC
Ubuntu 12.04

Synaptics touchpad gestures like two finger scroll, pinch zoom, three finger press etc are not working. only edge scroll is working.
also the tapping on top left corner of the touchpad no longer toggles the enabled/disabled state. please help.
i have checked the hp website for the device driver, they don't have driver for linux. i have already tried registry 

Please help.

---

### Post by lkraemer on 2012-07-19
Try synclient -l in a Terminal Window (Console) to determine what
parameters are set on your Synaptics Touchpad.  Then change what you
would like.  Copy and paste commands to prevent errors......

```

man synclient
synclient --help
synclient -l

```

To make those settings persistent might require a script.  Look in the 
Script section of the Linux Mint Forum........for an example.

There is also a package named gpointing-device-settings on some Distro's to allow easy modifications.  It might not be persistent
if below Version 1.4.0 according to Launchpad.....ie., Linux Mint 201204 (LMDE)


lk

---

### Post by llmunro on 2012-08-09
Hello forum,

I seem to be having this same problem, which just started today...I don't know if its related to recent updates?

Anyways, like the original OP, two finger scroll, three finger middle click, etc. no longer work for me.  Edge scrolling still works.  I tried seeing if I could enable it under "Mouse and Touchpad," but the only options available are for a mouse.  I seem to recall that there was a separate tab under Mouse and Touchpad with options for two finger scroll, horizontal scroll, disable touchpad when typing, etc.  The tab for touchpad settings no longer exists!

This is calculated to drive me bonkers, as the touchpad gestures are things I use all the time.  I'm praying this is fixed in an update sooner rather than later!

I am not entirely sure how to modify the touchpad settings via the CLI or using a script to accomplish this.

Suggestions?

Thanks much.
Lisa

ETA: I am happy to report that a restart has solved the problem for me, at least and I was able to adjust the touchpad settings and restore two finger scroll under Mouse and Touchpad settings.  Hopefully the OP will find a solution soon...

---

