---
title: "Trying to get matchbox working, but can't grasp how X works."
date: 2010-09-14
forum: Programming Talk
---

### Post by carlsmith on 2010-09-14
In short, I'm trying to get matchbox-window-manager running.

I started this whole project by reformatting and installing Ubuntu Server 10.4 with the `manually select packages` option, then stuck fluxbox, synaptic, chromium and some terminal app on it, (it being a generic desktop, P4, 512MB).

Then I rebooted it, which brought me back to the console, and fluxbox did not autofire on bootup, which is what I wanted.

If I ran fluxbox it would fail, no X server, but when I ran `startx`, fluxbox started up automatically. Hmmm

By now, you've probably figured out that I'm new to this.

Then I tried rebooting and running `xinit` and then `matchbox-window-manager` which gave me that quarter-screen, white console you normally get at the top-left, but I now had another glitchy, grey, square at the top of the screen, it kinda sat behind the other, less glitchy square. Not good.

I tried to reboot, the console blanked me and started acting up so I was forced to yank the mains.

When I boot it now, it always, seemingly with no issues at all, takes me straight to my GUI, fluxbox, log-in screen. Once I'm in fluxbox, I'm screwed. Even if I Ctrl+Alt+F1, I don't know how to shut down fluxbox nor run matchbox while X already has a window manager.

I'm quiet happy to break this system, it's a computer I'm just using to practice on, so I can easily do a fresh OS install if that'll help.

In the long run, I just want to get matchbox running on this desktop so I can tweak it up and then use the set-up to run an older laptop, and that I only want to use to practice my python on and do a bit of bash.

I'm happy to use the machine with nothing, but text-based control, but I still want my scripts to be able to generate graphics - and for me to be able to see them of course - and yes, on the same device, before someone asks.

---

### Post by carlsmith on 2010-09-14
Any pointers please anyone?

---

### Post by soltanis on 2010-09-14
Your problem seems to be matchbox, but never having used it, I can't really help you.

---

