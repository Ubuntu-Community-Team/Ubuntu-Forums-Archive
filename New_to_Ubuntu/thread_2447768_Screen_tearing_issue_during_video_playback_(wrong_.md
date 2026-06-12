---
title: "Screen tearing issue during video playback (wrong horizontal resolution?)"
date: 2020-07-25
forum: New to Ubuntu
---

### Post by rockthecaspar on 2020-07-25
I've been trying to figure out why I'm getting horizontal screen tearing during video playback, similar to the type of tearing you would experience when playing games without VSync switched on.

Despite my display settings and Nvidia X Server settings being set to 2560x1440p, when I type the following command into terminal I get a different response:[INDENT]
xdpyinfo | grep dimensions
dimensions:    4480x1440 pixels (1673x537 millimeters)
[/INDENT]

Is this possibly the root of the problem, and if so how would I go about fixing it? 

Thanks for any advice.

Edit: I'm guessing the 4480x1440 is down to my 1080p second screen and is just the total available resolution across both monitors.

---

### Post by rockthecaspar on 2020-07-25
I solved the issue, it was Firefox. In case anyone in the future stumbles on this page:

Typed about:config in the search bar
Set "layers.acceleration.force-enabled" to True
Closed & restarted browser.

---

