---
title: "Changing (messed-up) cursor issue"
date: 2005-05-29
forum: Outdated Tutorials &amp; Tips
---

### Post by jonrkc on 2005-05-29
Some users have found that their cursor will change to solid black or some other solid color hard to see, and its outline changes, too.  This is apt to happen after an application that uses a pretty basic level of display operation, such as screensavers.

The solution I found for my system was to insert 

```

Option   "SWcursor"

```

in my xorg.conf file in the monitor section.  

You can read about this and other xorg options on

[http://www.x.org/X11R6.8.2/doc/chips3.html](http://www.x.org/X11R6.8.2/doc/chips3.html)

This particular option causes the machine to rely on a software cursor system, not the hardware one built into some display-driver chips such as my ATI one.

Since I added the line and restarted X, the problem has not happened again.

---

