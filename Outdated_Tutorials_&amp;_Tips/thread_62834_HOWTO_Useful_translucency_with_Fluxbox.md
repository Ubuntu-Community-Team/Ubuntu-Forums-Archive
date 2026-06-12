---
title: "HOWTO: Useful translucency with Fluxbox"
date: 2005-09-06
forum: Outdated Tutorials &amp; Tips
---

### Post by kamstrup on 2005-09-06
You've seen all the fancy screenshots have you? You've even tried out Composite+xcompmgr+transset, but was never really satisfied because manually transsetting each window was a pain?

I just discovered that the fluxbox window manager actually utilises transparency if you have it enabled. The way that fluxbox handles transparency is to make all but the focused window transparent. This works exceptionally well if you use the "Sloppy Focus" focus model. - See the second screenshot where the lower terminal has focus while the top one is tranparent.

First install fluxbox:```
sudo apt-get install fluxbox
```
Then follow this thread to enable Composite and install xcompmgr: [http://www.ubuntuforums.org/showthread.php?t=20769](http://www.ubuntuforums.org/showthread.php?t=20769)

**Be warned though**: If you are not using the real nvidia or ati drivers this will be *very* resource hungry! (but works fine if you use them)

Now log out and restart X (ctrl-alt-backspace), and log into a fluxbox session (choose fluxbox in the session-menu on the login screen).

When logged in fire up a terminal and do```
xcompmgr
``` which enables transparency and no drop shadows, or ```
xcompmgr -cfF
``` to enable drop shadows as well. Note that I find it to be more stable when running without drop shadows...

Play around!

Note that there is a "Transparency" submenu in the configuration menu in fluxbox. You might wanna have a look at that.

Good luck!

EDIT: I just learned that the nvidia drivers are the only ones capable of accelrating Composite; which essentially means that you'll have to have an nvidia graphics card to *enjoy* composition. Ie. ATI will give your poor perormance as it stands now.

---

### Post by Elena on 2005-09-06
Thanks bro! :smile: 

good job, I like it soooooooooo much, and BTW nice screenshots  :wink:

---

