---
title: "Xfce4 + Window Maker"
date: 2008-03-27
forum: Outdated Tutorials &amp; Tips
---

### Post by bytor4232 on 2008-03-27
I thought I would share a recent discovery of mine.  Recently I decided I needed finer granulated control over my windows, but still love the Xfce4 desktop.  I found that you can actually run the Xfce4 desktop environment with Window Maker as the window manager.

Here's the steps I took to create my little hybrid desktop environment:

1. I installed WindowMaker:  sudo apt-get install wmaker wmaker-data
2. I logged out of Xfce4, and changed my gdm session to Window Maker
3. I created the following file in Window Maker:
- editor $HOME/GNUstep/Library/WindowMaker/autostart
and placed the following in the file:
```

#!/bin/bash
xfce4-session &

```
- Save, exit, and make the file executable:
```

chmod +x $HOME/GNUstep/Library/WindowMaker/autostart

```
4. Ran WPrefs (Window Maker preferences) and tweaked a few things.  Mainly I got rid of the dock and clip, but there was quite a few other things I changed to my taste (autofocus new windows, icon position, etc)
5. Logged out, and logged back in.

The desktop is a little hackneyed and Window Maker doesn't recognize Xfce4's logout function, so I have to exit Window Maker when I log out.  But the panels are there, desktop and keyboard settings per xfce, etc.

I'm not sure how useful this will be to y'all.  I mainly needed tighter control over the windows, such as MPlayer always on top and alway sticky with no window decorations, plus keyboard shortcuts to jump to windows.  It feels faster than xfwm4, but its just barely noticeable.  There was quite a few tweaking I had to do, like setting NoAppIcon for the Xfce4 functions in the WMWindowAttributes file in GNUstep.

I'm sure there is more configuring I need to do, but it seems fast, and serves me well.  I used to use Window Maker back in my Debian days before switching to Ubuntu, so its a little stroll down memory lane.

---

