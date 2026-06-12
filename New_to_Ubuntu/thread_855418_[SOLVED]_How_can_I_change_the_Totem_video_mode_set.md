---
title: "[SOLVED] How can I change the Totem video mode setting"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by crjackson on 2008-07-10
I can't play video clips on most of the installed players when compiz is running.  I found that by changing the settings on VLC and MPlayer from Xv to X11 the video files play fine.

In Totem however, I can't find where to change this setting.  It's not in the preferences so how does one change this in Totem?

---

### Post by tjwoosta on 2008-07-10
i have the same issues with my computer

i eventually just completely removed totem because i couldn't figure out how to change the video output   (mplayer does everything totem does anyway)

---

### Post by kostkon on 2008-07-10
If you are talking about *totem* (and not *totem-xine*) then you can change the video driver that is used from the *Multimedia Systems Selector*, one configuration utility that in the past existed in *System -> Preferences*. Now it's hidden.

Press *ALT+F2* and give
```
gstreamer-properties
```
Select the *Video* tab and check what driver is used for the *Default Output*.

---

### Post by crjackson on 2008-07-11
> **kostkon said:**
> If you are talking about *totem* (and not *totem-xine*) then you can change the video driver that is used from the *Multimedia Systems Selector*, one configuration utility that in the past existed in *System -> Preferences*. Now it's hidden.

Press *ALT+F2* and give
```
gstreamer-properties
```
Select the *Video* tab and check what driver is used for the *Default Output*.

Thanks for the tip, but that was a no go.  It only offered v4lnx.

---

