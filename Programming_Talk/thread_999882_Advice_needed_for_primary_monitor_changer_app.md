---
title: "Advice needed for primary monitor changer app"
date: 2008-12-02
forum: Programming Talk
---

### Post by mssever on 2008-12-02
As I described in my [original thread on this subject]("http://ubuntuforums.org/showthread.php?p=6294236"), operating my laptop with an external monitor attached is a pain. For some reason, the fine folks at Intel decided that if I plug in a projector, I must want it to become primary so that my panels, program windows, etc. show up on the big screen instead of my laptop screen where they should be. I don't know what the folks at Intel were smoking when they came up with such a harebrained idea.

Intel's Windows drivers include a program that's capable of changing which monitor is primary, but as far as I can tell the Linux drivers have no such option. According to Google, nVidia ships a Linux program to accomplish this task, but that does me no good since I don't own nVidia hardware.

Given that neither Google nor the UF community knows of an existing solution, it appears that a program needs to be written to allow people to change which monitor is considered primary. IMO, it should work at a higher level than the video driver, because it seems silly to make that hardware-dependent. My problem is that I don't know what would be involved in such a project, or even where to start. Would this be accomplished in the window manager, or Gnome, or Xorg? Or better yet, could it be a standalone program? This is a subject area I know very little about. Basically, I'm trying to determine if this is something I can write without spending too much time on it.

---

### Post by HalPomeranz on 2008-12-02
I'm not clear on exactly what you mean by "primary" in this case, but have you looked at the xrandr program at all?  It allows you to size and position multiple monitor configurations very easily.

---

### Post by mssever on 2008-12-03
> **HalPomeranz said:**
> I'm not clear on exactly what you mean by "primary" in this case, but have you looked at the xrandr program at all?  It allows you to size and position multiple monitor configurations very easily.
Thanks for mentioning xrandr. It never showed up in my Google searches. While it doesn't do what I want, the documentation cleared some things up.

I've discovered two things related to setting the primary monitor. First, new windows appear on the monitor that currently contains the pointer. So I need a way to control that. I previously thought they appeared on the primary monitor. Second, the Gnome panels always appear on the external monitor (which is why I'm calling it the primary monitor--I guess that's more of a Windows term, though). I've read that dragging the panels to the proper monitor will fix that, but doing so causes all sorts of problems when the external monitor is toggled on or off. So, it appears that I need some way to force the panels to show up on the proper monitor.

By the way, while I normally use Compiz, I run dual-head with Metacity, since the combination of Compiz and dual-head makes my machine unstable.

EDIT: 3,000th post

---

