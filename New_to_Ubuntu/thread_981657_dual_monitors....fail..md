---
title: "dual monitors....fail."
date: 2008-11-13
forum: New to Ubuntu
---

### Post by B34ST1Y on 2008-11-13
Hey,

I have compiz-fusion running perfectly on my Ubuntu 8.10. I LOVE IT! :) but I digress.....I have the cube enabled, and I recently added a 2nd monitor to my setup. Now that I have the monitor plugged in, and enabled....I have it set to be a separate desktop, so that I can work simultaneously.

anyways, for some reason it gives me a seperate wall (not a cube, as its only 2 desktop faces) on the 2nd monitor, and independantly my 4 desktop faces on my primary monitor....the problem is two-fold.


1.) how can I configure it to be a cube on the 2nd monitor? I can't seem to find the settings...

2.) whenever I try to open a window on my 2nd monitor (i.e. open firefox)...it ALWAYS opens on the first monitor, and I cant drag it over.


Any help would be greatly appreciated! :)

---

### Post by talsemgeest on 2008-11-13
If you have compizconfig-settings manager installed then go into the general setting and check the settings for dual monitors.

Hope this helps :)

---

### Post by B34ST1Y on 2008-11-13
```
sudo ccsm
```


???

---

### Post by B34ST1Y on 2008-11-13
I dont see any settings at all, involving dual monitors...

---

### Post by epitaph on 2008-11-14
If you're using an Nvidia video card don't run both monitors as separate X servers, use TwinView. This will allow you to run compiz and have windows interact between the monitors.

To have the cube be one single cube instead of 2, open up Advanced Appearance Preferences (if you don't have it, install compizconfig-settings-manager) and go to Desktop Cube plugin and select "One Big Cube" for the Multi Ouput Mode.

---

